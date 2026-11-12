# HOJA DE EJERCICIOS PRÁCTICOS DE DAX EN POWER BI DESKTOP
## 📊 Casos de Negocio: Acumulados, Ratios Porcentuales e Inteligencia de Tiempo
* **Curso:** IFCT56 Excel Avanzado y Power BI
* **Módulo:** 3 - Power BI + AI Insights (Días 21 a 30)
* **Entorno de Trabajo:** Power BI Desktop + Copilot / Asistencia de IA
* **Objetivo:** Resolver preguntas de negocio clave mediante la creación de medidas DAX estructuradas, auditando y validando los resultados en el lienzo visual.

---

Podéis copiar estas tablas directamente en Power BI Desktop usando la opción **"Especificar datos" (Enter Data)** o importarlas desde Excel/CSV para realizar todos los casos prácticos.

---

### 1. Tabla de Hechos: `FACT_Ventas`

Contiene operaciones representativas para los años 2025 y 2026, lo que nos permitirá probar las medidas de Inteligencia de Tiempo (YTD, Año Anterior, Crecimiento YoY) y los filtros por cliente y producto.

| ID_Venta | Fecha | ID_Cliente | ID_Producto | Cantidad | Precio_Unitario | Importe | Coste |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 15/01/2025 | C01 | P01 | 2 | 1200.00 | 2400.00 | 1600.00 |
| 2 | 20/02/2025 | C02 | P03 | 5 | 150.00 | 750.00 | 450.00 |
| 3 | 10/03/2025 | C03 | P02 | 1 | 800.00 | 800.00 | 500.00 |
| 4 | 05/05/2025 | C04 | P04 | 3 | 250.00 | 750.00 | 450.00 |
| 5 | 18/06/2025 | C01 | P05 | 2 | 400.00 | 800.00 | 500.00 |
| 6 | 12/09/2025 | C05 | P01 | 1 | 1200.00 | 1200.00 | 800.00 |
| 7 | 22/11/2025 | C02 | P02 | 2 | 800.00 | 1600.00 | 1000.00 |
| 8 | 15/01/2026 | C01 | P01 | 3 | 1200.00 | 3600.00 | 2400.00 |
| 9 | 18/02/2026 | C03 | P03 | 4 | 150.00 | 600.00 | 360.00 |
| 10 | 10/03/2026 | C02 | P02 | 2 | 800.00 | 1600.00 | 1000.00 |
| 11 | 05/05/2026 | C04 | P05 | 3 | 400.00 | 1200.00 | 750.00 |
| 12 | 12/05/2026 | C05 | P04 | 2 | 250.00 | 500.00 | 300.00 |

---

### 2. Tabla Dimensión: `DIM_Cliente`

Incluye diversidad de tipos de cliente (Estándar, Preferente, VIP) para poner a prueba el **Caso 4.1** (Ventas Clientes VIP) y distintas provincias para la medida dinámica del **Caso 4.3**.

| ID_Cliente | Nombre_Cliente | Tipo_Cliente | Provincia |
| --- | --- | --- | --- |
| C01 | Tecnologías Norte S.L. | VIP | Madrid |
| C02 | Comercial Levante | Preferente | Valencia |
| C03 | Soluciones Sur | Estándar | Sevilla |
| C04 | Industrias Cántabras | VIP | Barcelona |
| C05 | Innova Retail | Preferente | Madrid |

---

### 3. Tabla Dimensión: `DIM_Producto`

Jerarquía completa con `Categoria` y `Subcategoria` para trabajar las medidas de cuota sobre el total y cuota sobre la categoría padre (**Casos 2.2 y 2.3**), así como el ranking de productos (**Caso 4.2**).

| ID_Producto | Nombre_Producto | Categoria | Subcategoria |
| --- | --- | --- | --- |
| P01 | Portátil Pro 15" | Informática | Ordenadores |
| P02 | Monitor 27" 4K | Informática | Monitores |
| P03 | Teclado Mecánico | Informática | Accesorios |
| P04 | Silla Ergonómica | Mobiliario | Oficina |
| P05 | Mesa Elevable | Mobiliario | Oficina |

---

### 4. Tabla Dimensión: `Dim_Tiempo`

Para que las funciones de Inteligencia de Tiempo (`TOTALYTD`, `SAMEPERIODLASTYEAR`) funcionen de manera óptima, la tabla calendario debe cubrir rangos de fechas completos y sin saltos. Esta es una muestra del rango del ejercicio:

