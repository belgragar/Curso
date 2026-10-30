# 🏔️ PROYECTO INTEGRADOR: GESTIÓN INTEGRAL DE LA RED DE ALBERGUES DEL CAMINO DE SANTIAGO EN ASTURIAS

## Manual Práctico de Aplicación por Fases — Excel Avanzado (Microsoft 365, Configuración Regional: Español de España)

---

### 📌 PRESENTACIÓN DEL PROYECTO Y CONTEXTO DE NEGOCIO

La **Fundación Jacobea del Principado de Asturias** gestiona la Red Pública de Albergues, Puntos de Acogida y Servicios de Atención al Peregrino a lo largo de las dos grandes rutas jacobeas asturianas:

1. **El Camino Primitivo:** *Oviedo → Grado → Salas → Tineo → Pola de Allande → Grandas de Salime*.
2. **El Camino del Norte (Costa):** *Llanes → Ribadesella → Villaviciosa → Gijón / Avilés → Luarca → Castropol*.

Para modernizar la gestión operativa, auditar la afluencia, simular presupuestos de conservación y automatizar los partes diarios de recepción, la Fundación ha encomendado la construcción del libro de trabajo maestro **`Camino_Santiago_Asturias_Gestion.xlsm`**.

Todas las fórmulas y funciones de este proyecto se han configurado estrictamente bajo el estándar de **Microsoft 365 en español de España**, utilizando punto y coma (`;`) como separador de argumentos en las fórmulas (por ejemplo, `=FILTRAR(rango; condición)`).

---

## 📋 DATOS DE EJEMPLO PARA EL PROYECTO (FORMATO TSV PARA PEGAR DIRECTAMENTE EN EXCEL)

> 💡 **Instrucciones de copia para el alumnado:** Selecciona todo el contenido dentro del bloque de código TSV a continuación, cópialo (`Ctrl + C`) y pégalo directamente en la celda `A1` de una hoja vacía de Excel (`Ctrl + V`). Excel separará automáticamente el texto en columnas. A continuación, selecciona los datos y pulsa `Ctrl + T` para convertir el rango en la tabla estructurada `Tbl_RegistroPeregrinos`.

### 1. Tabla Principal: `Tbl_RegistroPeregrinos` (50 registros)

```tsv
ID_Registro	Fecha	Ruta	Etapa	Albergue	Concejo	Pais_Origen	Pernoctaciones	Aportacion_EUR
REG-001	01/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	España	1	5,00
REG-002	01/05/2026	Camino Primitivo	Etapa 1	Albergue de Oviedo	Oviedo	Francia	2	10,00
REG-003	02/05/2026	Camino Primitivo	Etapa 2	Albergue de Grado	Grado	Alemania	1	7,50
REG-004	02/05/2026	Camino del Norte	Etapa 1	Albergue de Llanes	Llanes	Italia	1	5,00
REG-005	03/05/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	España	3	15,00
REG-006	03/05/2026	Camino Primitivo	Etapa 3	Albergue de Salas	Salas	Portugal	1	6,00
REG-007	04/05/2026	Camino Primitivo	Etapa 4	Albergue de Tineo	Tineo	Países Bajos	2	12,00
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
REG-018	09/05/2026	Camino del Norte	Etapa 1	Albergue de Llanes	Llanes	España	2	10,00
REG-019	10/05/2026	Camino del Norte	Etapa 2	Albergue de Ribadesella	Ribadesella	Italia	1	5,00
REG-020	10/05/2026	Camino Primitivo	Etapa 4	Albergue de Tineo	Tineo	Alemania	3	18,00
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

### 2. Tabla Auxiliar: `Tbl_Albergues` (10 registros)

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

### 🔹 FASE 2: CONFIGURACIÓN DE CAMPOS DE VALOR Y MÉTRICAS DE CUOTA

* **Epígrafe del Manual:** **`2.2 Configuración de los campos de valor`**
* **Contexto Jacobeo:** Evaluación de la contribución económica media y distribución por país de procedencia de los caminantes.

#### 📝 Tareas a desarrollar:

1. **Múltiples métricas sobre un mismo campo:** En la hoja `TD_Analisis_Economico`, insertar una Tabla Dinámica con el campo *Pais_Origen* en **FILAS** y añadir el campo *Aportacion_EUR* **tres veces** en el área de **VALORES**.
2. **Configuración de funciones de resumen:**
* **Campo 1:** Renombrar a "Aportación Total" (Función *Suma*).
* **Campo 2:** Renombrar a "Aportación Media por Peregrino" (Función *Promedio*).
* **Campo 3:** Renombrar a "% Cuota de Afluencia" (Configurar en *Mostrar valores como* -> **% del total general**).


3. **Formato persistente de campo:** Aplicar formato de moneda `Moneda (€)` a los dos primeros campos y `Porcentaje (0,0%)` al tercero directamente desde *Configuración de campo de valor > Formato de número*.

---

### 🔹 FASE 3: GESTIÓN INTERACTIVA DE DATOS, AGRUPACIONES Y EXTRAICIÓN

* **Epígrafe del Manual:** **`2.3 Gestión de datos en tablas dinámicas`**
* **Contexto Jacobeo:** Estacionalidad de las pernoctaciones y control de aportaciones por intervalos.

#### 📝 Tareas a desarrollar:

1. **Agrupación temporal y por intervalos:**
* En `TD_Estacionalidad`, agrupar el campo *Fecha* por **Meses** y **Trimestres** para observar los picos de afluencia.
* Agrupar el campo *Aportacion_EUR* en intervalos o tramos de 5 € (de 0 € a 20 €) para analizar el perfil de donaciones de los peregrinos.


2. **Controles visuales de filtrado:**
* Insertar una **Segmentación de Datos (Slicer)** para el campo *Ruta*.
* Insertar una **Escala de Tiempo (Timeline)** sobre el campo *Fecha*.
* Sincronizar ambos controles con las tablas dinámicas mediante *Conexiones de informe*.


3. **Extracción directa:** Utilizar la función `=IMPORTARDATOSDINAMICOS()` en un panel exterior para extraer el total de pernoctaciones del albergue de *Salas* y de *Pola de Allande*.

---

### 🔹 FASE 4: GENERACIÓN DE LISTADOS DINÁMICOS CON MATRICES DESBORDADAS Y NUEVAS FUNCIONES DE M365 (`ELEGIRCOLS`, `APILARH`)

* **Epígrafe del Manual:** **`2.4 Listados Dinámicos`**
* **Contexto Jacobeo:** Automatización del directorio activo de albergues, construcción de informes ejecutivos compuestos con matrices dinámicas y consultas dinámicas.

#### 📝 Tareas a desarrollar:

1. **Matriz derramada de albergues destacados:** En la hoja `Listados_Activos`, construir una fórmula en una sola celda utilizando las funciones de matriz dinámica:
```excel
=ORDENAR(FILTRAR(Tbl_Albergues[Nombre_Albergue]; (Tbl_Albergues[Ruta]="Camino Primitivo") * (Tbl_Albergues[Plazas]>20); "Sin resultados"); 1; 1)

