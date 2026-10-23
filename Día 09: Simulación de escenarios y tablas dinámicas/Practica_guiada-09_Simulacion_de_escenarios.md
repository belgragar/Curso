
# Práctica Guiada 09: Análisis de Datos y Simulación de Escenarios Financieros

---

## 1. Contexto de Negocio

La dirección de **Nortech Solutions S.L.** necesita evaluar la sensibilidad y las alternativas de su plan de financiación (100.000 € a amortizar mediante cuotas fijas) ante posibles cambios en el entorno económico.

Para ello, utilizaremos las herramientas de **Análisis de hipótesis** (*¿Qué pasaría si...?*) desarrolladas en el temario:

1. **Búsqueda de Objetivo:** Ajustar el capital prestado o los plazos para lograr una cuota mensual exacta.


2. **Tabla de Datos de Una Variable:** Analizar el impacto de diferentes tipos de interés en la cuota mensual.


3. **Tabla de Datos de Dos Variables:** Evaluar simultáneamente la cuota mensual variando tanto el tipo de interés como el plazo en años.


4. **Administrador de Escenarios:** Configurar y comparar tres escenarios financieros corporativos (*Conservador*, *Base* y *Agresivo*) y generar su **Informe de Resumen de Escenarios**.



---

## 2. Conjunto de Datos (Dataset)

Para mantener la continuidad didáctica, trabajaremos sobre el modelo financiero anterior. Abre tu libro de Excel, crea una hoja llamada **Análisis_Hipótesis** y copia exactamente el siguiente bloque a partir de la celda **A1**:

```csv
Parametro_Financiacion;Valor;Unidad
Importe del Prestamo (VA);100000;€
Interes Anual Nominal;0,06;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Tasa Mensual;=B3/B5;Porcentaje
Total Periodos (NPER);=B4*B5;Meses
Cuota Mensual Fija;=PAGO(B6;B7;-B2);€/mes

```

---

## 3. Tareas a Resolver

1. **Búsqueda de Objetivo (`Datos > Análisis de hipótesis > Buscar objetivo`):**
* La empresa dispone de un presupuesto máximo de **1.800,00 €/mes**. Utiliza la *Búsqueda de objetivo* para averiguar cuál debe ser el **Importe del Préstamo (celda `B2`)** para ajustar la cuota mensual exacta a **1.800,00 €**. (Tras observar el resultado, restablece el importe inicial a **100.000 €**).




2. **Tabla de Datos de Una Variable:**
* Construye una tabla analítica que muestre cómo varía la cuota mensual si el interés anual cambia desde el **4,00%** hasta el **8,00%** en incrementos del **0,50%**.




3. **Tabla de Datos de Dos Variables:**
* Crea una matriz de doble entrada que evalúe la cuota mensual combinando distintos tipos de interés (**4,00%** a **8,00%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).




4. **Administrador de Escenarios y Resumen Ejecutivos:**
* Define 3 escenarios de financiación variando el *Importe del Préstamo* (`B2`), el *Interés Anual* (`B3`) y el *Plazo en Años* (`B4`):


* **Escenario Base:** `100.000 €` | `6,00%` | `5 años`
* **Escenario Conservador (Restricción):** `80.000 €` | `7,50%` | `4 años`
* **Escenario Agresivo (Expansión):** `120.000 €` | `5,00%` | `6 años`


* Genera automáticamente un **Informe de Resumen de Escenarios** en una nueva hoja.





---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Búsqueda de Objetivo para ajustar la cuota mensual

> **Enunciado de la tarea:**
> La empresa dispone de un presupuesto máximo de **1.800,00 €/mes**. Utiliza la *Búsqueda de objetivo* para averiguar cuál debe ser el **Importe del Préstamo (celda `B2`)** para ajustar la cuota mensual exacta a **1.800,00 €**. (Tras observar el resultado, restablece el importe inicial a **100.000 €**).
> 
> 

1. Haz clic en la celda `B8` (Cuota Mensual Fija).
2. Ve a la pestaña **Datos > Análisis de hipótesis > Buscar objetivo...**

3. En el cuadro de diálogo configura:


* **Definir la celda:** `B8`
* **Con el valor:** `1800`
* **Para cambiar la celda:** `B2`


4. Haz clic en **Aceptar**.
* *(Resultado esperado: Excel calculará un importe de préstamo de **93.100,82 €**)*.


5. Pulsa **Cancelar** o escribe de nuevo `100000` en `B2` para mantener los datos originales de partida.

---

