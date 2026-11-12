# 📊 Ejercicio 27: Creación de un Modelo en Estrella y Medidas DAX

## 🎯 **Objetivos de la Práctica**
1. Comprender las deficiencias del modelado en una única tabla plana (desnormalizada).
2. Utilizar **Power Query** para descomponer la tabla plana en una **Tabla de Hechos** (*Fact Table*) y varias **Tablas de Dimensiones** (*Dimension Tables*).
3. Generar una **Tabla de Fechas (Calendario)** independiente mediante DAX.
4. Establecer la arquitectura del **Modelo en Estrella (Star Schema)** en la *Vista de Modelo* de Power BI Desktop con relaciones 1:N y dirección de filtro único.
5. Ocultar llaves foráneas y organizar el modelo para garantizar un rendimiento óptimo.
6. **Crear una tabla de métricas y desarrollar Medidas DAX explícitas** (agregaciones básicas, métricas calculadas y Time Intelligence) para comprobar la potencia del modelo dimensional.

---

## 📂 **1. Enunciado del Ejercicio**

La empresa distribuidora de tecnología *AsturTech* te ha entregado un extracto de ventas en un único archivo CSV plano denominado `datos_ventas_desnormalizados.csv`. 

El archivo contiene todas las operaciones mezclando datos de clientes, productos, tiendas, empleados y los importes de venta en una misma estructura.

### 📋 **Estructura del archivo CSV de origen:**

```csv
ID_Venta,Fecha_Venta,ID_Cliente,Nombre_Cliente,Email_Cliente,Tipo_Cliente,Ciudad_Cliente,ID_Producto,Nombre_Producto,Categoria_Producto,Precio_Unitario,ID_Tienda,Nombre_Tienda,Ciudad_Tienda,ID_Empleado,Nombre_Empleado,Cantidad,Descuento_Aplicado,Importe_Total
V-1001,2025-01-10,CLI-01,Juan Pérez,juan@email.com,Particular,Oviedo,PROD-10,Teclado Mecánico RGB,Periféricos,45.00,TND-01,Tienda Oviedo Central,Oviedo,EMP-05,Laura Martínez,2,0.00,90.00
V-1002,2025-01-10,CLI-02,María Rodríguez,maria@empresa.es,Empresa,Gijón,PROD-20,Monitor 27 FHD,Pantallas,180.00,TND-02,Tienda Gijón Puerto,Gijón,EMP-08,Carlos Gómez,1,10.00,170.00
V-1003,2025-01-11,CLI-03,Norte Tech SL,contacto@nortetech.es,Empresa,Avilés,PROD-30,Ratón Inalámbrico,Periféricos,25.00,TND-01,Tienda Oviedo Central,Oviedo,EMP-05,Laura Martínez,5,5.00,120.00
...
```

---

### 📝 **Tareas a realizar:**

1. **Importación:** Cargar el archivo `datos_ventas_desnormalizados.csv` en **Power BI Desktop** y acceder al **Editor de Power Query**.
2. **Creación de Dimensiones:** A partir de la consulta original, crear por referencia las siguientes 4 tablas de dimensión, eliminando duplicados para garantizar la unicidad de las claves primarias:
   * **`Dim_Cliente`**: `ID_Cliente`, `Nombre_Cliente`, `Email_Cliente`, `Tipo_Cliente`, `Ciudad_Cliente`. (PK: `ID_Cliente`).
   * **`Dim_Producto`**: `ID_Producto`, `Nombre_Producto`, `Categoria_Producto`, `Precio_Unitario`. (PK: `ID_Producto`).
   * **`Dim_Tienda`**: `ID_Tienda`, `Nombre_Tienda`, `Ciudad_Tienda`. (PK: `ID_Tienda`).
   * **`Dim_Empleado`**: `ID_Empleado`, `Nombre_Empleado`. (PK: `ID_Empleado`).
