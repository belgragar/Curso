# EJERCICIOS 19: HERRAMIENTAS DE TABLAS DINÁMICAS
## B1.2. Práctica Guiada (Bloque 1)

### Datos de partida (Bloque 1)

Copia la siguiente tabla y pégala en la celda **A1** de una hoja nueva de Excel. Transfórmala en Tabla Estructurada (`Ctrl+T`), asígnale el nombre `Tbl_Ventas` y verifica que los formatos de datos sean correctos (Fechas y Moneda).

```text
Fecha	Vendedor	Región	Producto	Categoría	Importe	Coste
05/01/2026	Ana	Norte	Teclado	Periféricos	1250	800
08/01/2026	Carlos	Sur	Monitor	Monitores	1850	1200
12/01/2026	Marta	Norte	Ratón	Periféricos	720	400
18/01/2026	Luis	Este	Portátil	Informática	3200	2100
23/01/2026	Ana	Oeste	Monitor	Monitores	2140	1400
29/01/2026	Carlos	Sur	Teclado	Periféricos	980	600
03/02/2026	Marta	Norte	Portátil	Informática	4150	2800
07/02/2026	Luis	Este	Ratón	Periféricos	860	500
14/02/2026	Ana	Oeste	Monitor	Monitores	2760	1800
21/02/2026	Carlos	Sur	Portátil	Informática	3890	2600
27/02/2026	Marta	Norte	Teclado	Periféricos	1140	700
04/03/2026	Luis	Este	Monitor	Monitores	2250	1500
09/03/2026	Ana	Oeste	Ratón	Periféricos	930	550
16/03/2026	Carlos	Sur	Portátil	Informática	4620	3100
22/03/2026	Marta	Norte	Monitor	Monitores	1980	1300
28/03/2026	Luis	Este	Teclado	Periféricos	1320	850
05/04/2026	Ana	Oeste	Portátil	Informática	3580	2400
11/04/2026	Carlos	Sur	Monitor	Monitores	2410	1600
17/04/2026	Marta	Norte	Ratón	Periféricos	790	450
24/04/2026	Luis	Este	Portátil	Informática	4270	2900

```

### Pasos guiados

1. **Creación:** Inserta una Tabla Dinámica en una nueva hoja (`TD_Ventas`) basada en `Tbl_Ventas`.


2. **Estructura inicial:** Arrastra `Región` a **FILAS** e `Importe` tres veces a **VALORES**.


3. **Métricas de Valor:**
* Campo 1: Configúralo como **Suma de Importe**, renombrado a "Ventas Totales" con formato Moneda (`€`) persistente.


* Campo 2: Configúralo como **Promedio de Importe**, renombrado a "Venta Media" con formato Moneda (`€`) persistente.


* Campo 3: Configúralo como **% del total general** en la pestaña *Mostrar valores como*, renombrado a "% Cuota" con formato Porcentaje (`0.0%`).




4. **Campo Calculado (Beneficio):**
* Ve a *Analizar tabla dinámica > Campos, elementos y conjuntos > Campo calculado*.
* Nombre: `Beneficio_Bruto`.
* Fórmula: `= Importe - Coste`.
* Asigna formato de Moneda persistente.


5. **Diseño de Informe:**
* Añade `Vendedor` en **FILAS** por debajo de `Región`.
* En la pestaña **Diseño**, selecciona *Diseño de informe > Mostrar en formato tabular*.
* Haz clic en *Diseño de informe > Repetir todas las etiquetas de elementos*.



---

## B1.3. Ejercicios autónomos progresivos (Bloque 1)

### 🟢 Nivel Básico B1 — Operaciones y Formato Persistente

1. Crea una Tabla Dinámica a partir de `Tbl_Ventas` con **FILAS:** `Categoría` y **VALORES:** `Importe`.
2. Realiza sucesivamente los siguientes análisis en el campo de valor:
   - Suma de las ventas por categoría.
   - Promedio de las ventas por categoría.
   - Venta máxima registrada en cada categoría.
   - Venta mínima registrada en cada categoría.
   - *Pregunta de reflexión:* ¿Por qué el resultado cambia aunque el campo utilizado en VALORES sea siempre `Importe`?
3. Finalmente, vuelve a configurar el campo como **Suma** y aplica formato de moneda con dos decimales.
   - Asegúrate de aplicar formato de moneda persistente únicamente desde *Configuración de campo de valor > Formato de número*.
