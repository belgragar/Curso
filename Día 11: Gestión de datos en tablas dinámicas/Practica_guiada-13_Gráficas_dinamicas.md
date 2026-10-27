# Práctica Guiada 13: GRÁFICOS DINÁMICOS Y CUADROS DE MANDO

Durante esta práctica vas a construir un cuadro de mando comercial ejecutivo paso a paso, aplicando las técnicas de maquetación, formato e integración gráfica explicadas.

## Datos de partida

Crea una hoja denominada `Ventas` y copia los siguientes datos comenzando en la celda `A1`.

```text
ID_Venta	Fecha	Comercial	Provincia	Producto	Categoria	Canal	Importe
V001	05/01/2026	Ana	Madrid	Portátil	Informática	Tienda Física	1250
V002	08/01/2026	Luis	Barcelona	Monitor	Informática	Tienda Online	680
V003	12/01/2026	Marta	Valencia	Teclado	Periféricos	Tienda Física	320
V004	18/01/2026	Ana	Sevilla	Impresora	Informática	Tienda Online	890
V005	25/01/2026	Luis	Madrid	Ratón	Periféricos	Tienda Física	175
V006	03/02/2026	Marta	Barcelona	Portátil	Informática	Tienda Online	1450
V007	09/02/2026	Ana	Valencia	Monitor	Informática	Tienda Física	720
V008	15/02/2026	Luis	Sevilla	Teclado	Periféricos	Tienda Online	295
V009	21/02/2026	Marta	Madrid	Impresora	Informática	Tienda Física	970
V010	27/02/2026	Ana	Barcelona	Ratón	Periféricos	Tienda Online	210
V011	04/03/2026	Luis	Valencia	Portátil	Informática	Tienda Física	1320
V012	10/03/2026	Marta	Sevilla	Monitor	Informática	Tienda Online	760
V013	16/03/2026	Ana	Madrid	Teclado	Periféricos	Tienda Física	340
V014	22/03/2026	Luis	Barcelona	Impresora	Informática	Tienda Online	920
V015	28/03/2026	Marta	Valencia	Ratón	Periféricos	Tienda Física	190
V016	04/04/2026	Ana	Sevilla	Portátil	Informática	Tienda Online	1510
V017	11/04/2026	Luis	Madrid	Monitor	Informática	Tienda Física	740
V018	17/04/2026	Marta	Barcelona	Teclado	Periféricos	Tienda Online	310
V019	23/04/2026	Ana	Valencia	Impresora	Informática	Tienda Física	850
V020	29/04/2026	Luis	Sevilla	Ratón	Periféricos	Tienda Online	225

```

## Paso 1. Preparación de datos y lienzo visual

1. Convierte la lista en **Tabla Estructurada** (`Ctrl + T`) y nómbrala `Tbl_Ventas_Dashboard`.
2. Crea una nueva hoja llamada `Dashboard`.
3. Ve a **Vista** $\rightarrow$ desmarca **Líneas de cuadrícula** para obtener un lienzo totalmente blanco.

## Paso 2. Tarjeta KPI de Facturación Total

1. En la hoja `Dashboard`, crea una tabla dinámica básica que muestre la **Suma de Importe** total en la celda `Q1` (zona de trabajo auxiliar).
   - La celda `Q1` contendrá el título "Suma de Importe".
   - La celda `Q2` contendrá la cifra numérica del total.
2. Configura el número como Moneda (€) desde la configuración del campo de valor.
3. Inserta un rectángulo con esquinas redondeadas y ajusta sus dimensiones exactamente al rango `A2:C5` manteniendo pulsada la tecla `Alt` mientras arrastras los extremos del rectángulo.
4. Selecciona la forma, escribe `=` en la barra de fórmulas y haz clic en la celda del total `Z2`.
5. Aplicar jerarquía visual de texto:
   - **Cifra clave** (`=Dashboard!Z2`): Tamaño 18 pt - 22 pt, Negrita, alineación centrada.
   - **Etiqueta explicativa** ("Facturación Total"): Tamaño secundario 9 pt - 11 pt, texto normal (sin negrita), ubicada debajo de la cifra. (El tamaño de la cifra ha de ser al menos el doble que el del título)

## Paso 3. Gráfico 1 — Facturación por Comercial (Columnas)