```


2. **Selección de columnas específicas con `ELEGIRCOLS`:** Generar un reporte simplificado de la tabla `Tbl_Albergues` mostrando únicamente las columnas de *Nombre_Albergue* (columna 2) y *Telefono* (columna 6) filtradas para el Camino del Norte:
```excel
=ELEGIRCOLS(FILTRAR(Tbl_Albergues; Tbl_Albergues[Ruta]="Camino del Norte"); 2; 6)

```


3. **Consolidación horizontal con `APILARH`:** Crear un encabezado compuesto uniendo en paralelo las etiquetas "Albergue", "Concejo" y "Capacidad" con sus respectivos datos filtrados:
```excel
=APILARH(ELEGIRCOLS(Tbl_Albergues; 2; 4); ELEGIRCOLS(Tbl_Albergues; 5))

```


4. **Listado de países sin duplicados:** Generar una columna derramada con `=ORDENAR(UNICOS(Tbl_RegistroPeregrinos[Pais_Origen]))`.
5. **Lista desplegable dinámica con operador `#`:**
* En una celda de consulta (`B3`), crear una Validación de Datos de tipo *Lista*.
* En el origen, apuntar a la primera celda de la lista de países derramada añadiendo el operador de desbordamiento: `=H2#`.


---


### 🔹 FASE 5: DASHBOARD VISUAL CON GRÁFICOS DINÁMICOS

* **Epígrafe del Manual:** **`2.5 Gráficos Dinámicos`**
* **Contexto Jacobeo:** Panel ejecutivo visual de comparativa entre rutas y ocupación por etapas.

#### 📝 Tareas a desarrollar:

1. **Creación de Gráficos Dinámicos:**
* **Gráfico 1 (Columnas Agrupadas):** Vinculado a la ocupación por albergue en el Camino Primitivo (*Oviedo, Grado, Salas, Tineo, Allande, Grandas*).
* **Gráfico 2 (Líneas con Marcadores):** Vinculado a la evolución mensual de pernoctaciones comparando Camino Primitivo vs. Camino del Norte.


2. **Personalización UX/UI:**
* Ocultar todos los botones de campos del gráfico para una estética limpia.
* Añadir etiquetas de datos y títulos dinámicos.
* Conectar los gráficos a la segmentación de datos de *Ruta* y a la escala de tiempo.


---


### 🔹 FASE 6: PREPARACIÓN DE INFORMES PARA IMPRESIÓN Y EXPORTACIÓN EXECUTIVE