### Paso 2: Crear una Tabla de Datos de Una Variable (Sensibilidad de Interés)

> **Enunciado de la tarea:**
> Construye una tabla analítica que muestre cómo varía la cuota mensual si el interés anual cambia desde el **4,00%** hasta el **8,00%** en incrementos del **0,50%**.
> 
> 

1. Prepara la estructura de la tabla en el rango `D2:E11`:
* En la celda `D2` deja el espacio vacío o escribe la etiqueta `Interés Anual`.
* En la celda `E2` introduce la fórmula de referencia a la cuota: `=B8`.


* En el rango `D3:D11` escribe la serie de intereses: `4,00%`, `4,50%`, `5,00%`, `5,50%`, `6,00%`, `6,50%`, `7,00%`, `7,50%`, `8,00%`.


2. Selecciona todo el rango de la tabla: **`D2:E11`**.


3. Ve a **Datos > Análisis de hipótesis > Tabla de datos...**

4. Como los valores de entrada están dispuestos verticalmente en una columna:


* Deja en blanco *Celda de entrada (fila)*.
* En **Celda de entrada (columna)**, selecciona la celda del modelo: **`B3`** (Interes Anual Nominal).




5. Haz clic en **Aceptar** y aplica formato de moneda (`€`) a la columna `E`.
* *(Resultado esperado: Al 4,00% la cuota será `1.841,65 €`; al 6,00% será `1.933,28 €`; al 8,00% será `2.027,64 €`)*.



---

### Paso 3: Crear una Tabla de Datos de Dos Variables (Interés vs. Plazo)

> **Enunciado de la tarea:**
> Crea una matriz de doble entrada que evalúe la cuota mensual combinando distintos tipos de interés (**4,00%** a **8,00%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).
> 
> 

1. Prepara la estructura de la matriz en el rango `G2:L11`:
* En la celda esquina `G2` vincula la fórmula de la cuota: **`=B8`**.


* En la cabecera horizontal (`H2:L2`) introduce los plazos en años: `3`, `4`, `5`, `6`, `7`.
* En la columna vertical (`G3:G11`) introduce los intereses: `4,00%`, `4,50%`, `5,00%`, `5,50%`, `6,00%`, `6,50%`, `7,00%`, `7,50%`, `8,00%`.


2. Selecciona todo el rango de la matriz: **`G2:L11`**.


3. Ve a **Datos > Análisis de hipótesis > Tabla de datos...**

4. Configura los dos parámetros:


* **Celda de entrada (fila):** **`B4`** (Plazo en Anos — coincide con los valores en la fila `H2:L2`).


* **Celda de entrada (columna):** **`B3`** (Interes Anual Nominal — coincide con los valores en la columna `G3:G11`).




5. Haz clic en **Aceptar** y da formato de moneda (`€`) al interior de la tabla (`H3:L11`).
* *(Resultado esperado: Podrás comparar de un vistazo la cuota para cualquier combinación; ej. a 3 años y 4,00% la cuota es `2.952,40 €`)*.



---

### Paso 4: Configurar Administrador de Escenarios e Informe de Resumen

> **Enunciado de la tarea:**
> Define 3 escenarios de financiación variando el *Importe del Préstamo* (`B2`), el *Interés Anual* (`B3`) y el *Plazo en Años* (`B4`). Genera automáticamente un **Informe de Resumen de Escenarios** en una nueva hoja.
> 
> 

1. Ve a **Datos > Análisis de hipótesis > Administrador de escenarios...**

2. **Crear Escenario Base:**
* Haz clic en **Agregar**.


* Nombre del escenario: `Base`.


* Celdas cambiantes: **`B2:B4`**.


* Haz clic en **Aceptar** e introduce sus valores:


* `B2`: `100000`
* `B3`: `0,06`
* `B4`: `5`




3. **Crear Escenario Conservador:**
* Haz clic en **Agregar**.


* Nombre del escenario: `Conservador`.


* Celdas cambiantes: **`B2:B4`**.


* Haz clic en **Aceptar** e introduce sus valores:


* `B2`: `80000`
* `B3`: `0,075`
* `B4`: `4`




4. **Crear Escenario Agresivo:**
* Haz clic en **Agregar**.


* Nombre del escenario: `Agresivo`.


* Celdas cambiantes: **`B2:B4`**.


* Haz clic en **Aceptar** e introduce sus valores:


* `B2`: `120000`
* `B3`: `0,05`
* `B4`: `6`




5. **Generar Informe Resumen:**
* En la ventana del Administrador de escenarios, haz clic en el botón **Resumen...**