| Fecha | Año | Trimestre | Mes | Nombre_Mes | Numero_Mes |
| --- | --- | --- | --- | --- | --- |
| 01/01/2025 | 2025 | T1 | 1 | Enero | 1 |
| 15/01/2025 | 2025 | T1 | 1 | Enero | 1 |
| 15/01/2026 | 2026 | T1 | 1 | Enero | 1 |
| 18/02/2026 | 2026 | T1 | 2 | Febrero | 2 |
| 10/03/2026 | 2026 | T1 | 3 | Marzo | 3 |
| 05/05/2026 | 2026 | T2 | 5 | Mayo | 5 |
| 12/05/2026 | 2026 | T2 | 5 | Mayo | 5 |
| 31/12/2026 | 2026 | T4 | 12 | Diciembre | 12 |

*(Nota: En Power BI es aconsejable generar la tabla `Dim_Tiempo` mediante DAX usando `CALENDARAUTO()` o `CALENDAR(DATE(2025,1,1), DATE(2026,12,31))` para asegurar que todos los días del año estén cubiertos).*

#### 1. Generar la tabla con DAX

1. En Power BI Desktop, dirígete a la pestaña **Modelado** en la cinta de opciones superior.
2. Haz clic en el botón **Nueva tabla**.
3. En la barra de fórmulas, copia y pega el siguiente script:

  ```dax
  Dim_Tiempo = 
  ADDCOLUMNS (
      CALENDAR ( DATE ( 2025, 1, 1 ), DATE ( 2026, 12, 31 ) ),
      "Año", YEAR ( [Date] ),
      "Trimestre", "T" & FORMAT ( [Date], "q" ),
      "Mes", MONTH ( [Date] ),
      "Nombre_Mes", FORMAT ( [Date], "mmmm" ),
      "Numero_Mes", MONTH ( [Date] )
  )

  ```

> **Nota:** La función `CALENDAR` se encarga de crear una fila por cada día comprendido entre el `01/01/2025` y el `31/12/2026`. `ADDCOLUMNS` añade automáticamente los campos calculados de Año, Trimestre y Mes.


#### 2. Renombrar la columna principal

1. Ve a la vista de **Tabla / Datos** (icono de tabla en la barra lateral izquierda).
2. Selecciona la tabla `Dim_Tiempo`.
3. Haz doble clic sobre la cabecera de la primera columna (`[Date]`) y cámbiale el nombre a **`Fecha`**.

#### 3. Marcar como Tabla de Fechas (Requisito Indispensable)

1. En el panel lateral de **Datos**, haz clic derecho sobre el nombre de la tabla `Dim_Tiempo`.
2. Selecciona **Marcar como tabla de fechas** > **Marcar como tabla de fechas**.
3. En el desplegable, selecciona la columna **`Fecha`** y haz clic en **Aceptar**.


#### 4. Configurar el orden del Nombre del Mes

Para evitar que los meses se ordenen alfabéticamente (Abril, Diciembre, Enero...) en los gráficos visuales:

1. En la vista de **Tabla / Datos**, haz clic sobre la columna `Nombre_Mes`.
2. Ve a la pestaña superior **Herramientas de columnas**.
3. Haz clic en la opción **Ordenar por columna** y selecciona **`Numero_Mes`**.



---

### 🛠️ Pasos de configuración previa en el lienzo:

1. **Relaciones en la vista de Modelo:**
   * `FACT_Ventas[Fecha]` $\rightarrow$ `Dim_Tiempo[Fecha]` (Varios a Uno, *:1)

   * `FACT_Ventas[ID_Cliente]` $\rightarrow$ `DIM_Cliente[ID_Cliente]` (Varios a Uno, *:1)

   * `FACT_Ventas[ID_Producto]` $\rightarrow$ `DIM_Producto[ID_Producto]` (Varios a Uno, *:1)


2. **Creación de la tabla de medidas:**
   * Crea una tabla vacía llamada `_Medidas` (Inicio > Introducir datos) e introduce todas las fórmulas del solucionario dentro de ella para mantener ordenado el proyecto.

     >La tabla `_Medidas` **no necesita ninguna columna de datos**; su única función es actuar como un contenedor o carpeta organizada para almacenar las fórmulas DAX del informe.
     >Para configurarla correctamente, sigue estos pasos:
     >
     >1. Al ir a **Inicio > Introducir datos**, Power BI te pedirá definir la tabla. Deja la columna por defecto (llamada `Columna1`), ponle de nombre a la tabla **`_Medidas`** y haz clic en **Cargar**.
     >
     >2. A medida que vayas creando las 15 medidas del solucionario (haciendo clic derecho sobre `_Medidas` > **Nueva medida**), estas se irán guardando dentro de la tabla.
     >
     >3. **Paso final para convertirla en carpeta contenedora:** Una vez que hayas creado al menos una medida DAX dentro de `_Medidas`, haz clic derecho sobre `Columna1` y selecciona **Eliminar del modelo**.
     >
     >Al eliminar la única columna de datos, el icono de la tabla `_Medidas` en el panel lateral cambiará automáticamente a la forma de una **calculadora amarilla**, posicionándose en la parte superior del panel de datos para tener todas tus métricas ordenadas.

