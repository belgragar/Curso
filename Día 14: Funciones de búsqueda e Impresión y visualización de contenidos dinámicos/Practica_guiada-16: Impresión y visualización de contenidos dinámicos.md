# 📝 Práctica Guiada 16: Impresión y Visualización de Contenidos Dinámicos

* **Curso:** IFCT56 Excel Avanzado y Power BI
* **Módulo:** Módulo 2 – Excel Avanzado
* **Epígrafe de Referencia:** 2.6 Impresión y visualización de contenidos dinámicos (Manual de Teoría)
* **Contexto del Proyecto:** Red de Cuevas Prehistóricas y Turísticas del Principado de Asturias
* **Versión de Referencia:** Microsoft 365 (Apps, edición educativa) / Excel 2021

---

## 🎯 1. Objetivos de Aprendizaje

Al finalizar esta práctica guiada, el alumnado será capaz de:
1. **Configurar el área de impresión y la maquetación de página** para informes que combinan Tablas Dinámicas, Gráficos Dinámicos y Segmentadores de Datos (márgenes, orientación, escala y vista previa `Ctrl + P`).
2. **Aplicar Títulos de Impresión** para repetir encabezados de fila y columna en informes multipágina, activando la impresión de la cuadrícula y encabezados de celda.
3. **Configurar opciones de impresión específicas para Tablas Dinámicas**, incluyendo la repetición de etiquetas de elementos y la inserción automática de saltos de página por grupo de datos.
4. **Optimizar la visualización interactiva en pantalla (Dashboard)** mediante la inmovilización de paneles, el cambio entre vistas del libro (`Normal`, `Diseño de página`, `Vista previa de salto de página`) y la ocultación de elementos de interfaz (botones de campo y lista de campos).

---

## 📊 2. Base de Datos de Origen: Red de Cuevas de Asturias

Copia la siguiente tabla de datos sobre la gestión turística y de conservación de las cuevas de Asturias y pégala en la celda **A1** de una hoja nueva de Excel (También está disponible como `base_datos_cuevas_asturias.xslx`). A continuación, conviértela en **Tabla Estructurada** (`Ctrl + T`) con el nombre **`Tbl_Cuevas`**.

| ID_Registro | Cueva | Municipio | Tipo_Visita | Temporada | Visitantes | Ingresos_Euros | Guia_Asignado |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: | :--- |
| CUV-101 | Tito Bustillo | Ribadesella | Arte Rupestre | Alta | 1.450 | 11.600 € | Covadonga M. |
| CUV-102 | El Pindal | Ribadedeva | Arte Rupestre | Alta | 820 | 4.920 € | Pelayo G. |
| CUV-103 | Cueva de Candamo | Candamo | Arte Rupestre | Baja | 310 | 1.860 € | Ana F. |
| CUV-104 | El Buxu | Cangas de Onís | Arte Rupestre | Baja | 240 | 1.440 € | Pelayo G. |
| CUV-105 | Cueva de Huerta | Teverga | Espeleoturismo | Alta | 950 | 7.600 € | David R. |
| CUV-106 | La Lluera | Oviedo / San Claudio | Arte Rupestre | Baja | 180 | 1.080 € | Ana F. |
| CUV-107 | Tito Bustillo | Ribadesella | Arte Rupestre | Baja | 620 | 4.960 € | Covadonga M. |
| CUV-108 | El Pindal | Ribadedeva | Arte Rupestre | Baja | 390 | 2.340 € | Pelayo G. |
| CUV-109 | Cueva de Huerta | Teverga | Espeleoturismo | Baja | 410 | 3.280 € | David R. |
| CUV-110 | Tito Bustillo | Ribadesella | Taller Didáctico | Alta | 890 | 8.900 € | Covadonga M. |
| CUV-111 | Cueva de Candamo | Candamo | Arte Rupestre | Alta | 680 | 4.080 € | Ana F. |
| CUV-112 | El Buxu | Cangas de Onís | Arte Rupestre | Alta | 530 | 3.180 € | Pelayo G. |
| CUV-113 | Cueva de Huerta | Teverga | Taller Didáctico | Alta | 720 | 5.760 € | David R. |
| CUV-114 | Tito Bustillo | Ribadesella | Arte Rupestre | Alta | 1.620 | 12.960 € | Covadonga M. |