3. **Creación de la Tabla de Hechos:** Transformar la consulta original en **`Fact_Ventas`**, conservando únicamente las claves foráneas (`ID_Venta`, `Fecha_Venta`, `ID_Cliente`, `ID_Producto`, `ID_Tienda`, `ID_Empleado`) y las métricas numéricas (`Cantidad`, `Descuento_Aplicado`, `Importe_Total`).
4. **Creación de la Tabla de Fechas (`Dim_Calendario`):** Crear una tabla de calendario dedicada usando DAX (`CALENDAR()`) que cubra todo el rango de fechas del modelo. Agregar columnas calculadas para `Año`, `Número de Mes`, `Nombre de Mes` y `Trimestre`.
5. **Configuración del Modelo en Estrella:**
   * Conectar cada dimensión con `Fact_Ventas` mediante relaciones de **1 a Muchos (1 : N)**, con dirección de filtro **Único**.
   * Marcar la tabla `Dim_Calendario` como **Tabla de fechas oficial**.
   * Ocultar las claves foráneas en `Fact_Ventas`.
6. **Desarrollo de Medidas DAX en una Tabla Dedicada (`_Medidas`):**
   * Crear una tabla vacía contenedora denominada **`_Medidas`**.
   * Escribir e implementar las siguientes medidas DAX clave:
     * **Total Ventas** (`SUM`)
     * **Total Unidades** (`SUM`)
     * **Ticket Medio por Transacción** (`DIVIDE` + `DISTINCTCOUNT`)
     * **Descuento Promedio** (`AVERAGE`)
     * **Ventas Año Anterior (SAMEPERIODLASTYEAR)**
     * **Crecimiento YoY %** (`DIVIDE`)

---

## 🔑 **2. Solución Paso a Paso:**

### **Paso 1: Transformación e Ingeniería de Tablas en Power Query**

1. Abre **Power BI Desktop** ➔ **Obtener datos** ➔ **Texto/CSV** ➔ Selecciona `datos_ventas_desnormalizados.csv` ➔ Haz clic en **Transformar datos**.
2. Renombra la consulta original importada como **`Origen_Ventas_Plano`** y desactiva su carga en el informe (clic derecho sobre la consulta ➔ desmarcar **Habilitar carga**).

#### A. Creación de `Dim_Cliente`
1. Haz clic derecho en `Origen_Ventas_Plano` ➔ **Referenciar**.
2. Renombra la nueva consulta como **`Dim_Cliente`**.
3. Selecciona las columnas: `ID_Cliente`, `Nombre_Cliente`, `Email_Cliente`, `Tipo_Cliente`, `Ciudad_Cliente`.
4. Haz clic derecho en los encabezados seleccionados ➔ **Quitar otras columnas**.
5. Selecciona la columna `ID_Cliente` ➔ Haz clic derecho ➔ **Quitar duplicados**.

#### B. Creación de `Dim_Producto`
1. Clic derecho en `Origen_Ventas_Plano` ➔ **Referenciar**. Renombra a **`Dim_Producto`**.
2. Selecciona: `ID_Producto`, `Nombre_Producto`, `Categoria_Producto`, `Precio_Unitario`.
3. Haz clic derecho ➔ **Quitar otras columnas**.
4. Selecciona `ID_Producto` ➔ **Quitar duplicados**.

#### C. Creación de `Dim_Tienda`
1. Clic derecho en `Origen_Ventas_Plano` ➔ **Referenciar**. Renombra a **`Dim_Tienda`**.
2. Selecciona: `ID_Tienda`, `Nombre_Tienda`, `Ciudad_Tienda`.
3. Haz clic derecho ➔ **Quitar otras columnas**.
4. Selecciona `ID_Tienda` ➔ **Quitar duplicados**.

#### D. Creación de `Dim_Empleado`
1. Clic derecho en `Origen_Ventas_Plano` ➔ **Referenciar**. Renombra a **`Dim_Empleado`**.
2. Selecciona: `ID_Empleado`, `Nombre_Empleado`.
3. Haz clic derecho ➔ **Quitar otras columnas**.
4. Selecciona `ID_Empleado` ➔ **Quitar duplicados**.