* Selecciona **Resumen de escenarios**.


* En **Celdas de resultado**, selecciona la celda de la cuota: **`B8`**.


* Haz clic en **Aceptar**.





---

### Resumen Didáctico de Interpretación

* **Informe de Resumen:** Excel creará una pestaña nueva llamada **Resumen de escenario** con una tabla comparativa estática que contrapone las variables de entrada y la cuota resultante (`B8`) de cada alternativa:


* **Conservador:** Cuota de **1.933,90 €/mes** (menor endeudamiento pero menor plazo).
* **Base:** Cuota de **1.933,28 €/mes**.
* **Agresivo:** Cuota de **1.932,56 €/mes** (mayor capital dispuesto diluido en un plazo más amplio y menor tasa).




* **Nota didáctica sobre Escenarios:** Recuerda a los alumnos que los informes de escenarios **no se recalculan automáticamente** si cambias las celdas del modelo. Si se modifican las condiciones iniciales, se debe volver a hacer clic en **Resumen...** para actualizar la tabla comparativa.

# Práctica Guiada 09: Optimización de Modelos Financieros con Solver y Análisis de Escenarios

## 1. Contexto de Negocio

La empresa tecnológica **Nortech Solutions S.L.** está planificando el presupuesto de amortización de un préstamo corporativo de **100.000 €** a un tipo de interés nominal del **6,00% anual** a **5 años**.

Hasta ahora, la dirección financiera ha evaluado el comportamiento de la cuota mensual mediante *Búsqueda de Objetivos*, *Tablas de Datos* y el *Administrador de Escenarios*. Sin embargo, la gerencia necesita resolver un problema de **optimización con múltiples variables sujetas a restricciones operativas del negocio** (límites de cuota máxima mensual, plazo máximo permitido por la entidad bancaria e importe mínimo del préstamo para cubrir la compra del equipamiento).

Para dar respuesta a estas exigencias, utilizaremos la herramienta matemática **Solver**. Además, aplicaremos la técnica de **Guardar Escenarios desde Solver** para consolidar los resultados óptimos dentro del *Administrador de Escenarios* y generar un **Informe de Resumen Ejecutivo** comparativo para la dirección.

---

## 2. Conjunto de Datos (Dataset)

Abre tu libro de Excel, crea una hoja llamada **Optimizacion_Solver** y copia exactamente la siguiente estructura a partir de la celda **A1**. Los datos están delimitados por punto y coma (`;`) para adaptarse estrictamente a la configuración regional de España (separador decimal con coma `,`).

```csv
Parametro_Financiacion;Valor;Unidad
Importe del Prestamo (VA);100000;€
Interes Anual Nominal;0,06;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Tasa Mensual;=B3/B5;Porcentaje
Total Periodos (NPER);=B4*B5;Meses
Cuota Mensual Fija;=PAGO(B6;B7;-B2);€/mes

```

---

## 3. Tareas a Resolver

1. **Activación de la herramienta Solver en Excel:**
* Verificar si el complemento **Solver** está activo en la pestaña *Datos* (grupo *Analizar*) y, en caso contrario, habilitarlo desde el menú *Opciones de Excel > Complementos*.




2. **Asignación de Nombres a Celdas de Trabajo (Buena Práctica):**
* Asignar nombres significativos a las celdas clave (`B2`: `Importe_Prestamo`, `B3`: `Interes_Anual`, `B4`: `Plazo_Anos`, `B8`: `Cuota_Mensual`) antes de ejecutar el análisis para que el informe final resulte legible e intuitivo para la dirección.




3. **Caso 1 — Optimización Básica con Solver (Maximizar Financiación con Límite de Cuota):**
* Configurar **Solver** para encontrar el **máximo importe de préstamo** que la empresa puede solicitar (`B2`), manteniendo el interés al 6,00% anual y el plazo a 5 años, respetando las siguientes restricciones:


* La `Cuota_Mensual` (`B8`) no puede superar los **1.850,00 €/mes**.


* El `Importe_Prestamo` (`B2`) debe ser como mínimo de **80.000 €**.




* Al encontrar la solución óptima, utilizar el botón **Guardar escenario...** de Solver y nombrarlo **`Optimo_Cuota1850`**.




4. **Caso 2 — Optimización Multivariable con Solver (Ajuste de Capital y Plazo):**
* Configurar **Solver** modificando simultáneamente **dos celdas cambiantes**: el `Importe_Prestamo` (`B2`) y el `Plazo_Anos` (`B4`), bajo las siguientes restricciones del mercado financiero:


* Minimizar la `Cuota_Mensual` (`B8`).


* `Importe_Prestamo` (`B2`) debe ser exactamente de **100.000 €**.


* `Plazo_Anos` (`B4`) debe ser mayor o igual a **3 años** y menor o igual a **7 años** (`<= 7`).


* `Plazo_Anos` (`B4`) debe ser obligatoriamente un **número entero** (`int`).




* Al encontrar la solución, guardar el resultado como un nuevo escenario denominado **`Optimo_PlazoMaximo`**.




5. **Generación del Informe Resumen Consolidado:**
* Acceder al **Administrador de escenarios** (`Datos > Análisis de hipótesis > Administrador de escenarios`) y generar un **Informe de Resumen de Escenarios** que contraponga los escenarios guardados desde Solver.





---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Activar el complemento Solver en Excel

> **Enunciado de la tarea:**
> Verificar si el complemento **Solver** está activo en la pestaña *Datos* (grupo *Analizar*) y, en caso contrario, habilitarlo desde el menú *Opciones de Excel > Complementos*.
> 
> 

1. Ve a la pestaña **Datos** en la cinta de opciones superior.


2. Comprueba si en el extremo derecho aparece el botón **Solver** (grupo *Analizar*).


3. Si no aparece visible:


* Haz clic en **Archivo > Opciones**.


* Selecciona **Complementos** en el panel izquierdo.


* En el menú desplegable inferior (*Administrar:*), asegúrate de que está seleccionado **Complementos de Excel** y haz clic en **Ir...**

* Marca la casilla **Solver** y pulsa **Aceptar**.





---

### Paso 2: Asignar nombres a las celdas de trabajo

> **Enunciado de la tarea:**
> Asignar nombres significativos a las celdas clave (`B2`: `Importe_Prestamo`, `B3`: `Interes_Anual`, `B4`: `Plazo_Anos`, `B8`: `Cuota_Mensual`) antes de ejecutar el análisis para que el informe final resulte legible e intuitivo para la dirección.
> 
> 

1. Haz clic en la celda `B2`. En el **Cuadro de Nombres** (situado a la izquierda de la barra de fórmulas), escribe `Importe_Prestamo` y presiona *Intro*.


2. Haz clic en la celda `B3`, dirígete al Cuadro de Nombres, escribe `Interes_Anual` y presiona *Intro*.


3. Haz clic en la celda `B4`, dirígete al Cuadro de Nombres, escribe `Plazo_Anos` y presiona *Intro*.


4. Haz clic en la celda `B8`, dirígete al Cuadro de Nombres, escribe `Cuota_Mensual` y presiona *Intro*.



---

### Paso 3: Resolver el Caso 1 con Solver y guardar el escenario (`Optimo_Cuota1850`)

> **Enunciado de la tarea:**
> Configurar **Solver** para encontrar el **máximo importe de préstamo** que la empresa puede solicitar (`B2`), manteniendo el interés al 6,00% anual y el plazo a 5 años, respetando las siguientes restricciones:
> 
> 
> * La `Cuota_Mensual` (`B8`) no puede superar los **1.850,00 €/mes**.
> 
> 
> * El `Importe_Prestamo` (`B2`) debe ser como mínimo de **80.000 €**.
> Al encontrar la solución óptima, utilizar el botón **Guardar escenario...** de Solver y nombrarlo **`Optimo_Cuota1850`**.
> 
> 
> 
> 

1. Ve a la pestaña **Datos > Solver**.


2. Configura los campos del panel de parámetros de Solver:


* **Establecer objetivo:** Selecciona la celda `B2` (`Importe_Prestamo`).


* **Para:** Selecciona la opción **Máx** (para maximizar el capital solicitado).


* **Cambiando las celdas de variables:** Selecciona la celda `B2` (`Importe_Prestamo`).




3. Añade las restricciones haciendo clic en el botón **Agregar**:


* *Restricción 1:* `Cuota_Mensual` (`B8`) `<= 1850`

* *Restricción 2:* `Importe_Prestamo` (`B2`) `>= 80000`



4. Selecciona el método de resolución **Simplex LP** o **GRG No Lineal** y pulsa **Resolver**.


5. En el cuadro de diálogo **Resultados de Solver**:


* Verifica que Solver ha encontrado una solución.


* Haz clic en el botón **Guardar escenario...** (situado en la parte derecha de la ventana).


* En el cuadro emergente, escribe como nombre: `Optimo_Cuota1850` y pulsa **Aceptar**.


