# 🏔️ PROYECTO INTEGRADOR: GESTIÓN INTEGRAL DE LA RED DE ALBERGUES DEL CAMINO DE SANTIAGO EN ASTURIAS

## 📌 PRESENTACIÓN DEL PROYECTO Y CONTEXTO DE NEGOCIO

La **Fundación Jacobea del Principado de Asturias** gestiona la Red Pública de Albergues, Puntos de Acogida y Servicios de Atención al Peregrino a lo largo de las dos grandes rutas jacobeas asturianas:

1. **El Camino Primitivo:** *Oviedo → Grado → Salas → Tineo → Pola de Allande → Grandas de Salime*.
2. **El Camino del Norte (Costa):** *Llanes → Ribadesella → Villaviciosa → Gijón / Avilés → Luarca → Castropol*.

Para modernizar la gestión operativa, auditar la afluencia, simular presupuestos de conservación y automatizar los partes diarios de recepción, la Fundación ha encomendado la construcción del libro de trabajo maestro **`Camino_Santiago_Asturias_Gestion.xlsm`**.

---

## 📋 DATOS DE EJEMPLO PARA EL PROYECTO (FORMATO TSV PARA PEGAR DIRECTAMENTE EN EXCEL)

> 💡 **Instrucciones de copia:** Selecciona todo el contenido dentro del bloque de código TSV a continuación, cópialo (`Ctrl + C`) y pégalo directamente en la celda `A1` de una hoja vacía de Excel (`Ctrl + V`). Excel separará automáticamente el texto en columnas. A continuación, selecciona los datos y pulsa `Ctrl + T` para convertir el rango en la tabla estructurada `Tbl_RegistroPeregrinos`.

### 1. Tabla Principal: `Tbl_RegistroPeregrinos` (50 registros)

