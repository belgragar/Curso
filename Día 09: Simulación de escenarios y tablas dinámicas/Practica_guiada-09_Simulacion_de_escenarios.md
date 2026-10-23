# Práctica Guiada 09: Análisis de Datos y Simulación de Escenarios Financieros


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