---

## 🛠️ 3. Desarrollo Paso a Paso de la Práctica Guiada

### 📍 BLOQUE 1: Construcción de la Estructura Dinámica Básica

1. **Crear la Tabla Dinámica Principal:**
   * Haz clic dentro de `Tbl_Cuevas` y ve a **Insertar > Tabla dinámica**.
   * Ubícala en una nueva hoja denominada **`Informe_Explotacion`**.
   * Configura las áreas del panel de campos:
     * **FILAS:** `Cueva` y, debajo, `Tipo_Visita`.
     * **COLUMNAS:** `Temporada`.
     * **VALORES:** `Suma de Visitantes` y `Suma de Ingresos_Euros`.
2. **Dar Formato Persistente a los Valores:**
   * En el área Valores, abre **Configuración de campo de valor > Formato de número**:
     * `Visitantes`: Formato Número entero con separador de millares (`#,##0`).
     * `Ingresos_Euros`: Formato Moneda (`#,##0 €`).
   * Aplica el **Diseño de Informe Tabular** (`Diseño > Diseño de informe > Mostrar en formato tabular`) y activa **Repetir todas las etiquetas de elementos**.
3. **Insertar Gráfico Dinámico y Segmentador:**
   * Con la Tabla Dinámica seleccionada, ve a **Analizar tabla dinámica > Gráfico dinámico** e inserta un **Gráfico de Columnas Agrupadas**.
   * Inserta un **Segmentador de datos** para el campo `Municipio` (**Analizar tabla dinámica > Insertar segmentación de datos**). Configura el segmentador a **3 columnas** horizontales.

---

### 📍 BLOQUE 2: Configuración del Área de Impresión y Títulos de Impresión

1. **Delimitar el Área de Impresión Completa:**
   * Selecciona el rango que abarca la Tabla Dinámica, el Gráfico Dinámico y el Segmentador de datos (por ejemplo, `A1:M35`).
   * Ve a **Diseño de página > Área de impresión > Establecer área de impresión**.
2. **Configurar los Títulos de Impresión (Repetición de Encabezados):**
   * Ve a **Diseño de página > Imprimir títulos**.
   * En la ficha **Hoja**, en la casilla **Repetir filas en la parte superior**, selecciona las filas de encabezado de la Tabla Dinámica (por ejemplo, `$3:$4`).
   * Marca las casillas:
     * ☑ **Líneas de cuadrícula** (para que se impriman las divisiones de celda).
     * ☑ **Encabezados de filas y columnas** (para mostrar las letras A, B, C y números 1, 2, 3 en el papel).
   * *Nota técnica:* Recuerda que si el botón *Imprimir títulos* aparece atenuado (en gris), se debe a que estás editando una celda o tienes seleccionado el gráfico dinámico. Haz clic en una celda vacía para reactivarlo.

---

### 📍 BLOQUE 3: Impresión Especializada de Tablas Dinámicas y Saltos de Página

1. **Insertar Salto de Página Automático por Cueva:**
   * Haz clic derecho sobre una celda del campo `Cueva` dentro de la Tabla Dinámica.
   * Selecciona **Configuración de campo**.
   * En la pestaña **Diseño e imprimir**, marca la casilla:
     * ☑ **Insertar salto de página después de cada elemento**.
   * *Efecto:* Cada cueva (Tito Bustillo, El Pindal, Candamo, etc.) se imprimirá en una página independiente junto con sus tipos de visita asociados.
2. **Repetir Etiquetas de Elementos al Imprimir:**
   * En la misma ventana de **Configuración de campo**, en la pestaña **Diseño e imprimir**, marca la casilla **Repetir etiquetas de elementos**.
3. **Comprobar la Inclusión de Elementos Visuales:**
   * Asegúrate de que el Gráfico Dinámico y el Segmentador de Municipio estén ubicados dentro del rango fijado como Área de Impresión para que aparezcan reflejados en el documento impreso o exportado a PDF.