```tsv
ID_Registro	Fecha	Ruta	Etapa	Albergue	Concejo	Pais_Origen	Pernoctaciones	Aportacion_EUR
REG-001	01/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	España	1	5,00
REG-002	01/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	Francia	2	10,00
REG-003	02/05/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	Alemania	1	7,50
REG-004	02/05/2026	Camino del Norte	Etapa 1	La Casona del Peregrino	Llanes	Italia	1	5,00
REG-005	03/05/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	España	3	15,00
REG-006	03/05/2026	Camino Primitivo	Etapa 3	Albergue de Salas	Salas	Portugal	1	6,00
REG-007	04/05/2026	Camino Primitivo	Etapa 4	Palacio de Meras	Tineo	Países Bajos	2	12,00
REG-008	04/05/2026	Camino del Norte	Etapa 3	Albergue de Villaviciosa	Villaviciosa	Reino Unido	1	8,00
REG-009	05/05/2026	Camino del Norte	Etapa 4	Albergue de Gijón	Gijón	Estados Unidos	1	10,00
REG-010	05/05/2026	Camino Primitivo	Etapa 5	Albergue de Pola de Allande	Allande	Bélgica	2	10,00
REG-011	06/05/2026	Camino Primitivo	Etapa 6	Albergue de Grandas de Salime	Grandas de Salime	Francia	1	5,00
REG-012	06/05/2026	Camino del Norte	Etapa 5	Albergue de Avilés	Avilés	España	2	12,00
REG-013	07/05/2026	Camino del Norte	Etapa 6	Albergue de Luarca	Valdés	Alemania	1	7,00
REG-014	07/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	Polonia	1	5,00
REG-015	08/05/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	España	2	10,00
REG-016	08/05/2026	Camino del Norte	Etapa 7	Albergue de Castropol	Castropol	Canadá	1	8,50
REG-017	09/05/2026	Camino Primitivo	Etapa 3	Albergue de Salas	Salas	Francia	1	6,00
REG-018	09/05/2026	Camino del Norte	Etapa 1	La Casona del Peregrino	Llanes	España	2	10,00
REG-019	10/05/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	Italia	1	5,00
REG-020	10/05/2026	Camino Primitivo	Etapa 4	Palacio de Meras	Tineo	Alemania	3	18,00
REG-021	11/05/2026	Camino Primitivo	Etapa 5	Albergue de Pola de Allande	Allande	Corea del Sur	1	10,00
REG-022	11/05/2026	Camino del Norte	Etapa 3	Albergue de Villaviciosa	Villaviciosa	Francia	2	12,00
REG-023	12/05/2026	Camino del Norte	Etapa 4	Albergue de Gijón	Gijón	España	1	5,00
REG-024	12/05/2026	Camino Primitivo	Etapa 6	Albergue de Grandas de Salime	Grandas de Salime	Australia	2	15,00
REG-025	13/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	Suiza	1	8,00
REG-026	01/06/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	Alemania	2	12,00
REG-027	02/06/2026	Camino del Norte	Etapa 5	Albergue de Avilés	Avilés	España	1	5,00
REG-028	03/06/2026	Camino del Norte	Etapa 6	Albergue de Luarca	Valdés	Francia	2	10,00
REG-029	04/06/2026	Camino Primitivo	Etapa 3	Albergue de Salas	Salas	Italia	1	6,00
REG-030	05/06/2026	Camino Primitivo	Etapa 4	Albergue de Tineo	Tineo	España	2	10,00
REG-031	06/06/2026	Camino del Norte	Etapa 7	Albergue de Castropol	Castropol	Países Bajos	1	7,50
REG-032	07/06/2026	Camino Primitivo	Etapa 5	Albergue de Pola de Allande	Allande	Estados Unidos	1	10,00
REG-033	08/06/2026	Camino del Norte	Etapa 1	Albergue de Llanes	Llanes	Reino Unido	3	15,00
REG-034	09/06/2026	Camino Primitivo	Etapa 6	Albergue de Grandas de Salime	Grandas de Salime	España	1	5,00
REG-035	10/06/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	Bélgica	2	12,00
REG-036	01/07/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	Francia	1	6,00
REG-037	02/07/2026	Camino del Norte	Etapa 3	Albergue de Villaviciosa	Villaviciosa	España	2	10,00
REG-038	03/07/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	Alemania	1	5,00
REG-039	04/07/2026	Camino del Norte	Etapa 4	Albergue de Gijón	Gijón	Corea del Sur	2	14,00
REG-040	05/07/2026	Camino Primitivo	Etapa 3	Albergue de Salas	Salas	España	1	5,00
REG-041	06/07/2026	Camino Primitivo	Etapa 4	Albergue de Tineo	Tineo	Polonia	2	10,00
REG-042	07/07/2026	Camino del Norte	Etapa 5	Albergue de Avilés	Avilés	Italia	1	6,00
REG-043	08/07/2026	Camino Primitivo	Etapa 5	Albergue de Pola de Allande	Allande	España	3	15,00
REG-044	09/07/2026	Camino del Norte	Etapa 6	Albergue de Luarca	Valdés	Suiza	1	8,00
REG-045	10/07/2026	Camino Primitivo	Etapa 6	Albergue de Grandas de Salime	Grandas de Salime	Alemania	2	12,00
REG-046	11/07/2026	Camino del Norte	Etapa 7	Albergue de Castropol	Castropol	Francia	1	5,00
REG-047	12/07/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	España	2	10,00
REG-048	13/07/2026	Camino del Norte	Etapa 1	Albergue de Llanes	Llanes	Canadá	1	7,00
REG-049	14/07/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	Portugal	1	5,00
REG-050	15/07/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	España	2	10,00
```

---

### 2. Tabla Auxiliar: `Tbl_Albergues` (12 registros)

> 💡 **Instrucciones de copia para el alumnado:** Pega el siguiente bloque en otra hoja y nómbralo como la tabla estructurada `Tbl_Albergues`.

```tsv
ID_Albergue	Nombre_Albergue	Ruta	Concejo	Plazas	Telefono
ALB-01	Albergue de Oviedo	Camino Primitivo	Oviedo	35	985111222
ALB-02	Albergue de Grado	Camino Primitivo	Grado	20	985222333
ALB-03	Albergue de Salas	Camino Primitivo	Salas	28	985333444
ALB-04	Albergue de Tineo	Camino Primitivo	Tineo	25	985444555
ALB-05	Albergue de Pola de Allande	Camino Primitivo	Allande	18	985555666
ALB-06	Albergue de Grandas de Salime	Camino Primitivo	Grandas de Salime	22	985666777
ALB-07	Albergue de Llanes	Camino del Norte	Llanes	40	985777888
ALB-08	Albergue de Ribadesella	Camino del Norte	Ribadesella	30	985888999
ALB-09	Albergue de Villaviciosa	Camino del Norte	Villaviciosa	24	985999000
ALB-10	Albergue de Gijón	Camino del Norte	Gijón	50	985000111
ALB-11	Palacio de Meras	Camino Primitivo	Tineo	45	985001011
ALB-12	La Casona del Peregrino	Camino del Norte	Llanes	42	985014211
```