## 🗄️ MODELO SEMÁNTICO DE TRABAJO (Esquema en Estrella)

Antes de redactar las fórmulas, asegúrate de tener cargado en Power BI Desktop el siguiente modelo de datos relacionado:

1. **`FACT_Ventas` (Tabla de Hechos):**
   * `ID_Venta` (PK / Clave técnica)
   * `Fecha` (FK -> `Dim_Tiempo[Fecha]`)
   * `ID_Cliente` (FK -> `DIM_Cliente[ID_Cliente]`)
   * `ID_Producto` (FK -> `DIM_Producto[ID_Producto]`)
   * `Cantidad` (Número entero)
   * `Precio_Unitario` (Número decimal)
   * `Importe` (Número decimal)
   * `Coste` (Número decimal)

2. **`DIM_Cliente` (Dimensión):** `ID_Cliente`, `Nombre_Cliente`, `Tipo_Cliente` (Estándar, Preferente, VIP), `Provincia`.
3. **`DIM_Producto` (Dimensión):** `ID_Producto`, `Nombre_Producto`, `Categoria`, `Subcategoria`.
4. **`Dim_Tiempo` (Tabla de Calendario Dedicada):** `Fecha`, `Año`, `Trimestre`, `Mes`, `Nombre_Mes`, `Numero_Mes`.
5. **`_Medidas` (Tabla de Medidas Dedicada):** Tabla vacía creada para alojar todas las fórmulas analíticas del informe.

---

## 🟢 BLOQUE 1: AGREGACIONES Y MÉTRICAS BASE (Nivel Básico)

### 📌 Caso de Negocio 1.1: Volumen de Negocio y Beneficio Bruto
La dirección comercial necesita visualizar en tres tarjetas KPI el volumen total de ventas en euros, el coste total de las operaciones y el beneficio bruto generado.

* **Ejercicios a crear:**
  
  1. `Ventas_Totales`: Suma del campo `Importe` de la tabla de hechos.
  2. `Costes_Totales`: Suma del campo `Coste` de la tabla de hechos.
  3. `Beneficio_Bruto`: Diferencia entre las Ventas Totales y los Costes Totales.

* **Prompt para Copilot / IA:**
  > *"Actúa como analista de datos. Genera tres medidas DAX para la tabla '_Medidas': 1) 'Ventas_Totales' que sume 'FACT_Ventas'[Importe], 2) 'Costes_Totales' que sume 'FACT_Ventas'[Coste], y 3) 'Beneficio_Bruto' que reste las dos anteriores haciendo referencia a los nombres de las medidas entre corchetes. Formato moneda en euros."*

---

### 📌 Caso de Negocio 1.2: Actividad Operativa y Clientes Activos
El departamento de marketing requiere conocer el número total de transacciones realizadas y cuántos clientes distintos han comprado en el periodo seleccionado.

* **Ejercicios a crear:**
  
  4. `Total_Operaciones`: Recuento del número total de filas de la tabla de ventas.
  5. `Clientes_Unicos`: Recuento de los códigos distintos de clientes que han registrado compras.

---

## 🟡 BLOQUE 2: RATIOS Y CUOTAS PORCENTUALES (Nivel Intermedio)

### 📌 Caso de Negocio 2.1: Margen de Rentabilidad Seguro
Se requiere calcular el porcentaje de margen comercial sobre ventas (`Beneficio_Bruto / Ventas_Totales`). La fórmula debe ser inmune a errores de división por cero cuando se filtren periodos sin ventas.

* **Ejercicio a crear:**
  
  6. `Porcentaje_Margen`: Ratio del margen comercial utilizando la función de división segura.

* **Prompt para Copilot / IA:**
  > *"Crea una medida DAX llamada 'Porcentaje_Margen' en '_Medidas'. Debe dividir '[Beneficio_Bruto]' entre '[Ventas_Totales]' utilizando obligatoriamente la función DIVIDE para evitar el error de división por cero. Asigna formato de porcentaje con 2 decimales."*