#### E. Creación de `Fact_Ventas`
1. Clic derecho en `Origen_Ventas_Plano` ➔ **Referenciar**. Renombra a **`Fact_Ventas`**.
2. Selecciona únicamente las claves y numéricos: `ID_Venta`, `Fecha_Venta`, `ID_Cliente`, `ID_Producto`, `ID_Tienda`, `ID_Empleado`, `Cantidad`, `Descuento_Aplicado`, `Importe_Total`.
3. Haz clic derecho ➔ **Quitar otras columnas**.
4. Haz clic en **Cerrar y aplicar** en la cinta de opciones superior.

---

### **Paso 2: Creación de la Tabla de Fechas (`Dim_Calendario`) mediante DAX**

1. En Power BI Desktop, ve a la vista de **Tabla / Datos** ➔ Pestaña **Herramientas de tablas** ➔ **Nueva tabla**.
2. Escribe el siguiente código DAX para generar la tabla de calendario:

```dax
Dim_Calendario = 
VAR FechaMin = MIN(Fact_Ventas[Fecha_Venta])
VAR FechaMax = MAX(Fact_Ventas[Fecha_Venta])
RETURN
ADDCOLUMNS (
    CALENDAR(FechaMin, FechaMax),
    "Año", YEAR([Date]),
    "MesNum", MONTH([Date]),
    "NombreMes", FORMAT([Date], "mmmm"),
    "Trimestre", "T" & FORMAT([Date], "q"),
    "AñoMes", FORMAT([Date], "YYYY-MM")
)
```

3. Selecciona la columna `NombreMes` ➔ Pestaña **Herramientas de columnas** ➔ **Ordenar por columna** ➔ Selecciona **`MesNum`** (para evitar ordenación alfabética).
4. Haz clic derecho sobre la tabla `Dim_Calendario` ➔ **Marcar como tabla de fechas** ➔ Selecciona la columna `[Date]`.

---

### **Paso 3: Construcción del Modelo en Estrella en la Vista de Modelo**

1. Cambia a la **Vista de Modelo** (icono de diagrama de bloques a la izquierda).
2. Arrastra las tablas para formar la disposición visual en estrella (coloca `Fact_Ventas` en el centro y las dimensiones alrededor).
3. Establece las siguientes relaciones (arrastrando la clave de la dimensión hacia la clave de la tabla de hechos):

| Tabla Origen (Dimensión) | Campo Clave (1) | Tabla Destino (Hechos) | Campo Clave (N) | Cardinalidad | Dirección de Filtro |
| :--- | :--- | :--- | :--- | :---: | :---: |
| **`Dim_Cliente`** | `ID_Cliente` | **`Fact_Ventas`** | `ID_Cliente` | `1 : *` | Única (Dim -> Fact) |
| **`Dim_Producto`** | `ID_Producto` | **`Fact_Ventas`** | `ID_Producto` | `1 : *` | Única (Dim -> Fact) |
| **`Dim_Tienda`** | `ID_Tienda` | **`Fact_Ventas`** | `ID_Tienda` | `1 : *` | Única (Dim -> Fact) |
| **`Dim_Empleado`** | `ID_Empleado` | **`Fact_Ventas`** | `ID_Empleado` | `1 : *` | Única (Dim -> Fact) |
| **`Dim_Calendario`** | `Date` | **`Fact_Ventas`** | `Fecha_Venta` | `1 : *` | Única (Dim -> Fact) |

---

### **Paso 4: Limpieza y Ocultación de Claves (Buenas Prácticas)**

1. En `Fact_Ventas`, selecciona los campos `ID_Cliente`, `ID_Producto`, `ID_Tienda` y `ID_Empleado`.
2. En el panel de **Propiedades**, activa la opción **Está oculto: Sí** (o haz clic en el icono del ojo junto a cada campo).