---

## 🗺️ ESTRUCTURA DEL PROYECTO POR FASES Y EPÍGRAFES DEL MANUAL

---

### 🔹 FASE 1: CREACIÓN Y CONFIGURACIÓN BASE DE TABLAS DINÁMICAS

* **Epígrafe del Manual:** **`2.1 Creación y modificación de tablas dinámicas`**
* **Contexto Jacobeo:** Análisis de la base de datos transaccional de registro de pernoctaciones de la red de albergues asturianos (`Tbl_RegistroPeregrinos`).

#### 📝 Tareas a desarrollar:

1. **Origen de datos limpio:** Partir de la tabla estructurada `Tbl_RegistroPeregrinos`.
2. **Inserción de la Tabla Dinámica:** Crear una primera Tabla Dinámica en una hoja nueva denominada `TD_Afluencia_Concejos`.
3. **Estructuración:**
   * Disponer el campo *Concejo* en **FILAS**.
   * Disponer el campo *Albergue* anidado justo debajo de *Concejo*.
   * Disponer el campo *Pernoctaciones* en **VALORES** (Suma).
   * Disponer el campo *Ruta* en **FILTROS** (Camino Primitivo / Camino del Norte).
4. **Mantenimiento y actualización:** Simular la incorporación de nuevos registros de peregrinos en la celda final de la tabla de origen y verificar la actualización mediante *Analizar tabla dinámica > Actualizar*.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 1)

1. Seleccionar cualquier celda dentro de la tabla `Tbl_RegistroPeregrinos`.
2. Ir a la cinta de opciones **Insertar** > **Tabla dinámica**.
3. Seleccionar *Nueva hoja de cálculo* y renombrar la pestaña creada como `TD_Afluencia_Concejos`.
4. En el panel lateral *Campos de la tabla dinámica*:
   * Arrastrar **Concejo** a la sección **FILAS**.
   * Arrastrar **Albergue** a **FILAS** (posicionándolo justo debajo de Concejo).
   * Arrastrar **Pernoctaciones** a **VALORES** (se configurará como `Suma de Pernoctaciones`).
   * Arrastrar **Ruta** a la sección **FILTROS**.
5. Para comprobar la actualización dinámica, añadir una fila al final de `Tbl_RegistroPeregrinos`, volver a `TD_Afluencia_Concejos`, ir a la pestaña **Analizar tabla dinámica** y hacer clic en **Actualizar**.

---

### 🔹 FASE 2: CONFIGURACIÓN DE CAMPOS DE VALOR Y MÉTRICAS DE CUOTA

* **Epígrafe del Manual:** **`2.2 Configuración de los campos de valor`**
* **Contexto Jacobeo:** Evaluación de la contribución económica media y distribución por país de procedencia de los caminantes.

#### 📝 Tareas a desarrollar:

1. **Múltiples métricas sobre un mismo campo:** En la hoja `TD_Analisis_Economico`, insertar una Tabla Dinámica con el campo *Pais_Origen* en **FILAS** y añadir el campo *Aportacion_EUR* **tres veces** en el área de **VALORES**.
2. **Configuración de funciones de resumen:**
   * **Campo 1:** Renombrar a "Aportación Total" (Función *Suma*).
   * **Campo 2:** Renombrar a "Aportación Media por Peregrino" (Función *Promedio*).
   * **Campo 3:** Renombrar a "% Cuota de Aportación" (Configurar en *Mostrar valores como* -> **% del total general**).
3. **Formato persistente de campo:** Aplicar formato de moneda `Moneda (€)` a los dos primeros campos y `Porcentaje (0,0%)` al tercero directamente desde *Configuración de campo de valor > Formato de número*.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 2)

