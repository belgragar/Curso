# EJERCICIOS 06: HERRAMIENTAS DE TABLAS DINÁMICAS
## Práctica Guiada (Bloque 2)

### Datos de partida (Bloque 2)

Utiliza la misma tabla estructurada `Tbl_Ventas` creada en el bloque anterior.

### Pasos guiados

1. **Crear vistas paralelas:**
* En una hoja nueva llamada `Dashboard_Ventas`, crea **dos Tablas Dinámicas independientes** asociadas a `Tbl_Ventas`:
* **Tabla Dinámica A:** `FILAS:` Vendedor | `VALORES:` Suma de Importe.

* **Tabla Dinámica B:** `FILAS:` Categoría | `VALORES:` Promedio de Importe.

2. **Insertar Controles Visuales:**
* Selecciona la Tabla A y ve a *Analizar tabla dinámica > Insertar segmentación de datos*. Elige el campo `Región`.

* Ve a *Analizar tabla dinámica > Insertar escala de tiempo*. Elige el campo `Fecha`.

3. **Personalizar la apariencia de los Slicers:**
* Haz clic en el segmentador `Región`. Ve a la pestaña **Segmentación** de la cinta superior.
* Cambia el número de **Columnas a 4** para que los botones se muestren en una fila horizontal.

4. **Establecer Conexiones de Informes:**
* Haz clic derecho sobre el segmentador `Región` > **Conexiones de informes**.

* Activa la casilla correspondiente a la **Tabla Dinámica B**.

* Haz clic derecho sobre la Línea de Tiempo > **Conexiones de informes** y conéctala también a la **Tabla Dinámica B**.

5. **Prueba de interactividad:**
* Selecciona "Norte" en el segmentador y un trimestre específico en la línea de tiempo. Verifica cómo ambas tablas dinámicas se filtran e interactúan al instante.

---

## B2.3. Ejercicios autónomos progresivos (Bloque 2)

### 🟢 Nivel Básico B2 — Filtrado Visual Individual

1. Crea una Tabla Dinámica con **FILAS:** `Producto` y **VALORES:** `Suma de Importe`.
2. Inserta un segmentador de datos para `Categoría`.
3. Configura el segmentador para que se muestre en **2 columnas**.
4. Filtra por la categoría "Periféricos" y verifica la actualización inmediata del informe.

---

### 🟡 Nivel Intermedio B2 — Sincronización de Filtros Cruzados

1. Crea dos Tablas Dinámicas en la misma hoja a partir de `Tbl_Ventas`:
* **Tabla 1:** `FILAS:` Región | `VALORES:` Suma de Importe.
* **Tabla 2:** `FILAS:` Vendedor | `VALORES:` Promedio de Importe.


2. Inserta un Segmentador para `Categoría` y una Línea de Tiempo para `Fecha`.
3. Sincroniza ambos controles mediante **Conexiones de informes** para que controlen las dos tablas a la vez.


4. Filtra el periodo "Febrero 2026" y la categoría "Informática".

*Pregunta de reflexión:* ¿Por qué un segmentador resulta más adecuado que un filtro tradicional cuando el informe va a ser utilizado por una persona que no ha creado la Tabla Dinámica?

---

### 🟠 Nivel Avanzado B2 — Gestión de Elementos sin Datos

1. En el segmentador de `Categoría` creado anteriormente, haz clic derecho > **Configuración de segmentación de datos**.

2. Explora las opciones del bloque Ordenación y filtrado de elementos, donde por defecto está activa la opción de *Ocultar los elementos que no contienen datos*.

3. Observa cómo, gracias a esta configuración predeterminada, al aplicar filtros cruzados con la *Línea de Tiempo*, las categorías sin ventas en ese periodo desaparecen automáticamente de la interfaz visual en lugar de quedarse bloqueadas o en gris.

---

### 🔴 Nivel Experto B2 — Cuadro de Mando Multidimensional con Slicers Cruzados

La dirección comercial necesita un informe que permita analizar rápidamente la evolución de las ventas sin modificar manualmente la Tabla Dinámica.

El informe debe permitir:

- Consultar la facturación total por región.
- Consultar el promedio de venta por vendedor.
- Consultar el porcentaje de participación de cada categoría.
- Filtrar visualmente por Vendedor.
- Filtrar visualmente por Región.
- Filtrar visualmente por Categoría.
- Seleccionar periodos mediante una línea de tiempo.
- Mostrar los importes en euros y los porcentajes con formato adecuado.
- Colocar los controles de filtrado de forma ordenada y profesional.

Para ello, entre otras cosas:

1. A partir de `Tbl_Ventas`, crea una Tabla Dinámica avanzada con la siguiente estructura analítica compleja:
   * **FILAS:** `Región` y, debajo, `Vendedor` (anidados jerárquicamente).
   * **COLUMNAS:** `Categoría`.
   * **VALORES:**
     * `Suma de Importe` (Renombrada como "Ventas").
     * `Promedio de Importe` (Renombrada como "Media por Opción").

2. Modifica el diseño del informe a **Formato Tabular** y activa **Repetir todas las etiquetas de elementos**.
3. Inserta **tres Segmentadores de datos independientes**: uno para el campo `Categoría`, otro para el campo `Vendedor` y otro para el campo `Región`.
4. Personaliza el segmentador de `Categoría` para que se muestre en **3 columnas** en formato horizontal, el de `Vendedor` en **2 columnas** y el de `Región` colócalo en formato vertical limpio.
5. Inserta una **línea de tiempo** uno para el campo `Fecha`.
6. Aplica un **Estilo de Tabla Dinámica** corporativo (medio u oscuro) y comprueba cómo la combinación simultánea de los segmentadores filtra dinámicamente la matriz bidimensional de filas y columnas.

**Comprobación final**:

Realiza varias combinaciones de filtros y verifica que todos los informes responden correctamente.

*Preguntas de reflexión:*

* Qué configuración has utilizado.
* Qué indicadores consideras más útiles para la dirección.
* Qué combinación de filtros permite detectar el periodo de mayor actividad comercial.

---



* **Documentación oficial:** Consulta las guías de soporte de Microsoft sobre [creación y diseño de tablas dinámicas](https://support.microsoft.com/es-ES/Excel/get-started/create-a-pivottable-to-analyze-worksheet-data).
* **Herramientas recomendadas:** Microsoft Excel 365 o versiones recientes de escritorio.
* **Recursos para ampliar:** Vídeos técnicos especializados en análisis de datos y cuadros de mando interactivos en canales formativos oficiales.
