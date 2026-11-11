# Práctica guiada 24: Construcción de un Modelo en Estrella a partir de Datos Desestructurados

## 1. Contexto de Negocio

La empresa de distribución **Merx Data** ha estado registrando todas sus transacciones comerciales en un único archivo de datos plano en Excel (`Merx Data.xlsx`). La gerencia necesita analizar la evolución de las ventas, la rentabilidad por cliente y el rendimiento por líneas de productos.

Actualmente, el archivo contiene información redundante, datos sin tipar correctamente e inconsistencias estructurales. Tu cometido como analista de datos es importar este archivo en **Power BI Desktop**, aplicar las transformaciones necesarias en **Power Query (ETL)** para separar la tabla plana en un **Esquema en Estrella (Star Schema)** óptimo, establecer las relaciones relacionales correspondientes y crear medidas de análisis mediante **DAX**.

---

## 2. Conjunto de Datos (Dataset)

Para realizar el ejercicio, utilizarás como fuente el archivo adjunto **`Merx Data.xlsx`**.

> **Nota didáctica sobre la estructura original del archivo:**
> El archivo contiene una tabla principal o pestañas donde conviven mezclados los detalles transaccionales de venta junto con los atributos de los clientes, productos y comerciales.

*Estructura de origen en el archivo `Merx Data.xlsx`:*

* `ID_Venta` / `Fecha_Venta` / `ID_Cliente` / `Nombre_Cliente` / `Ciudad_Cliente` / `ID_Producto` / `Nombre_Producto` / `Categoria` / `Precio_Unitario` / `Cantidad` / `Importe_Total` / `ID_Comercial` / `Nombre_Comercial`

---

## 3. Tareas a Resolver

### **Fase A: Extracción y Transformación (Power Query)**

1. **Conexión e Importación:** Importa el libro de Excel `Merx Data.xlsx` a Power BI Desktop accediendo a través del Editor de Power Query (`Transformar datos`).
2. **Limpieza e Inspección:**
* Revisa los tipos de datos de cada columna (códigos como entero/texto, importes como número decimal, fechas como formato Fecha).
* Elimina filas nulas o inconsistentes si las hubiera.
* Aplica transformaciones de texto (recortar espacios sobrantes y poner en formato mayúsculas/minúsculas adecuado).


3. **Modelado en Esquema en Estrella (Creación de Dimensiones):**
* A partir de la consulta original, crea las dimensiones independientes **`DIM_Cliente`**, **`DIM_Producto`** y **`DIM_Comercial`** mediante duplicación/referencia de consultas, eliminando duplicados para garantizar claves primarias ($PK$) únicas.
* Modifica la tabla de hechos **`FACT_Ventas`** conservando únicamente los eventos transaccionales, sus métricas y las claves foráneas ($FK$).



### **Fase B: Modelado Relacional (Vista de Modelo)**

4. **Cargar al Modelo:** Aplica las transformaciones con `Cerrar y aplicar`.
5. **Creación de Relaciones:**
* Define las relaciones en la vista de **Modelo** entre las tablas de dimensiones ($1$) y la tabla de hechos ($*$).
* Asegúrate de verificar la cardinalidad de **Uno a Varios (1:*)** y que la dirección del filtro cruzado sea **Única** (de la dimensión a los hechos).


6. **Creación de Tabla Calendario (DAX):** Genera una tabla de dimensión temporal **`DIM_Calendario`** con lenguaje DAX (`CALENDARAUTO`) y relaciónala con la fecha de la tabla de hechos.

### **Fase C: Análisis y Cálculo de Medidas (DAX)**

7. Desarrolla las siguientes medidas de negocio centralizadas en una tabla de medidas:
* **Ventas Totales:** Suma del importe total de ventas.
* **Unidades Vendidas:** Suma total de cantidades.
* **Ticket Medio:** Promedio del importe por transacción.



---

## 4. Guía de Solución Paso a Paso

### **Paso 1: Importación de datos desde Excel**

1. Abre **Power BI Desktop**.
2. En la pestaña **Inicio**, haz clic en **Obtener datos** > **Libro de Excel**.
3. Selecciona el archivo **`Merx Data.xlsx`** y pulsa **Abrir**.
4. En la ventana del Navegador, selecciona la hoja/tabla de datos y haz clic en el botón **Transformar datos** *(importante: no pulsar Cargar directamente para evitar introducir basura o datos no normalizados al modelo)*.

---

### **Paso 2: Transformación ETL en Power Query**

#### **A. Limpieza de la consulta base**

1. Renombra la consulta cargada como `Ventas_Origen`.
2. Asegúrate de que la primera fila se haya promovido correctamente como encabezado.
3. Asegúrate de ajustar los tipos de datos desde el icono situado a la izquierda del nombre de cada columna:
* `Fecha_Venta` $\rightarrow$ **Fecha**
* `Precio_Unitario` e `Importe_Total` $\rightarrow$ **Número decimal**
* `Cantidad` $\rightarrow$ **Número entero**