1. Crear una nueva tabla dinámica en la hoja `TD_Analisis_Economico` desde `Tbl_RegistroPeregrinos`.
2. Arrastrar el campo **Pais_Origen** a **FILAS**.
3. Arrastrar el campo **Aportacion_EUR** tres veces consecutivas a **VALORES**.
4. **Primer campo:** Hacer clic en la flecha de *Suma de Aportacion_EUR* > **Configuración de campo de valor...** > Cambiar el nombre personalizado a `Aportación Total`. Hacer clic en el botón **Formato de número**, elegir **Moneda** (Símbolo: `€`, 2 decimales) y pulsar Aceptar.
5. **Segundo campo:** Entrar en su configuración, seleccionar **Promedio**, renombrar como `Aportación Media por Peregrino` y aplicar el formato de número **Moneda** (`€`).
6. **Tercer campo:** Entrar en su configuración, ir a la pestaña **Mostrar valores como**, seleccionar **% del total general**, renombrar como `% Cuota de Aportación` y pulsar en **Formato de número** para aplicar **Porcentaje** (1 decimal).

---

### 🔹 FASE 3: GESTIÓN INTERACTIVA DE DATOS, AGRUPACIONES Y EXTRACCIÓN

* **Epígrafe del Manual:** **`2.3 Gestión de datos en tablas dinámicas`**
* **Contexto Jacobeo:** Estacionalidad de las pernoctaciones y control de aportaciones por intervalos.

#### 📝 Tareas a desarrollar (Detalle de Tablas Dinámicas y Agrupaciones):

Para completar esta fase, se deben construir **dos Tablas Dinámicas independientes** en la hoja `TD_Estacionalidad`:

1. **Tabla Dinámica 1 (`TD_Estacionalidad_Fechas` - Estacionalidad Temporal):**
   * **Origen:** `Tbl_RegistroPeregrinos`
   * **Configuración de Campos:**
     * Área **FILAS**: Arrastrar el campo `Fecha`. Una vez colocado, hacer clic derecho sobre cualquier fecha de la tabla, seleccionar **Agrupar...** y marcar **Meses** y **Trimestres** (desmarcando Años o Días si procede) para estructurar la afluencia temporalmente.
     * Área **VALORES**: Arrastrar `Pernoctaciones` (configurado como *Suma*).
     * Área **FILTROS**: Arrastrar `Ruta`.
2. **Tabla Dinámica 2 (`TD_Donaciones_Intervalos` - Análisis de Aportaciones):**
   * **Origen:** `Tbl_RegistroPeregrinos`
   * **Configuración de Campos:**
     * Área **FILAS**: Arrastrar el campo `Aportacion_EUR`. Una vez situado, hacer clic derecho sobre los valores numéricos de la tabla, seleccionar **Agrupar...** e indicar los parámetros de intervalos (*Comenzar en*: `0`, *Terminar en*: `20`, *Por*: `5`) para crear los tramos de donación.
     * Área **VALORES**: Arrastrar `ID_Registro` (configurado automáticamente como *Cuenta* o *Recuento*) para cuantificar cuántos peregrinos aportan en cada tramo.
3. **Controles visuales de filtrado y extracción directa con fórmulas:**
   * Insertar una **Segmentación de Datos (Slicer)** para el campo *Ruta* y una **Escala de Tiempo (Timeline)** sobre el campo *Fecha*, conectándolas a ambas tablas mediante *Conexiones de informe*.
   * **Extracción de datos sin crear tablas dinámicas nuevas:** En un cuadro resumen exterior (por ejemplo, en la parte derecha de la hoja), extraer el total de pernoctaciones de un albergue específico utilizando la función `=IMPORTARDATOSDINAMICOS()`. No se crea una tabla dinámica nueva para esto; la función apunta directamente a un dato presente en la primera tabla dinámica realizada en la Fase 1 (`TD_Afluencia_Concejos`).

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 3)