---

### 📍 BLOQUE 4: Ajuste de Escala, Márgenes y Encabezado/Pie de Página

1. **Ajuste de Escala (Evitar Columnas Cortadas):**
   * En **Diseño de página > Configurar página**:
     * Orientación: **Horizontal** (adecuada para tablas con múltiples columnas de valores).
     * Ajuste de escala: Selecciona **Ajustar a 1 página de ancho** (deja la casilla de alto en blanco o en automático para permitir el crecimiento vertical).
2. **Encabezado y Pie de Página Institucional:**
   * En **Diseño de página > Configurar página > Encabezado y pie de página**:
     * **Encabezado personalizado:** En la sección central, escribe `"Principado de Asturias — Red Autonómica de Cuevas"`.
     * **Pie de página personalizado:** 
       * Sección izquierda: `"Módulo 2: Excel Avanzado — MENTIONA"`.
       * Sección derecha: Inserta el campo de número de página con formato `"Página &[Página] de &[Páginas]"`.
3. **Verificación en Vista Previa de Impresión:**
   * Pulsa **`Ctrl + P`** (o `Ctrl + F2`) para abrir la Vista previa de impresión.
   * Navega entre las páginas para verificar que los títulos de encabezado se repiten en cada hoja, que las celdas se dividen limpiamente por cueva y que no hay columnas huérfanas cortadas.

---

### 📍 BLOQUE 5: Optimización para la Visualización Interactiva en Pantalla

1. **Inmovilización de Paneles:**
   * Para consultar el informe en pantalla sin perder de vista los encabezados al hacer *scroll*:
   * Sitúate en la celda situada justo debajo de la fila de encabezados y a la derecha de la columna de celdas fijas.
   * Ve a **Vista > Inmovilizar > Inmovilizar paneles**.
2. **Conmutación de Vistas del Libro:**
   * Experimenta con las tres vistas disponibles en **Vista > Vistas del libro** (o desde la barra de estado inferior):
     * **Vista Normal:** Entorno de trabajo predeterminado para edición de datos.
     * **Diseño de página:** Muestra la hoja dividida como folios reales con reglas superior/lateral y margen visible para encabezados.
     * **Vista previa de salto de página:** Muestra las líneas de trazo azul ajustables manualmente para definir dónde corta Excel cada página.
3. **Preparar el Lienzo para Presentación Ejecutiva:**
   * Haz clic en el Gráfico Dinámico, ve a **Analizar gráfico dinámico > Botones de campo** y selecciona **Ocultar todo** para presentar una gráfica limpia.
   * Desactiva la visión del panel lateral haciendo clic en **Analizar tabla dinámica > Lista de campos** para ocultarlo.
   * Organiza el Segmentador de Municipio en la parte superior como control deslizante horizontal y ajusta el **Zoom** (`Ctrl + Rueda del ratón`) para encuadrar todo el cuadro de mando en la pantalla.

---

## 🔍 4. Solucionario y Check de Verificación Docente

| Paso / Aspecto | Configuración Correcta en Excel | Resultado Esperado |
| :--- | :--- | :--- |
| **Área de Impresión** | `Diseño de página > Área de impresión` | Cubre exactamente la TD, el gráfico y el segmentador sin celdas sobrantes. |
| **Títulos de Impresión** | `Diseño de página > Imprimir títulos > Repetir filas` | Las filas de encabezado `$3:$4` reaparecen en la parte superior de cada página impresa. |
| **Salto por Cueva** | `Configuración de campo (Cueva) > Insertar salto de página` | Cada cueva comienza en una hoja impresa independiente. |
| **Escala** | `Ajustar a 1 página de ancho` | Ninguna columna de ingresos o visitantes queda cortada en hojas sueltas a la derecha. |
| **Visualización** | `Vista > Inmovilizar paneles` | La fila de títulos de la tabla permanece fija en pantalla al desplazarse hacia abajo. |

---

## 🛠️ 5. Tabla de Diagnóstico de Errores Frecuentes (Epígrafe 2.6)