* Selecciona **Conservar solución de Solver** y pulsa **Aceptar**.





*(Resultado esperado: El importe del préstamo se ajustará automáticamente a **95.692,80 €**, con una cuota exacta de **1.850,00 €/mes**)*.

---

### Paso 4: Resolver el Caso 2 con Solver y guardar el escenario (`Optimo_PlazoMaximo`)

> **Enunciado de la tarea:**
> Configurar **Solver** modificando simultáneamente **dos celdas cambiantes**: el `Importe_Prestamo` (`B2`) y el `Plazo_Anos` (`B4`), bajo las siguientes restricciones del mercado financiero:
> 
> 
> * Minimizar la `Cuota_Mensual` (`B8`).
> 
> 
> * `Importe_Prestamo` (`B2`) debe ser exactamente de **100.000 €**.
> 
> 
> * `Plazo_Anos` (`B4`) debe ser mayor o igual a **3 años** y menor o igual a **7 años** (`<= 7`).
> 
> 
> * `Plazo_Anos` (`B4`) debe ser obligatoriamente un **número entero** (`int`).
> Al encontrar la solución, guardar el resultado como un nuevo escenario denominado **`Optimo_PlazoMaximo`**.
> 
> 
> 
> 

1. Abre nuevamente **Datos > Solver**.


2. Pulsa el botón **Restablecer todo** para limpiar la configuración previa.
3. Configura el nuevo modelo:


* **Establecer objetivo:** Selecciona `B8` (`Cuota_Mensual`).


* **Para:** Selecciona **Mín** (para minimizar el impacto mensual en caja).


* **Cambiando las celdas de variables:** Selecciona el rango `B2; B4` (`Importe_Prestamo` y `Plazo_Anos`).




4. Pulsa **Agregar** para incluir las siguientes restricciones:


* `B2` (`Importe_Prestamo`) `= 100000`

* `B4` (`Plazo_Anos`) `>= 3`

* `B4` (`Plazo_Anos`) `<= 7`

* `B4` (`Plazo_Anos`) operador **int** (entero).




5. Pulsa **Resolver**.


6. En la ventana **Resultados de Solver**:


* Haz clic en **Guardar escenario...**

* Nombra el escenario como: `Optimo_PlazoMaximo` y pulsa **Aceptar**.


* Marca **Conservar solución de Solver** y haz clic en **Aceptar**.





*(Resultado esperado: Solver ampliará el plazo a **7 años**, reduciendo la cuota fija mensual a **1.460,86 €/mes**)*.

---

### Paso 5: Generar el Informe Resumen Consolidado de Escenarios

> **Enunciado de la tarea:**
> Acceder al **Administrador de escenarios** (`Datos > Análisis de hipótesis > Administrador de escenarios`) y generar un **Informe de Resumen de Escenarios** que contraponga los escenarios guardados desde Solver.
> 
> 

1. Ve a la pestaña **Datos > Análisis de hipótesis > Administrador de escenarios...**

2. Observa la lista de escenarios guardados: comprobarás que aparecen registrados **`Optimo_Cuota1850`** y **`Optimo_PlazoMaximo`** gracias al vínculo directo con Solver.


3. Haz clic en el botón **Resumen...**

4. En el tipo de informe, deja seleccionada la opción **Resumen de escenarios**.


5. En **Celdas de resultado**, asegúrate de que está seleccionada la celda `B8` (`Cuota_Mensual`).


6. Haz clic en **Aceptar**.



---

### Resumen Didáctico e Interpretación de Resultados

* **Integración Nativa Solver - Escenarios:** Gracias a la opción *Guardar escenario* al finalizar la ejecución de Solver, evitamos perder los resultados de las optimizaciones matemáticas previas. Excel consolida automáticamente las soluciones en una nueva pestaña de informe.


* **Aportación de Nombres a Celdas:** Al haber etiquetado previamente las celdas (`Importe_Prestamo`, `Plazo_Anos`, `Cuota_Mensual`), la tabla resumen no muestra referencias abstractas como `B2` o `B8`, sino nombres de negocio directamente comprensibles para el equipo directivo.


* **Conclusión de Negocio:**
* Si la empresa restringe su flujo de caja a 1.850,00 €/mes a 5 años, solo podrá solicitar **95.692,80 €**.


* Si la empresa requiere obligatoriamente los **100.000 €** de financiación, optimizar el plazo a 7 años permite reducir la cuota a **1.460,86 €/mes**, mejorando notablemente la liquidez operativa.