1. **Construir TD 1 (Estacionalidad):** Insertar la tabla dinámica en `TD_Estacionalidad`, colocar `Fecha` en **FILAS** y `Pernoctaciones` en **VALORES**. Clic derecho en las fechas > **Agrupar...** > Seleccionar **Meses** y **Trimestres**.
2. **Construir TD 2 (Intervalos de aportación):** Colocar debajo o en un lateral otra tabla dinámica con `Aportacion_EUR` en **FILAS** y `ID_Registro` en **VALORES**. Clic derecho en los importes > **Agrupar...** > Definir inicio `0`, fin `20` e intervalo `5`.
3. **Slicers y Conexiones:** Seleccionar cualquier tabla dinámica > **Analizar tabla dinámica** > **Insertar segmentación de datos** (`Ruta`). Clic derecho en la segmentación > **Conexiones de informe** y marcar ambas tablas dinámicas.
4. **Extracción con `IMPORTARDATOSDINAMICOS` (Aclaración de no crear tabla nueva):**
   * Ir a la celda del cuadro de mando exterior donde se quiera mostrar el dato aislado.
   * Escribir `=` y hacer clic directamente sobre la celda que contiene el total del *Albergue de Salas* dentro de la Tabla Dinámica de la Fase 1 (`TD_Afluencia_Concejos`).
   * Excel insertará automáticamente la fórmula:
     ```excel
     =IMPORTARDATOSDINAMICOS("Pernoctaciones"; TD_Afluencia_Concejos!$A$3; "Albergue"; "Albergue de Salas")
     ```
   * Esto permite extraer ese indicador clave (KPI) para un panel ejecutivo sin necesidad de rehacer o crear otra tabla dinámica.

---

### 🔹 FASE 4: GENERACIÓN DE LISTADOS DINÁMICOS CON MATRICES DESBORDADAS Y NUEVAS FUNCIONES DE M365 (`ELEGIRCOLS`, `APILARH`)

* **Epígrafe del Manual:** **`2.4 Listados Dinámicos`**
* **Contexto Jacobeo:** Automatización del directorio activo de albergues, construcción de informes ejecutivos compuestos con matrices dinámicas y consultas dinámicas.

#### 📝 Tareas a desarrollar:

1. **Matriz derramada de albergues destacados:** En la hoja `Listados_Activos`, construir una fórmula en una sola celda utilizando las funciones de matriz dinámica:
   ```excel
   =ORDENAR(FILTRAR(Tbl_Albergues[Nombre_Albergue]; (Tbl_Albergues[Ruta]="Camino Primitivo") * (Tbl_Albergues[Plazas]>20); "Sin resultados"); 1; 1)
   ```
2. **Selección de columnas específicas con `ELEGIRCOLS`:** Generar un reporte simplificado extrayendo columnas directas de la tabla mediante referencia de columna limpia:
   ```excel
   =ELEGIRCOLS(Tbl_Albergues; 2; 6)
   ```
3. **Consolidación horizontal con `APILARH`:** Unir de forma directa las columnas de nombre y teléfono empleando directamente las referencias de columnas de la tabla estructurada sin anidaciones complejas:
   ```excel
   =APILARH(Tbl_Albergues[Nombre_Albergue]; Tbl_Albergues[Telefono])
   ```
4. **Listado de países sin duplicados y validación interactiva:** Generar una columna derramada con `=ORDENAR(UNICOS(Tbl_RegistroPeregrinos[Pais_Origen]))` y vincularla a una lista desplegable mediante el operador de desbordamiento (`#`).

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 4)

1. Ir a la hoja `Listados_Activos`.
2. En la celda `A3`, escribir la fórmula de filtrado y ordenación:
   `=ORDENAR(FILTRAR(Tbl_Albergues[Nombre_Albergue]; (Tbl_Albergues[Ruta]="Camino Primitivo") * (Tbl_Albergues[Plazas]>20); "Sin resultados"); 1; 1)`
3. En la celda `D3`, aplicar **`ELEGIRCOLS`** referenciando la tabla completa y las columnas deseadas (ej. columna 2 y 6):
   `=ELEGIRCOLS(Tbl_Albergues; 2; 6)`
4. En la celda `G3`, utilizar **`APILARH`** uniendo de forma limpia las columnas directas de la tabla:
   `=APILARH(Tbl_Albergues[Nombre_Albergue]; Tbl_Albergues[Telefono])`
5. En la celda `H2`, escribir `=ORDENAR(UNICOS(Tbl_RegistroPeregrinos[Pais_Origen]))`.
6. Crear una validación de datos de tipo *Lista* en `B3` apuntando al origen con desbordamiento: `=H2#`.

---