#### **B. Generación de las Tablas de Dimensiones**

* **Crear `DIM_Cliente`:**
1. En el panel izquierdo de Consultas, haz clic derecho sobre `Ventas_Origen` y selecciona **Referenciar**.
2. Renombra la nueva consulta a **`DIM_Cliente`**.
3. Selecciona únicamente las columnas `ID_Cliente`, `Nombre_Cliente` y `Ciudad_Cliente` (haz clic derecho en el encabezado > *Quitar otras columnas*).
4. Selecciona la columna `ID_Cliente`, haz clic derecho y elige **Quitar duplicados**.


* **Crear `DIM_Producto`:**
1. Haz clic derecho sobre `Ventas_Origen` > **Referenciar**.
2. Renombra a **`DIM_Producto`**.
3. Selecciona las columnas `ID_Producto`, `Nombre_Producto`, `Categoria` y `Precio_Unitario` > *Quitar otras columnas*.
4. Selecciona `ID_Producto` y aplica **Quitar duplicados**.


* **Crear `DIM_Comercial`:**
1. Haz clic derecho sobre `Ventas_Origen` > **Referenciar**.
2. Renombra a **`DIM_Comercial`**.
3. Selecciona las columnas `ID_Comercial` y `Nombre_Comercial` > *Quitar otras columnas*.
4. Selecciona `ID_Comercial` y aplica **Quitar duplicados**.



#### **C. Generación de la Tabla de Hechos (`FACT_Ventas`)**

1. Haz clic derecho sobre `Ventas_Origen` > **Referenciar** y renombra la consulta como **`FACT_Ventas`**.
2. Conserva únicamente las columnas de claves foráneas y valores numéricos/transaccionales:
* `ID_Venta`, `Fecha_Venta`, `ID_Cliente`, `ID_Producto`, `ID_Comercial`, `Cantidad`, `Importe_Total`.


3. Haz clic derecho sobre la consulta original `Ventas_Origen` y **desmarca** la opción **Habilitar carga** (esto evitará llevar la tabla plana original redundante al modelo de datos final).
4. Ve a la pestaña **Inicio** y pulsa **Cerrar y aplicar**.

---

### **Paso 3: Creación del Modelo en Estrella y Relaciones**

1. En Power BI Desktop, dirígete al panel lateral izquierdo y haz clic en la **Vista de Modelo** (icono de diagrama de tablas).
2. Conecta las tablas arrastrando el campo de clave primaria ($PK$) desde la dimensión hasta la clave foránea ($FK$) en la tabla de hechos `FACT_Ventas`:
* `DIM_Cliente[ID_Cliente]` $\rightarrow$ `FACT_Ventas[ID_Cliente]`
* `DIM_Producto[ID_Producto]` $\rightarrow$ `FACT_Ventas[ID_Producto]`
* `DIM_Comercial[ID_Comercial]` $\rightarrow$ `FACT_Ventas[ID_Comercial]`


3. Haz doble clic sobre cada línea de relación creada para validar su configuración:
* **Cardinalidad:** Debe indicar **Uno a Varios (1:*)** (el `1` en el extremo de la dimensión y el `*` en el de hechos).
* **Dirección del filtro cruzado:** Configurada en **Única** (el filtro fluye desde la dimensión hacia los hechos).



---

### **Paso 4: Dimensión Temporal con DAX**

1. Ve a la pestaña **Modelado** en la cinta superior y selecciona **Nueva tabla**.
2. Escribe la fórmula DAX para construir la dimensión Calendario:
```dax
DIM_Calendario = 
ADDCOLUMNS (
    CALENDARAUTO(),
    "Año", YEAR([Date]),
    "Mes", FORMAT([Date], "mmmm"),
    "NroMes", MONTH([Date]),
    "Trimestre", "T" & FORMAT([Date], "Q")
)

```


3. En la **Vista de Modelo**, establece la relación:
* `DIM_Calendario[Date]` $\rightarrow$ `FACT_Ventas[Fecha_Venta]` *(Cardinalidad 1:*, Filtro cruzado Único)*.



---

### **Paso 5: Creación de Medidas DAX**

1. En la pestaña **Inicio**, haz clic en **Especificar datos**, nombra a la tabla `_Medidas` y pulsa **Cargar** (esto creará un contenedor limpio para organizar las fórmulas).
2. Haz clic derecho sobre `_Medidas` y selecciona **Nueva medida** para agregar las siguientes métricas:

* **Ventas Totales:**
```dax
Ventas Totales = SUM(FACT_Ventas[Importe_Total])

```


* **Unidades Vendidas:**
```dax
Unidades Vendidas = SUM(FACT_Ventas[Cantidad])

```


* **Ticket Medio:**
```dax
Ticket Medio = DIVIDE([Ventas Totales], COUNTROWS(FACT_Ventas), 0)

```