| Error Frecuente | Por qué se produce | Cómo evitarlo o corregirlo |
| :--- | :--- | :--- |
| **El botón *Imprimir títulos* aparece en gris (atenuado)** | Ocurre porque se está editando una celda (modo edición activo), hay un gráfico seleccionado o hay varias hojas del libro seleccionadas simultáneamente. | Sal del modo edición (pulsa `Esc`), haz clic en una celda vacía de la hoja y asegúrate de tener seleccionada una sola pestaña. |
| **Columnas cortadas en páginas sobrantes a la derecha** | El ancho total de la Tabla Dinámica supera el margen del papel en orientación vertical. | Cambia la orientación a **Horizontal** y ajusta la escala a **"Ajustar a 1 página de ancho"**. |
| **Páginas en blanco o vacías al imprimir** | El Área de Impresión establecida incluye filas o columnas vacías que contienen formatos invisibles o espacios en blanco. | Ve a `Diseño de página > Área de impresión > Borrar área de impresión` y vuelve a seleccionar únicamente el rango con contenido. |
| **Los títulos de encabezado no se repiten** | Se seleccionaron múltiples hojas a la vez antes de entrar en Configurar página, o la casilla de filas a repetir se dejó en blanco. | Haz clic derecho en la pestaña de la hoja, selecciona *Desagrupar hojas* y reconfigura los Títulos de Impresión. |
| **El informe impreso muestra datos desfasados** | Se envió a imprimir la Tabla Dinámica sin haber incorporado los últimos cambios realizados en la base de datos `Tbl_Cuevas`. | Haz clic derecho en la Tabla Dinámica y pulsa **Actualizar** (o atajo `Alt + F5`) antes de abrir la Vista Previa (`Ctrl + P`). |

---

## 📝 6. Cuestionario de Autoevaluación (Epígrafe 2.6)

### Preguntas Tipo Test
1. ¿Qué combinación de teclas abre directamente la Vista previa de impresión en Excel?
   * a) `Ctrl + Shift + P`
   * b) `Ctrl + P` (o `Ctrl + F2`)
   * c) `Alt + F5`
   * d) `Ctrl + T`
2. ¿Desde dónde se configura la repetición automática de los encabezados de fila de una Tabla Dinámica en cada página impresa?
   * a) Menú *Inicio > Formato condicional*.
   * b) Pestaña *Diseño de página > Imprimir títulos > Repetir filas en la parte superior*.
   * c) Pestaña *Insertar > Tabla dinámica*.
   * d) Pestaña *Datos > Filtro*.
3. ¿Cómo se puede lograr que cada elemento de un campo de fila (ej. cada Cueva) se imprima en una hoja separada de forma automática?
   * a) Insertando saltos de línea manuales con `Alt + Intro`.
   * b) Desde la opción *Configuración de campo* del área de Filas, marcando "Insertar salto de página después de cada elemento".
   * c) Dividiendo la base de datos en 10 libros independientes.
   * d) Ocultando manualmente las filas antes de imprimir.

### Preguntas de Desarrollo
1. Explica la diferencia entre utilizar la **Vista Normal**, la **Vista de Diseño de página** y la **Vista previa de salto de página** en el proceso de maquetación de un informe dinámico.
2. ¿Por qué es recomendable ocultar los "Botones de campo" de un Gráfico Dinámico al preparar un cuadro de mando para su presentación en pantalla ante la dirección?

---

### Solucionario del Cuestionario
* **Test:** 1 -> **b** | 2 -> **b** | 3 -> **b**
* **Desarrollo 1:** La *Vista Normal* es el lienzo de trabajo y edición sin límites de papel; la *Vista Diseño de página* muestra la hoja dividida en folios reales con sus márgenes, reglas y encabezados editables; la *Vista previa de salto de página* muestra las líneas azules ajustables que definen dónde corta Excel las páginas impresas.
* **Desarrollo 2:** Ocultar los botones de campo elimina el "ruido visual" y los elementos grises de interfaz, ofreciendo una apariencia gráfica corporativa más limpia, profesional y fácil de interpretar en pantalla.