* **Epígrafe del Manual:** **`2.6 Impresión y visualización de contenidos dinámicos`**
* **Contexto Jacobeo:** Presentación oficial de memoria anual ante la Consejería de Cultura y Turismo del Principado de Asturias.

#### 📝 Tareas a desarrollar:

1. **Configuración de página e impresión:**
* Definir el **Área de Impresión** en la hoja de informe mensual evitando zonas vacías.
* Configurar **Títulos de Impresión** (`Diseño de página > Imprimir títulos`) para repetir las filas de encabezado en todas las páginas impresas.
* Insertar un salto de página automático tras cada etapa/concejo.


2. **Visualización y diseño de informe:**
* Inmovilizar los paneles superiores para mantener visibles las cabeceras durante el desplazamiento (*Vista > Inmovilizar paneles*).
* Ajustar el diseño de las tablas dinámicas a **Formato Tabular** con la opción **Repetir todas las etiquetas de elementos** activada.


---


### 🔹 FASE 7: MODELADO DE BÚSQUEDA, DEPURACIÓN DE TEXTOS, BASE DE DATOS Y FINANZAS

* **Epígrafe del Manual:** **`2.7 Funciones avanzadas: Búsqueda, Mates/Cadenas, Base de datos y Financieras`**
* **Contexto Jacobeo:** Auditoría técnica de datos, limpieza de registros de credenciales y cuadro de amortización de préstamos para reformas de albergues.

#### 📝 Tareas a desarrollar:

1. **2.7.1 Búsquedas bidireccionales y avanzadas:**
* Usar `BUSCARX` para consultar el teléfono de emergencia y plazas de un albergue según su código:
`=BUSCARX(B3; Tbl_Albergues[ID_Albergue]; Tbl_Albergues[Telefono]:Tbl_Albergues[Plazas]; "No hallado")`.
* Realizar una búsqueda en 2 ejes (*Albergue × Mes*) combinando `INDICE` + `COINCIDIRX`.


2. **2.7.2 Limpieza de texto y matemática de precisión:**
* Corregir nombres de peregrinos importados con espacios superfluos usando `ESPACIOS()`.
* Extraer el código de concejo a partir del localizador mediante `TEXTOANTES()` o `EXTRAE()`.
* Unir el código de credencial y país mediante `UNIRCADENAS("-"; VERDADERO; Rango)`.
* Calcular importes filtrados respetando filas ocultas con `SUBTOTALES(109; Rango)`.


3. **2.7.3 Funciones de Base de Datos:**
* Crear un cuadro de criterios en la hoja y aplicar `BDPROMEDIO` y `BDSUMA` para calcular la estancia media y donaciones de peregrinos procedentes de *Alemania* o *Francia* en el *Camino Primitivo*.


4. **2.7.4 Modelado financiero del albergue de Grandas de Salime:**
* Para financiar la reforma del albergue de Grandas de Salime (Préstamo: 80.000 €, Plazo: 5 años, Interés anual: 4,5%):
* Calcular la cuota mensual con `=PAGO(4,5%/12; 5*12; -80000)`.
* Desglosar intereses y capital cuota a cuota con `PAGOINT()` y `PAGOPRIN()`.
* Determinar la Tasa Interna de Retorno con `TIR()` para evaluar la sostenibilidad del proyecto.

---

### 🔹 FASE 8: DIGITALIZACIÓN DEL PARTE DE RECEPCIÓN MEDIANTE PLANTILLAS Y FORMULARIOS

* **Epígrafe del Manual:** **`2.8 Creación de plantillas y formularios`**
* **Contexto Jacobeo:** Estándar digital de entrada de peregrinos en el albergue de Pola de Allande.

#### 📝 Tareas a desarrollar:

1. **Diseño del Formulario de Entrada:**
* Insertar un **Cuadro Combinado (Combo Box)** para seleccionar la nacionalidad del peregrino.
* Insertar **Botones de Opción (Radio Buttons)** dentro de un **Cuadro de Grupo (Frame)** para marcar el tipo de credencial (*Oficial Jacobea*, *Digital*, *Federación Internacional*).
* Insertar una **Casilla de Verificación (Checkbox)** para indicar si el peregrino solicita servicio de *Transporte de Equipaje (Mochila)*.
* Insertar un **Control de Número (Spinner)** para seleccionar el número de pernoctaciones.


2. **Vinculación a celdas y fórmulas de cálculo:** Vincular los controles a celdas ocultas y calcular la tarifa final mediante `=SI()`, `=ELEGIR()` e `=INDICE()`.
3. **Protección y guardado:** Bloquear las celdas con fórmulas, desproteger solo las celdas de entrada, proteger la hoja con contraseña y guardar el archivo como **Plantilla de Excel (`.xltx`)**.

---