---

### 📌 Caso de Negocio 2.2: Peso Relativo y Cuota de Mercado (%)
Al presentar una matriz de ventas por `Categoria` de producto, el director de ventas desea ver dos columnas: el importe absoluto vendido y qué porcentaje representa esa categoría sobre el **Total General de la empresa** (cuota de participación).

* **Ejercicio a crear:**
  
  7. `Porcentaje_Cuota_Total`: Divide las ventas de la categoría activa entre las ventas totales de la empresa (eliminando los filtros de la tabla de ventas con `ALL` o `REMOVEFILTERS`).

---

### 📌 Caso de Negocio 2.3: Cuota sobre la Categoría Padre
En una matriz jerárquica que muestra `Categoria` y `Subcategoria`, se necesita calcular el peso porcentual que tiene cada subcategoría respecto a su categoría madre, manteniendo el filtro de la categoría pero ignorando el de la subcategoría.

* **Ejercicio a crear:**
  
  8. `Porcentaje_Cuota_Categoria`: Uso de `ALLEXCEPT` para mantener el filtro de `DIM_Producto[Categoria]` al calcular el denominador.

---

## 🟠 BLOQUE 3: INTELIGENCIA DE TIEMPO Y COMPARATIVAS INTERANUALES (Nivel Avanzado)

### 📌 Caso de Negocio 3.1: Ventas Acumuladas del Año (YTD)
El departamento financiero evalúa el avance del presupuesto del año en curso. Necesita ver en un gráfico de líneas cómo se acumulan las ventas desde el 1 de enero hasta la fecha actual de cada mes.

* **Ejercicio a crear:**
  
  9. `Ventas_YTD`: Acumulado anual del importe de ventas utilizando la dimensión de tiempo dedicada.

* **Prompt para Copilot / IA:**
  > *"Necesito una medida DAX de inteligencia de tiempo llamada 'Ventas_YTD' para la tabla '_Medidas'. Debe calcular el acumulado anual de las '[Ventas_Totales]' usando la función TOTALYTD sobre la columna de fecha continua 'Dim_Tiempo'[Fecha]."*

---

### 📌 Caso de Negocio 3.2: Comparativa contra el Año Anterior (PY / Same Period Last Year)
Para medir el rendimiento de la red comercial, se necesita comparar las ventas del periodo seleccionado (ej. Mayo 2026) con lo que se vendió exactamente en el mismo periodo del año pasado (Mayo 2025).

* **Ejercicio a crear:**
  
  10. `Ventas_Año_Anterior`: Cálculo de ventas desplazando el contexto de filtro 12 meses atrás con `SAMEPERIODLASTYEAR`.

---

### 📌 Caso de Negocio 3.3: Análisis de Crecimiento Interanual (YoY Change & YoY %)
A partir de las ventas actuales y las del año anterior, la dirección exige dos indicadores ejecutivos: el incremento en euros y la tasa de crecimiento porcentual interanual.

* **Ejercicios a crear:**
  
  11. `Crecimiento_Interanual_Euros`: Cifra absoluta (`[Ventas_Totales] - [Ventas_Año_Anterior]`).
  12. `Crecimiento_Interanual_Porcentaje`: Variación relativa (`DIVIDE([Crecimiento_Interanual_Euros], [Ventas_Año_Anterior])`).

---

## 🔴 BLOQUE 4: FILTROS AVANZADOS Y CONTEXTOS ESPECIALES (Nivel Experto)

### 📌 Caso de Negocio 4.1: Ventas Segmentadas por Clientes VIP
Se desea calcular el volumen de ventas generado exclusivamente por los clientes calificados como `"VIP"`, independientemente de lo que el usuario seleccione en los filtros de tipo de cliente del informe.

* **Ejercicio a crear:**
  
  13. `Ventas_Clientes_VIP`: Modificación del contexto de filtro mediante `CALCULATE` para forzar la condición `DIM_Cliente[Tipo_Cliente] = "VIP"`.

---

### 📌 Caso de Negocio 4.2: Ranking Dinámico de Productos
En una tabla visual de productos, se quiere mostrar una columna que numere la posición ordinal (Ranking 1, 2, 3...) de cada producto según su volumen de ventas.

* **Ejercicio a crear:**
  
  14. `Ranking_Productos`: Clasificación dinámica utilizando la función `RANKX` combinada con `ALL`.

---