### 🔹 FASE 5: DASHBOARD VISUAL CON GRÁFICOS DINÁMICOS VARIADOS

* **Epígrafe del Manual:** **`2.5 Gráficos Dinámicos`**
* **Contexto Jacobeo:** Panel ejecutivo visual con múltiples perspectivas gráficas conectadas a segmentaciones.

#### 📝 Tareas a desarrollar:

1. **Creación de Gráficos Dinámicos Múltiples:** Para practicar distintos tipos de representación visual, se exige construir y poblar gráficos basados en las diferentes tablas dinámicas trabajadas en fases anteriores:
   * **Gráfico 1 (Columnas Agrupadas):** Vinculado a la tabla de afluencia por albergue de la Fase 1 (`TD_Afluencia_Concejos`).
   * **Gráfico 2 (Líneas con Marcadores):** Vinculado a la tabla de estacionalidad mensual y trimestral de la Fase 3 (`TD_Estacionalidad`).
   * **Gráfico 3 (Gráfico Circular o de Anillos):** Vinculado a la tabla de análisis económico por país de origen de la Fase 2 (`TD_Analisis_Economico`).
2. **Personalización UX/UI:**
   * Ocultar todos los botones de campo del gráfico para una estética limpia.
   * Conectar los gráficos a la segmentación de datos general (`Ruta`) para que interactúen de forma sincronizada.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 5)

1. Posicionarse en la tabla dinámica de la Fase 1 (`TD_Afluencia_Concejos`), ir a **Analizar tabla dinámica** > **Gráfico dinámico** y seleccionar el tipo **Columnas agrupadas**.
2. Posicionarse en la tabla dinámica de estacionalidad de la Fase 3, insertar un gráfico dinámico de tipo **Líneas**.
3. Posicionarse en la tabla dinámica de análisis económico de la Fase 2, insertar un gráfico dinámico de tipo **Circular** o **Anillos**.
4. Hacer clic derecho sobre los botones de campo integrados en cada gráfico y seleccionar **Ocultar todos los botones de campos de gráfico**.
5. Asegurar que las segmentaciones de datos de ruta controlen los tres gráficos mediante la opción *Conexiones de informe*.

---

### 🔹 FASE 6: PREPARACIÓN DE INFORMES PARA IMPRESIÓN Y EXPORTACIÓN EXECUTIVE

* **Epígrafe del Manual:** **`2.6 Impresión y visualización de contenidos dinámicos`**
* **Contexto Jacobeo:** Presentación oficial de memoria anual ante la Consejería de Cultura y Turismo del Principado de Asturias.

#### 📝 Tareas a desarrollar:

1. **Configuración de página e impresión:**
   * Definir el **Área de Impresión** en la hoja de informe mensual evitando zonas vacías.
   * Configurar **Títulos de Impresión** (`Diseño de página > Imprimir títulos`) para repetir las filas de encabezado en todas las páginas impresas.
2. **Visualización y diseño de informe:**
   * Inmovilizar los paneles superiores para mantener visibles las cabeceras durante el desplazamiento (*Vista > Inmovilizar paneles*).
   * Ajustar el diseño de las tablas dinámicas a **Formato Tabular** con la opción **Repetir todas las etiquetas de elementos** activada.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 6)

1. Seleccionar el rango del informe y pulsar en **Diseño de página** > **Área de impresión** > **Establecer área de impresión**.
2. En **Diseño de página** > **Imprimir títulos**, seleccionar la fila `$1:$1` en *Filas a repetir en extremo superior*.
3. Seleccionar la celda `A2` y hacer clic en **Vista** > **Inmovilizar paneles** > **Inmovilizar paneles**.
4. Configurar las tablas dinámicas en modo **Formato Tabular** desde la pestaña *Diseño* y activar **Repetir todas las etiquetas de elementos**.

---

### 🔹 FASE 7: MODELADO DE BÚSQUEDA, DEPURACIÓN DE TEXTOS, BASE DE DATOS Y FINANZAS

* **Epígrafe del Manual:** **`2.7 Funciones avanzadas: Búsqueda, Mates/Cadenas, Base de datos y Financieras`**
* **Contexto Jacobeo:** Auditoría técnica de datos, limpieza de registros de credenciales y cuadro de amortización de préstamos para reformas de albergues.