---

### **Paso 5: Creación de la Tabla de Métricas y Medidas DAX**

Para mantener una gobernanza limpia del modelo, agruparemos todas las fórmulas en una tabla contenedora dedicada:

1. Ve a la pestaña **Inicio** ➔ **Especificar datos**.
2. Nombra la tabla como **`_Medidas`** y haz clic en **Cargar**.
3. Selecciona la tabla `_Medidas` y crea las siguientes **6 medidas DAX**:

#### 1. Total Ventas (Métrica Base)
```dax
Total Ventas = SUM(Fact_Ventas[Importe_Total])
```
*Formato:* Moneda (`€ Español`).

#### 2. Total Unidades Vendidas
```dax
Total Unidades = SUM(Fact_Ventas[Cantidad])
```
*Formato:* Número entero (`#,##0`).

#### 3. Ticket Medio por Transacción
```dax
Ticket Medio = 
DIVIDE(
    [Total Ventas], 
    DISTINCTCOUNT(Fact_Ventas[ID_Venta]), 
    0
)
```
*Formato:* Moneda (`€ Español`).

#### 4. Descuento Promedio Aplicado
```dax
Descuento Promedio = AVERAGE(Fact_Ventas[Descuento_Aplicado])
```
*Formato:* Moneda (`€ Español`).

#### 5. Ventas del Año Anterior (Time Intelligence)
```dax
Ventas Año Anterior = 
CALCULATE(
    [Total Ventas],
    SAMEPERIODLASTYEAR(Dim_Calendario[Date])
)
```
*Formato:* Moneda (`€ Español`).

#### 6. Crecimiento Interanual (YoY %)
```dax
Crecimiento Ventas YoY % = 
VAR VentasActuales = [Total Ventas]
VAR VentasPrevias = [Ventas Año Anterior]
RETURN
DIVIDE(VentasActuales - VentasPrevias, VentasPrevias, 0)
```
*Formato:* Porcentaje (`0.0%`).

4. **Organización final:** Oculta o elimina la columna por defecto (`Columna1`) de la tabla `_Medidas`. La tabla adoptará el icono de calculadora y se posicionará en la parte superior del panel de datos.

---

### 🎨 **Diagrama Esquemático del Resultado Final (Star Schema + Medidas)**

```
                                  ┌────────────────┐
                                  │   _Medidas     │
                                  ├────────────────┤
                                  │ Total Ventas   │
                                  │ Total Unidades │
                                  │ Ticket Medio   │
                                  │ Ventas AA (LY) │
                                  │ Crecimiento %  │
                                  └────────────────┘

      [ Dim_Cliente ]                                 [ Dim_Producto ]
       (ID_Cliente)                                    (ID_Producto)
            │                                               │
            │ (1)                                           │ (1)
            ▼ (*)                                           ▼ (*)
 ┌────────────────────────────────────────────────────────────────────────┐
 │                              Fact_Ventas                               │
 │ ────────────────────────────────────────────────────────────────────── │
 │  ID_Venta (PK)                                                         │
 │  Fecha_Venta (FK -> Dim_Calendario)                                    │
 │  ID_Cliente (FK -> Dim_Cliente, oculto)                                │
 │  ID_Producto (FK -> Dim_Producto, oculto)                              │
 │  ID_Tienda (FK -> Dim_Tienda, oculto)                                  │
 │  ID_Empleado (FK -> Dim_Empleado, oculto)                              │
 │  Cantidad                                                              │
 │  Descuento_Aplicado                                                    │
 │  Importe_Total                                                         │
 └────────────────────────────────────────────────────────────────────────┘
            ▲ (*)                                           ▲ (*)
            │ (1)                                           │ (1)
            │                                               │
      [ Dim_Tienda ]                                  [ Dim_Empleado ]
       (ID_Tienda)                                     (ID_Empleado)
            
            ▲ (*)
            │ (1)
   [ Dim_Calendario ]
        (Date)
```