### 🔹 FASE 9: ANÁLISIS DE HIPÓTESIS, SENSIBILIDAD Y SIMULACIÓN DE ESCENARIOS

* **Epígrafe del Manual:** **`2.9 Análisis de datos. Simulación de escenarios`**
* **Contexto Jacobeo:** Planificación económica de la red pública ante fluctuaciones turísticas e inflación de costes energéticos.

#### 📝 Tareas a desarrollar:

1. **Administrador de Escenarios:**
* Definir 3 hipótesis de gestión para la temporada alta:
* **Escenario Conservador:** Aportación sugerida = 5 €, Ocupación = 60%.
* **Escenario Previsto:** Aportación sugerida = 8 €, Ocupación = 80%.
* **Escenario Optimista:** Aportación sugerida = 10 €, Ocupación = 95%.


* Generar el **Informe Resumen de Escenarios** en una hoja nueva.


2. **Tabla de Datos de 2 Variables (Matriz de Sensibilidad):**
* Crear una Tabla de Datos de dos entradas que evalúe el *Beneficio Neto Anual del Albergue* cruzando diferentes niveles de *Aportación Media (filas: 5€ a 12€)* y *Coste Energético Mensual (columnas: 400€ a 1.200€)*.


3. **Búsqueda de Objetivo / Solver:**
* Aplicar *Búsqueda de Objetivo* para determinar cuántos peregrinos deben alojarse en el albergue de *Tineo* para cubrir exactamente los costes fijos de mantenimiento de 3.500 € mensuales (punto de equilibrio / breakeven).

---

### 🔹 FASE 10: AUTOMATIZACIÓN DE TAREAS REPETITIVAS CON MACROS Y VBA

* **Epígrafe del Manual:** **`2.10 Macros. Herramientas avanzadas`**
* **Contexto Jacobeo:** Automatización del proceso de cierre diario de caja y volcado de registro al archivo central.

#### 📝 Tareas a desarrollar:

1. **Grabación de Macro Operativa:**
* Utilizar la Grabadora de Macros para automatizar la limpieza de los campos de datos del formulario de entrada de peregrinos tras cada registro.
* Asignar un atajo de teclado (`Ctrl + Mayús + L`).


2. **Edición en Visual Basic para Aplicaciones (VBA):**
* Acceder al Editor de VBA (`Alt + F11`), abrir el módulo y optimizar el código insertando `Application.ScreenUpdating = False` al inicio para evitar parpadeos de pantalla.
* Añadir un mensaje de confirmación interactivo: `MsgBox "El registro de peregrinos se ha guardado correctamente.", vbInformation, "Red de Albergues de Asturias"`.


3. **Asignación visual:** Crear un botón con forma corporativa en la hoja de recepción (*"Registrar Peregrino"*) y asignarle la macro grabada.
4. **Seguridad:** Guardar definitivamente el documento con la extensión **Libro de Excel habilitado para macros (`.xlsm`)**.

---

## 📊 MATRIZ DE SEGUIMIENTO Y EVALUACIÓN PEDAGÓGICA

| Fase | Epígrafe del Manual | Entregable Práctico en `Camino_Santiago_Asturias_Gestion.xlsm` |
| --- | --- | --- |
| **1** | 2.1 Tablas Dinámicas Base | Hoja `TD_Afluencia_Concejos` con jerarquía Concejo > Albergue. |
| **2** | 2.2 Campos de Valor | Hoja `TD_Analisis_Economico` con Suma, Promedio y % de Cuota. |
| **3** | 2.3 Gestión e Interacción | Hoja `TD_Estacionalidad` con agrupación mensual, Slicers y Timeline. |
| **4** | 2.4 Listados Dinámicos | Hoja `Listados_Activos` con `FILTRAR`, `UNICOS`, `ELEGIRCOLS`, `APILARH` y `#`. |
| **5** | 2.5 Gráficos Dinámicos | Dashboard visual interactivo con gráficos conectados a Slicers. |
| **6** | 2.6 Impresión y Layout | Configuración de títulos de impresión, saltos de página y vista tabular. |
| **7** | 2.7 Funciones Avanzadas | Módulo de consulta con `BUSCARX`, `BDPROMEDIO` y amortización `PAGO`. |
| **8** | 2.8 Plantillas y Formularios | Plantilla `.xltx` con controles de formulario y protección de celda. |
| **9** | 2.9 Simulación de Escenarios | Informe Resumen de Escenarios y Tabla de Datos de 2 variables. |
| **10** | 2.10 Macros y Automatización | Botón interactivo con macro VBA en archivo `.xlsm`. |

---

*Manual elaborado de acuerdo a las especificaciones del Módulo 2 de Excel Avanzado (Especialidad IFCT56 Excel Avanzado y Power BI) y adaptado a Microsoft 365 Edición Educativa (Configuración regional: Español de España).*