### 📌 Caso de Negocio 4.3: Título Dinámico e Interactivo para Informes
Para mejorar la experiencia de usuario (UX), el título del cuadro de mando debe cambiar dinámicamente según la provincia que seleccione el usuario en el segmentador de datos. Si no hay ninguna seleccionada, debe mostrar `"Todas las Provincias"`.

* **Ejercicio a crear:**
  
  15. `Titulo_Dinamico_Provincia`: Captura de la selección del usuario mediante `SELECTEDVALUE`.

---

## 🔑 SOLUCIONARIO COMPLETO DE MEDIDAS DAX

A continuación se detalla el código DAX exacto para cada uno de los ejercicios. Los alumnos deben revisar y auditar estas fórmulas tras generarlas con la IA:

```dax
-- =================================================================
-- BLOQUE 1: AGREGACIONES BASE
-- =================================================================

-- 1. Ventas Totales
Ventas_Totales = SUM('FACT_Ventas'[Importe])

-- 2. Costes Totales
Costes_Totales = SUM('FACT_Ventas'[Coste])

-- 3. Beneficio Bruto
Beneficio_Bruto = [Ventas_Totales] - [Costes_Totales]

-- 4. Total de Operaciones
Total_Operaciones = COUNTROWS('FACT_Ventas')

-- 5. Clientes Únicos
Clientes_Unicos = DISTINCTCOUNT('FACT_Ventas'[ID_Cliente])


-- =================================================================
-- BLOQUE 2: RATIOS Y CUOTAS PORCENTUALES
-- =================================================================

-- 6. Porcentaje de Margen Comercial
Porcentaje_Margen = 
DIVIDE(
    [Beneficio_Bruto],
    [Ventas_Totales],
    0
)

-- 7. Porcentaje de Cuota sobre el Total General
Porcentaje_Cuota_Total = 
DIVIDE(
    [Ventas_Totales],
    CALCULATE(
        [Ventas_Totales],
        ALL('FACT_Ventas')
    ),
    0
)

-- 8. Porcentaje de Cuota sobre la Categoría Padre
Porcentaje_Cuota_Categoria = 
DIVIDE(
    [Ventas_Totales],
    CALCULATE(
        [Ventas_Totales],
        ALLEXCEPT('DIM_Producto', 'DIM_Producto'[Categoria])
    ),
    0
)


-- =================================================================
-- BLOQUE 3: INTELIGENCIA DE TIEMPO
-- =================================================================

-- 9. Ventas Acumuladas del Año (YTD)
Ventas_YTD = 
TOTALYTD(
    [Ventas_Totales],
    'Dim_Tiempo'[Fecha]
)

-- 10. Ventas del Año Anterior (Same Period Last Year)
Ventas_Año_Anterior = 
CALCULATE(
    [Ventas_Totales],
    SAMEPERIODLASTYEAR('Dim_Tiempo'[Fecha])
)

-- 11. Crecimiento Interanual en Euros
Crecimiento_Interanual_Euros = [Ventas_Totales] - [Ventas_Año_Anterior]

-- 12. Crecimiento Interanual Porcentual (YoY %)
Crecimiento_Interanual_Porcentaje = 
DIVIDE(
    [Crecimiento_Interanual_Euros],
    [Ventas_Año_Anterior],
    0
)


-- =================================================================
-- BLOQUE 4: FILTROS AVANZADOS Y CONTEXTO
-- =================================================================

-- 13. Ventas Exclusivas a Clientes VIP
Ventas_Clientes_VIP = 
CALCULATE(
    [Ventas_Totales],
    'DIM_Cliente'[Tipo_Cliente] = "VIP"
)

-- 14. Ranking Dinámico de Productos por Venta
Ranking_Productos = 
IF(
    HASONEVALUE('DIM_Producto'[Nombre_Producto]),
    RANKX(
        ALL('DIM_Producto'),
        [Ventas_Totales],
        ,
        DESC
    ),
    BLANK()
)

-- 15. Título Dinámico por Selección de Provincia
Titulo_Dinamico_Provincia = 
"Informe de Rendimiento: " & 
SELECTEDVALUE(
    'DIM_Cliente'[Provincia], 
    "Todas las Provincias"
)
```

---

## 📋 PROTOCOLO DE AUDITORÍA Y VALIDACIÓN VISUAL EN EL AULA

Una vez creadas las medidas en Power BI Desktop, se debe verificar su funcionamiento construyendo las siguientes visualizaciones de prueba:

| Matriz / Objeto Visual | Campos / Medidas a colocar | Comprobación de Validación |
| :--- | :--- | :--- |
| **Tarjeta KPI** | `[Ventas_YTD]` y `[Crecimiento_Interanual_Porcentaje]` | Cambia el año en el segmentador y verifica que la cifra acumulada y el % reaccionen. |
| **Tabla / Matriz** | `DIM_Producto[Categoria]`, `[Ventas_Totales]`, `[Porcentaje_Cuota_Total]` | La suma de la columna `[Porcentaje_Cuota_Total]` debe dar exactamente el 100,0%. |
| **Gráfico de Líneas** | Eje X: `Dim_Tiempo[Nombre_Mes]`<br>Valores: `[Ventas_Totales]`, `[Ventas_Año_Anterior]` | Deben mostrarse dos líneas paralelas comparando el comportamiento mes a mes de ambos años. |
| **Tarjeta de Texto** | `[Titulo_Dinamico_Provincia]` | Haz clic en un segmentador de Provincia y comprueba que el título de la tarjeta se actualiza solo. |

Para configurar cada uno de esos 4 objetos visuales en la interfaz de Power BI (como la que se muestra en tu imagen), debes arrastrar los datos a las siguientes casillas del panel de configuración de datos:

---

### 1. Tarjeta / Tarjeta KPI

* **Tipo de objeto visual:** Selecciona **Tarjeta** (icono `123`) o **Tarjeta KPI**.


* **Campos a colocar:**
* En la casilla **Valor**: Arrastra `[Ventas_YTD]`.


* *(Si usas Tarjeta KPI)* En **Eje de tendencia**: Arrastra `Dim_Tiempo[Fecha]`.
* *(Para el porcentaje)* Crea una **segunda Tarjeta** e introduce en **Valor**: `[Crecimiento_Interanual_Porcentaje]`.


El enunciado pide usar el objeto visual específico **KPI** (que incluye indicador, destino y tendencia) y se puede resolver en una **sola tarjeta KPI** (o en un visual de **Tarjeta Nueva** de Power BI).

---

### Configuración en una sola Tarjeta KPI

Si utilizas el objeto visual nativo **KPI** (el icono con la gráfica y la flecha arriba/abajo en el panel de visualizaciones):

* **Valor (Indicator):** `[Ventas_YTD]`

* **Eje de tendencia (Trend axis):** `Dim_Tiempo[Fecha]` (o `Dim_Tiempo[Numero_Mes]`)


* **Destino (Target):** `[Ventas_Año_Anterior]`


> **¿Por qué?** El visual KPI calcula de forma automática el porcentaje de variación (`[Crecimiento_Interanual_Porcentaje]`) comparando el **Valor** actual con el **Destino**.

---

### Opción alternativa: Con el visual "Tarjeta (nueva)"

Si prefieres usar la **Tarjeta nueva** (el visual que permite mostrar varios indicadores juntos en un mismo bloque):

* **Valor:** Arrastra ambas medidas al mismo campo:
1. `[Ventas_YTD]`

2. `[Crecimiento_Interanual_Porcentaje]`




---

### Comprobación del Ejercicio

1. Añade un **Segmentador de datos** (*Slicer*) con el campo `Dim_Tiempo[Año]`.


2. Selecciona **2026**.


3. Verifica que la tarjeta KPI muestre el valor acumulado de 2026 y calcule el % de diferencia respecto al mismo periodo del año 2025.


---

### 2. Tabla / Matriz

* **Tipo de objeto visual:** Selecciona **Tabla** o **Matriz**.


* **Campos a colocar:**
* En **Filas** (o **Columnas** en el caso de Tabla): Arrastra `DIM_Producto[Categoria]`.


* En **Valores**: Arrastra las dos medidas `[Ventas_Totales]` y `[Porcentaje_Cuota_Total]`.





---

### 3. Gráfico de Líneas

* **Tipo de objeto visual:** Selecciona **Gráfico de líneas**.


* **Campos a colocar:**
* En **Eje X**: Arrastra `Dim_Tiempo[Nombre_Mes]`.


* En **Eje Y** (o **Valores**): Arrastra juntos `[Ventas_Totales]` y `[Ventas_Año_Anterior]`.





---

### 4. Tarjeta de Texto (Título Dinámico)

* **Tipo de objeto visual:** Selecciona **Tarjeta** (icono `123`) o **Tarjeta de varias filas**.


* **Campos a colocar:**
* En **Valor**: Arrastra la medida `[Titulo_Dinamico_Provincia]`.