4. Configura otro campo de valor: **Recuento de Operaciones**.
   - *Pregunta de reflexión:* ¿Por qué el número de operaciones no cambia aunque apliquemos o quitemos el formato de moneda a la columna `Importe`?

---

### 🟡 Nivel Intermedio B1 — Campo Calculado de Comisión Comercial

1. Utilizando la misma fuente, crea una Tabla Dinámica con **FILAS:** `Vendedor` y **VALORES:** `Suma de Importe`.
2. Crea un Campo Calculado llamado `Comision_Vendedor` con la fórmula `= Importe * 0.04` (4% sobre las ventas).
3. Añade un segundo Campo Calculado llamado `Venta_Neta` con la fórmula `= Importe - Comision_Vendedor`.
4. Asigna formato de Moneda (`€`) a ambos campos calculados.

5. Crea una nueva Tabla Dinámica con **FILAS:** `Región`y **VALORES:** `Suma de Importe`.
6. Configura el campo de valor para mostrar el **% del total general**. Después:
   - Comprueba que las regiones representan conjuntamente el 100 %.
   - Identifica qué región tiene una mayor participación.
   - Cambia temporalmente el campo de FILAS de `Región` a `Categoría`.
   - Observa cómo cambia la distribución porcentual.
   - *Pregunta de reflexión:* ¿Qué diferencia existe entre mostrar una cantidad en euros y mostrar esa misma cantidad como porcentaje del total?
  
---

### 🟠 Nivel Avanzado B1 — Agrupación por Rangos e Informe Tabular

1. Crea una Tabla Dinámica con **FILAS:** `Importe` y **VALORES:** `Vendedor` (en modo Recuento).
   - Haz clic derecho sobre un importe en la tabla dinámica y selecciona **Agrupar**.
   - Establece el rango de agrupación: *Comenzar en: 0*, *Terminar en: 5000*, *Por: 1000*.
   - Añade `Categoría` a **COLUMNAS**.
   - Cambia el diseño del informe a **Formato Tabular** para estructurar correctamente la visualización.
2. Crea otra Tabla Dinámica con: **FILAS:** `Vendedor`, **COLUMNAS:** `Región` y **VALORES:** `Importe`. Añade el campo `Importe` tres veces a VALORES y configura:
   - **Suma de Importe**
   - **Promedio de Importe**
   - **% del total general**.
   - Aplica formato de **moneda** a los dos primeros indicadores y formato de **porcentaje** al tercero.

#### Tareas adicionales para la segunda tabla

1. Cambia `Región` de COLUMNAS a FILAS.
2. Observa cómo cambia la estructura del informe.
3. Vuelve a colocar `Región` en COLUMNAS.
4. Identifica qué vendedor obtiene el mayor importe total.

---

### 🔴 Experto B1: Reporte de Margen Directivo

**Objetivo:** Construir un reporte analítico de rendimiento por categoría y producto utilizando campos calculados y formato tabular.

1. Crea una **nueva hoja** en tu libro de Excel y cámbiale el nombre a la pestaña por **`Reporte_Margenes`**.

2. Crea una Tabla Dinámica a partir de `Tbl_Ventas` y sitúala en esa hoja.

3. Configura los campos de fila y valores de forma anidada:
   * **FILAS:** Arrastra primero `Categoría` y, justo debajo, arrastra `Producto`.
   * **VALORES:**
     * Suma de `Importe` (Renombrada como "Facturación").
     * Suma de `Coste` (Renombrada como "Costes Directos").

4. Añade los siguientes **Campos Calculados**:
   * `Margen_Euros`: Fórmula `= Importe - Coste`.
   * `Margen_Porcentual`: Fórmula `= (Importe - Coste) / Importe`.

5. Aplica los formatos de número correspondientes (`€` para los importes absolutos y `%` con un decimal para el margen porcentual).

6. Ve a la pestaña *Diseño*, cambia el diseño del informe a **Formato Tabular** y activa **Repetir todas las etiquetas de elementos** para que cada fila muestre su categoría claramente.

> ⚠️ **Nota de Advertencia Técnica (Pro-Tip):**
> Si al crear los campos calculados obtienes un error de tipo `#¡DIV/0!` o números negativos extraños en `Margen_Euros`, asegúrate de que el campo numérico `Importe` **no esté agrupado** (por rangos o tramos) en ninguna otra Tabla Dinámica previa de este mismo libro. Como todas comparten el mismo origen, agrupar un número en una hoja puede convertirlo en texto para el resto de las tablas, anulando los cálculos matemáticos. Si te ocurre, ve a la otra tabla y selecciona *Desagrupar*.