#### 📝 Tareas a desarrollar:

1. **Búsquedas avanzadas y limpieza de textos:**
   * Usar `BUSCARX` para consultar el teléfono y plazas de un albergue según su código: `=BUSCARX(B3; Tbl_Albergues[ID_Albergue]; Tbl_Albergues[Telefono]; "No hallado")`.
   * Corregir nombres de peregrinos con espacios superfluos usando `ESPACIOS()` y unirlos con `UNIRCADENAS()`.
2. **Funciones de Base de Datos y Financieras:**
   * Aplicar `BDSUMA` sobre un rango de criterios para filtrar donaciones de peregrinos alemanes o franceses.
   * Modelar el préstamo de reforma del albergue de Grandas de Salime (80.000 €, 5 años, 4,5% interés) empleando `PAGO`, `PAGOINT` y `PAGOPRIN`.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 7)

1. **Búsqueda:** Introducir `=BUSCARX(B3; Tbl_Albergues[ID_Albergue]; Tbl_Albergues[Telefono]; "No hallado")`.
2. **BDSUMA:** Diseñar un pequeño rango de criterios con los encabezados de la tabla y aplicar `=BDSUMA(Tbl_RegistroPeregrinos; "Aportacion_EUR"; RangoCriterios)`.
3. **Financieras:** Calcular la cuota mensual con `=PAGO(4,5%/12; 60; -80000)` y el desglose de intereses del primer mes con `=PAGOINT(4,5%/12; 1; 60; -80000)`.

---

### 🔹 FASE 8: DIGITALIZACIÓN DEL PARTE DE RECEPCIÓN MEDIANTE PLANTILLAS Y FORMULARIOS

* **Epígrafe del Manual:** **`2.8 Creación de plantillas y formularios`**
* **Contexto Jacobeo:** Estándar digital de entrada de peregrinos en el albergue de Pola de Allande.

#### 📝 Tareas a desarrollar:

1. **Diseño del Formulario y Controles:**
   * Insertar controles de formulario (Cuadro Combinado para nacionalidad, Botones de Opción para credencial, Casilla de verificación para equipaje y Control de número para pernoctaciones).
2. **Protección y Guardado como Plantilla:**
   * Desbloquear exclusivamente las celdas de entrada manual, proteger la hoja con contraseña y guardar el libro con extensión **Plantilla de Excel (`.xltx`)**.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 8)

1. Activar la ficha **Programador**, ir a **Insertar** y añadir los controles de formulario vinculándolos a celdas auxiliares de control.
2. Calcular la tarifa final mediante fórmulas lógicas (`=SI()`, `=ELEGIR()`).
3. Desproteger celdas de entrada en *Formato de celdas*, activar la protección de hoja desde la pestaña *Revisar* y guardar como **Plantilla de Excel (*.xltx)**.

---

### 🔹 FASE 9: ANÁLISIS DE HIPÓTESIS, SENSIBILIDAD Y SIMULACIÓN DE ESCENARIOS

* **Epígrafe del Manual:** **`2.9 Análisis de datos. Simulación de escenarios`**
* **Contexto Jacobeo:** Planificación económica de la red pública ante fluctuaciones turísticas e inflación de costes energéticos.

#### 📝 Tareas a desarrollar:

1. **Administrador de Escenarios:** Definir hipótesis (Conservador, Previsto, Optimista) y generar el informe resumen.
2. **Tabla de Datos de 2 Variables:** Cruzar niveles de aportación media y costes energéticos mensuales para evaluar el beneficio neto.
3. **Búsqueda de Objetivo:** Determinar el volumen exacto de peregrinos necesario en Tineo para alcanzar el punto de equilibrio (*breakeven*).

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 9)

1. Ir a **Datos** > **Análisis de hipótesis** > **Administrador de escenarios** para registrar los supuestos y generar el reporte resumen.
2. Construir la matriz de doble entrada y utilizar la herramienta **Tabla de datos** especificando las celdas de entrada de fila y columna.
3. Aplicar **Búsqueda de objetivo** sobre la celda de beneficio neto para despejar la celda cambiante de afluencia.

---

### 🔹 FASE 10: AUTOMATIZACIÓN DE TAREAS REPETITIVAS CON LA GRABADORA DE MACROS