1. Crea una tabla dinámica en la zona auxiliar `Q5`: **FILAS:** `Comercial`, **VALORES:** `Suma de Importe`.
2. Inserta un gráfico dinámico de **Columnas agrupadas** y colócalo en el lienzo visible.
3. Haz clic derecho en los botones grises del gráfico $\rightarrow$ **Ocultar todos los botones de campo en gráfico**.
4. Modifica el *Ancho del entrepaño* (*Gap Width*) a **90%**.
5. Asigna el título: **Facturación por Comercial**.

## Paso 4. Gráfico 2 — Facturación por Categoría (Barras horizontales)

1. Crea una tabla dinámica en la zona auxiliar `Q12`: **FILAS:** `Categoria`, **VALORES:** `Suma de Importe`.
2. Inserta un gráfico dinámico de **Barras agrupadas**.
3. Oculta los botones de campo y elimina la leyenda innecesaria.
4. Asigna el título: **Facturación por Categoría**.

## Paso 5. Gráfico 3 — Evolución Temporal (Líneas)

1. Crea una tabla dinámica en la zona auxiliar `Q18`: **FILAS:** `Fecha` (agrupada por Meses), **VALORES:** `Suma de Importe`.
2. Inserta un gráfico dinámico de **Líneas con marcadores**.
3. Asigna el título: **Evolución Mensual de Ventas**.

## Paso 6. Controles interactivos y sincronización

1. Inserta un **Segmentador de Datos** para `Provincia` y configúralo a `4` columnas horizontales.
2. Inserta una **Línea de Tiempo** para el campo `Fecha`.
3. Usa **Conexiones de informes** en ambos controles para vincular las tres tablas dinámicas.

## Paso 7. Organización visual final (Patrón F/Z)

* **Fila Superior:** Tarjeta KPI + Segmentador horizontal de Provincia.
* **Fila Media:** Gráfico de Comercial (izquierda) y Gráfico de Categoría (derecha).
* **Fila Inferior:** Gráfico de Evolución Temporal a ancho completo + Línea de Tiempo.

### Ancho completo de un gráfico

Un gráfico a "ancho completo" significa que abarca todo el ancho del lienzo (cubriendo las mismas columnas que los gráficos superiores combinados) para mostrar cómodamente la secuencia temporal.

1. Selecciona el **Gráfico de Evolución Temporal** (líneas).
2. Mantén presionada la tecla **`Alt`**.
3. Arrastra la esquina izquierda del gráfico para alinearlo al borde izquierdo del lienzo (ejemplo: **Columna A**).
4. Arrastra la esquina derecha manteniendo **`Alt`** presionado hasta el borde derecho que cubren los dos gráficos de arriba (ejemplo: **Columna N** o **P**).
5. De este modo, la línea del gráfico tiene suficiente recorrido horizontal para representar los meses sin apretujar los datos.

#### ¿Dónde ubicar exactamente la Línea de Tiempo y los controles?

Seguir el **Patrón F/Z** permite colocar cada elemento en su bloque natural utilizando el ajuste magnético con la tecla **`Alt`**:

* **Bloque Superior (Filas 2 a 8):**
* **`A2:C5`** $\rightarrow$ Tarjeta KPI de Facturación Total.
* **`E2:N5`** $\rightarrow$ **Segmentador de Provincia** (configurado a 4 columnas horizontales).


* **Bloque Medio (Filas 7 a 18):**
* **`A7:G18`** $\rightarrow$ Gráfico 1: Facturación por Comercial (Columnas).
* **`H7:N18`** $\rightarrow$ Gráfico 2: Facturación por Categoría (Barras).


* **Bloque Inferior (Filas 20 a 32):**
* **`A20:N28`** $\rightarrow$ Gráfico 3: Evolución Mensual de Ventas (Líneas) a **ancho completo** (de la columna `A` a la `N`).
* **`A29:N32`** $\rightarrow$ **Línea de Tiempo de Fecha**, ubicada justo **debajo del gráfico de líneas** y abarcando también todo el ancho (`A` a `N`), lo que permite filtrar visualmente los periodos justo donde se observa la curva temporal.

---



* **Documentación oficial:** [Microsoft Support: Crear un gráfico dinámico](https://support.microsoft.com/es-ES/Excel/get-started/create-a-pivotchart)
* **Guía de diseño UX/UI:** [Microsoft Learn: Buenas prácticas para el diseño de paneles e informes](https://learn.microsoft.com/es-es/power-bi/create-reports/service-dashboards-design-tips)
* **Herramientas recomendadas:** Microsoft Excel 2016 o superior / Microsoft 365.

```

```