* **Epígrafe del Manual:** **`2.10 Macros. Herramientas avanzadas`**
* **Contexto Jacobeo:** Automatización del proceso de cierre diario de caja y vaciado del formulario de registro.

> 📝 **Nota metodológica:** En esta fase se trabaja exclusivamente utilizando la interfaz visual de la **Grabadora de Macros** de Excel. Si se requiere algún ajuste o bloque de código en **VBA**, este se obtendrá pidiéndolo directamente a la Inteligencia Artificial como soporte didáctico de apoyo.

#### 📝 Tareas a desarrollar:

1. **Grabación de Macro Operativa:**
   * Iniciar la grabadora de macros desde la ficha *Programador* asignando un método abreviado (`Ctrl + Mayús + L`).
   * Realizar los pasos de limpieza de los campos de entrada del formulario y detener la grabación.
2. **Asistencia opcional de IA (VBA):** Consultar opcionalmente a la IA si se desea refinar el código generado por la grabadora añadiendo optimizaciones de pantalla (`Application.ScreenUpdating = False`) o mensajes emergentes (`MsgBox`).
3. **Asignación y Guardado:** Asociar la macro a un botón con forma corporativa en la hoja de recepción y guardar obligatoriamente el libro como **Libro habilitado para macros (`.xlsm`)**.

---

#### 🛠️ SOLUCIÓN PASO A PASO (FASE 10)

1. Ir a **Programador** > **Grabar macro**. Asignar el nombre `LimpiarFormulario` y el método abreviado `Ctrl + Mayús + L`.
2. Seleccionar las celdas de entrada del formulario, pulsar *Suprimir* y hacer clic en **Detener grabación**.
3. *(Opcional - Soporte IA)*: Si se solicita a la IA optimizar el código grabado, insertar el siguiente bloque en el Módulo de VBA (`Alt + F11`):
   ```vba
   Sub LimpiarFormulario()
       Application.ScreenUpdating = False
       Range("C4:C8").ClearContents
       Application.ScreenUpdating = True
       MsgBox "Formulario limpiado con éxito.", vbInformation, "Red de Albergues"
   End Sub
   ```
4. Insertar una forma en la hoja, hacer clic derecho > **Asignar macro** y seleccionar `LimpiarFormulario`.
5. Guardar el archivo como **Libro de Excel habilitado para macros (*.xlsm)**.

---

## 📊 MATRIZ DE SEGUIMIENTO Y EVALUACIÓN PEDAGÓGICA

| Fase | Epígrafe del Manual | Entregable Práctico en `Camino_Santiago_Asturias_Gestion.xlsm` |
| :---: | :--- | :--- |
| **1** | 2.1 Tablas Dinámicas Base | Hoja `TD_Afluencia_Concejos` con jerarquía Concejo > Albergue. |
| **2** | 2.2 Campos de Valor | Hoja `TD_Analisis_Economico` con Suma, Promedio y % de Cuota. |
| **3** | 2.3 Gestión e Interacción | Hoja `TD_Estacionalidad` con agrupación mensual/intervalos y Slicers. |
| **4** | 2.4 Listados Dinámicos | Hoja `Listados_Activos` con `FILTRAR`, `UNICOS`, `ELEGIRCOLS`, `APILARH` y `#`. |
| **5** | 2.5 Gráficos Dinámicos | Dashboard visual con gráficos múltiples (columnas, líneas y anillos). |
| **6** | 2.6 Impresión y Layout | Configuración de títulos de impresión, saltos de página y vista tabular. |
| **7** | 2.7 Funciones Avanzadas | Módulo de consulta con `BUSCARX`, `BDPROMEDIO` y amortización `PAGO`. |
| **8** | 2.8 Plantillas y Formularios | Plantilla `.xltx` con controles de formulario y protección de celda. |
| **9** | 2.9 Simulación de Escenarios | Informe Resumen de Escenarios y Tabla de Datos de 2 variables. |
| **10** | 2.10 Macros y Automatización | Botón interactivo con macro grabada en archivo `.xlsm`. |

---
*Manual elaborado de acuerdo a las especificaciones del Módulo 2 de Excel Avanzado (Especialidad IFCT56 Excel Avanzado y Power BI) y adaptado a Microsoft 365 Edición Educativa (Configuración regional: Español de España).*
