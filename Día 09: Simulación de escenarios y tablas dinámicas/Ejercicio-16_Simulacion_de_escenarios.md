# Ejercicio 16: Modelado Financiero, Optimización con Solver y Análisis de Escenarios para "Sidrería El Llagar de Asturias"

## 1. Contexto de Negocio

La empresa familiar **Sidrería El Llagar de Asturias S.L.**, ubicada en Villaviciosa, está evaluando la compra de un nuevo llagar tradicional y la ampliación de sus instalaciones por un valor total de **100.000 €**.

Para tomar la decisión ejecutiva, la gerencia necesita un análisis analítico integral en tres dimensiones:

1. **Modelización Financiera Inicial:** Determinar las cuotas de amortización del préstamo, el desglose de capital e intereses en el primer mes, la duración bajo restricción presupuestaria, el tipo de interés implícito, la capacidad de endeudamiento, el valor futuro acumulado y la rentabilidad del proyecto (`TIR`).
2. **Optimización Avanzada con Solver:** Encontrar la combinación óptima de **Importe del Préstamo** y **Plazo en Años** que maximice el valor actual neto de la operación o minimice el coste de financiación sujeto a restricciones estrictas del banco y de la tesorería de la sidrería. La solución hallada por Solver se guardará directamente como un **Escenario**.


3. **Análisis de Hipótesis y Sensibilidad:** Evaluar la sensibilidad de la cuota mediante una *Tabla de datos de dos variables* (interés vs. plazo) y comparar mediante el **Administrador de escenarios** los modelos *Base*, *Conservador*, *Agresivo* y el modelo *Optimizado por Solver*.



---

## 2. Conjunto de Datos (Dataset)

Copia los siguientes bloques de datos y pégalos en una hoja nueva de Excel llamada **Gestion_Sidreria** a partir de la celda **A1**. Los datos utilizan el punto y coma (`;`) como separador de columnas para garantizar la compatibilidad con el separador decimal de España (coma `,`).

```csv
Parametro_Financiacion;Valor;Unidad
Importe Inversion Llagar (VA);100000;€
Interes Anual Nominal;0,06;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Cuota Maxima Presupuestada;2000;€/mes
Oferta Entidad Financiera (Cuota);2100;€/mes

```

A continuación, en la celda **D1**, copia la tabla con la previsión de flujos de caja generados por la venta de cajas de sidra natural:

```csv
Año;Flujo de Caja (€)
Año 0 (Inversion Inicial);-100000
Año 1;22000
Año 2;28000
Año 3;35000
Año 4;40000
Año 5;45000

```

---

## 3. Tareas a Resolver

1. **Parámetros de Apoyo Temporal:**
* Calcula la **Tasa de Interés Mensual** y el **Número Total de Períodos ($NPER$)**.


2. **Cuota Periódica del Préstamo (`PAGO`):**
* Determina la cuota fija mensual para amortizar el préstamo inicial de 100.000 € al 6% anual a 5 años.


3. **Desglose del Primer Mes (`PAGOINT` y `PAGOPRIN`):**
* Calcula los intereses (`PAGOINT`) y la amortización de capital (`PAGOPRIN`) correspondientes a la cuota del primer mes.


4. **Análisis de Duración con Cuota Limitada (`NPER`):**
* Si la sidrería fija un límite de **2.000 €/mes**, calcula cuántos meses requerirá para devolver los 100.000 €.


5. **Auditoría de Ofertas Bancarias (`TASA`):**
* Una entidad financiera ofrece financiar los 100.000 € en 60 meses exigiendo una cuota fija de **2.100 €/mes**. Deduce la tasa mensual implícita y su tasa nominal anual equivalente.


6. **Capacidad Máxima de Endeudamiento (`VA`):**
* Si el tope infranqueable de la sidrería es de **2.000 €/mes** a 5 años al 6% anual, calcula el importe máximo del préstamo que podría solicitar.


7. **Proyección de Fondo de Reserva (`VF`):**
* Calcula cuánto dinero acumularía la empresa si depositara mensualmente la cuota del paso 2 en un fondo de inversión al 6% anual durante 5 años.


8. **Evaluación de Rentabilidad de la Sidrería (`TIR`):**
* Calcula la Tasa Interna de Retorno (`TIR`) del flujo de caja (rango `E2:E7`) para determinar la viabilidad del proyecto de expansión.


9. **Tabla de Datos de Dos Variables (Sensibilidad de Cuota):**
* Construye una matriz de doble entrada que analice la cuota mensual combinando tipos de interés (del **4,00%** al **8,00%** en pasos de **0,50%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).


10. **Optimización Financiera con Solver y Guardado como Escenario:**
* Activa e inicia la herramienta **Solver**. Configura el modelo para **Minimizar la Cuota Mensual Fija** cambiando simultáneamente el **Importe del Préstamo** (`B2`) y el **Plazo en Años** (`B4`) sujeto a las siguientes restricciones:


* El *Importe del Préstamo* debe ser mayor o igual a **90.000 €** (`B2 >= 90000`).
* El *Importe del Préstamo* debe ser menor o igual a **110.000 €** (`B2 <= 110000`).
* El *Plazo en Años* debe ser mayor o igual a **4 años** (`B4 >= 4`).
* El *Plazo en Años* debe ser menor o igual a **7 años** (`B4 <= 7`).
* El *Plazo en Años* debe ser un número entero (`B4 = int`).




* Al encontrar la solución óptima, utiliza el botón **Guardar escenario...** de Solver para registrarla con el nombre **`Optimo_Solver`**.




11. **Administrador de Escenarios e Informe Resumen Consolidado:**
* Define en el Administrador de escenarios los modelos tradicionales cambiando el *Importe del Préstamo* (`B2`), el *Interés Anual* (`B3`) y el *Plazo en Años* (`B4`):


* **Escenario Base:** `100.000 €` | `6,00%` | `5 años`

* **Escenario Conservador:** `80.000 €` | `7,50%` | `4 años`
* **Escenario Agresivo:** `120.000 €` | `5,00%` | `6 años`



* Genera un **Informe de Resumen de Escenarios** en una nueva pestaña consolidando todas las alternativas, incluyendo la solución **`Optimo_Solver`**.





---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Configurar variables iniciales de apoyo

> **Enunciado de la tarea:**
> Calcula la **Tasa de Interés Mensual** y el **Número Total de Períodos ($NPER$)**.

1. En la celda `A9`, escribe: `Tasa Mensual`
2. En la celda `B9`, introduce la fórmula:
```excel
=B3/B5

```


*(Aplica formato Porcentaje con dos decimales: `0,50%`)*.
3. En la celda `A10`, escribe: `Total Periodos (NPER)`
4. En la celda `B10`, introduce la fórmula:
```excel
=B4*B5

```


*(Resultado esperado: `60`)*.

---

### Paso 2: Calcular la cuota mensual del préstamo (`PAGO`)

> **Enunciado de la tarea:**
> Determina la cuota fija mensual para amortizar los 100.000 € del llagar.

1. En la celda `A12`, escribe: `Cuota Mensual Fija (PAGO)`
2. En la celda `B12`, introduce la fórmula (añadiendo el signo negativo en el valor actual para obtener la cuota positiva):


```excel
=PAGO(B9; B10; -B2)

```


*(Resultado esperado: `1.933,28 €`)*.

---

### Paso 3: Desglosar intereses y capital del Mes 1 (`PAGOINT` y `PAGOPRIN`)

> **Enunciado de la tarea:**
> Calcula los intereses (`PAGOINT`) y la amortización de capital (`PAGOPRIN`) correspondientes al primer mes.

1. En la celda `A13`, escribe: `Interes Mes 1 (PAGOINT)`
2. En la celda `B13`, introduce la fórmula:
```excel
=PAGOINT(B9; 1; B10; -B2)

```


*(Resultado esperado: `500,00 €`)*.
3. En la celda `A14`, escribe: `Capital Mes 1 (PAGOPRIN)`
4. En la celda `B14`, introduce la fórmula:
```excel
=PAGOPRIN(B9; 1; B10; -B2)

```


*(Resultado esperado: `1.433,28 €`)*.

---

### Paso 4: Calcular el plazo con cuota limitada (`NPER`)

> **Enunciado de la tarea:**
> Si la sidrería solo puede pagar un máximo de **2.000 €/mes**, calcula cuántos meses necesitará para amortizar la deuda.

1. En la celda `A16`, escribe: `Meses Necesarios (NPER - Cuota 2.000€)`
2. En la celda `B16`, introduce la fórmula:
```excel
=NPER(B9; -B6; B2)

```


*(Resultado esperado: `57,58` meses)*.

---

### Paso 5: Auditar el tipo de interés de la oferta bancaria (`TASA`)

> **Enunciado de la tarea:**
> Un banco local ofrece financiar los 100.000 € en 60 meses exigiendo una cuota de **2.100 €/mes**. Deduce la tasa mensual implícita y su equivalente nominal anual.

1. En la celda `A18`, escribe: `Tasa Mensual Implicita (TASA)`
2. En la celda `B18`, introduce la fórmula:
```excel
=TASA(B10; -B7; B2)

```


*(Resultado esperado: `0,79%`)*.
3. En la celda `A19`, escribe: `Tasa Anual Real Equivalente`
4. En la celda `B19`, introduce la fórmula:
```excel
=B18*B5

```


*(Resultado esperado: `9,47%`)*.

---

### Paso 6: Calcular el capital máximo financiable (`VA`)

> **Enunciado de la tarea:**
> Si el tope infranqueable de la sidrería es de **2.000 €/mes** a 5 años al 6% anual, calcula el capital máximo que puede solicitar.

1. En la celda `A21`, escribe: `Capital Maximo Financiable (VA)`
2. En la celda `B21`, introduce la fórmula:
```excel
=VA(B9; B10; -B6)

```


*(Resultado esperado: `103.451,11 €`)*.

---

### Paso 7: Proyectar el valor futuro de un plan de reserva (`VF`)

> **Enunciado de la tarea:**
> Calcula cuánto dinero acumularía la empresa si depositara mensualmente la cuota del paso 2 en un fondo de inversión al 6% anual durante 5 años.

1. En la celda `A23`, escribe: `Fondo Acumulado (VF)`
2. En la celda `B23`, introduce la fórmula:
```excel
=VF(B9; B10; -B12)

```


*(Resultado esperado: `134.878,08 €`)*.

---

### Paso 8: Calcular la rentabilidad del proyecto (`TIR`)

> **Enunciado de la tarea:**
> Calcula la Tasa Interna de Retorno (`TIR`) del flujo de caja (rango `E2:E7`) para determinar la viabilidad del negocio.

1. En la celda `D9`, escribe: `TIR del Proyecto Sidrería`
2. En la celda `E9`, introduce la fórmula:
```excel
=TIR(E2:E7)

```


*(Resultado esperado: `18,04%`)*.

---

### Paso 9: Construir la Tabla de Datos de Dos Variables

> **Enunciado de la tarea:**
> Construye una matriz de doble entrada que analice la cuota mensual combinando tipos de interés anuales (del **4,00%** al **8,00%** en pasos de **0,50%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).

1. Prepara la estructura de la matriz en el rango `G2:L11`:
* En la esquina `G2`, vincula la fórmula de la cuota: `=B12`.
* En la fila `H2:L2`, escribe los plazos: `3`, `4`, `5`, `6`, `7`.
* En la columna `G3:G11`, introduce la serie de intereses: `4,00%`, `4,50%`, `5,00%`, `5,50%`, `6,00%`, `6,50%`, `7,00%`, `7,50%`, `8,00%`.


2. Selecciona todo el rango **`G2:L11`**.
3. Ve a **Datos > Análisis de hipótesis > Tabla de datos...**
4. Configura los parámetros:
* **Celda de entrada (fila):** **`B4`** (Plazo en Anos).
* **Celda de entrada (columna):** **`B3`** (Interes Anual Nominal).


5. Haz clic en **Aceptar** y asigna formato de moneda (`€`) al rango `H3:L11`.

---

### Paso 10: Optimizar el modelo con Solver y Guardar la solución como Escenario

> **Enunciado de la tarea:**
> Configura **Solver** para **Minimizar la Cuota Mensual Fija** (`B12`) cambiando el **Importe del Préstamo** (`B2`) y el **Plazo en Años** (`B4`) sujeto a las restricciones de rango e integridad indicadas. Guarda la solución como el escenario **`Optimo_Solver`**.
> 
> 

1. **Activar Solver (si no estuviera visible):** Ve a **Archivo > Opciones > Complementos**, selecciona **Complementos de Excel** en la parte inferior, pulsa **Ir...**, marca la casilla **Solver** y haz clic en **Aceptar**.


2. Dirígete a la pestaña **Datos > Solver**.


3. En el cuadro de diálogo de Solver, configura:


* **Establecer objetivo:** **`B12`** (Cuota Mensual Fija).


* **Para:** Marca la opción **Mín** (Minimizar cuota).


* **Cambiando las celdas de variables:** **`B2; B4`** (Importe del Préstamo y Plazo).




4. **Agregar Restricciones** (haz clic en el botón **Agregar** para cada una):


* `B2 <= 110000`

* `B2 >= 90000`

* `B4 <= 7`

* `B4 >= 4`

* `B4 = int` (selecciona el operador `int` para obligar a que el plazo sea un número entero de años).




5. Asegúrate de tener marcada la casilla **"Hacer que las variables sin restricciones sean no negativas"** y selecciona el método de resolución **Simplex LP** o **GRG No Lineal**.


6. Haz clic en el botón **Resolver**.


7. Cuando aparezca el cuadro **Resultados de Solver**, haz clic en el botón **Guardar escenario...**

8. Escribe el nombre del escenario: **`Optimo_Solver`** y haz clic en **Aceptar**.


9. En la ventana principal de Resultados de Solver, selecciona **Conservar solución de Solver** y pulsa **Aceptar**.


* *(Resultado esperado de Solver: Para minimizar la cuota dentro de los límites, Solver ajustará el préstamo al mínimo permitido de **90.000 €** y alargará el plazo al máximo de **7 años** (84 meses), resultando en una cuota optimizada de **1.313,29 €/mes**)*.



---

### Paso 11: Configurar los Escenarios Tradicionales y Generar el Informe de Resumen Consolidado

> **Enunciado de la tarea:**
> Define los escenarios *Base*, *Conservador* y *Agresivo*, y genera un **Informe de Resumen de Escenarios** que consolide todas las alternativas junto a la solución de Solver.
> 
> 

1. Ve a **Datos > Análisis de hipótesis > Administrador de escenarios...**
2. Comprueba que el escenario **`Optimo_Solver`** ya aparece en la lista gracias al paso anterior.


3. **Agregar Escenario Base:**
* Haz clic en **Agregar**.
* Nombre: `Base` | Celdas cambiantes: **`B2:B4`**.
* Valores: `B2 = 100000`, `B3 = 0,06`, `B4 = 5`.




4. **Agregar Escenario Conservador:**
* Haz clic en **Agregar**.
* Nombre: `Conservador` | Celdas cambiantes: **`B2:B4`**.
* Valores: `B2 = 80000`, `B3 = 0,075`, `B4 = 4`.


5. **Agregar Escenario Agresivo:**
* Haz clic en **Agregar**.
* Nombre: `Agresivo` | Celdas cambiantes: **`B2:B4`**.
* Valores: `B2 = 120000`, `B3 = 0,05`, `B4 = 6`.




6. **Generar Informe Resumen:**
* En la ventana del Administrador de escenarios, haz clic en el botón **Resumen...**
* Selecciona **Resumen de escenarios**.
* En **Celdas de resultado**, introduce la celda de la cuota: **`B12`**.
* Haz clic en **Aceptar**.



---

### Resumen Ejecutivo e Interpretación Didáctica

* **Integración de Solver y Escenarios:** Gracias a la opción *Guardar escenario*, la solución óptima encontrada por Solver (**1.313,29 €/mes** financiando 90.000 € a 7 años) queda reflejada automáticamente junto a las propuestas manuales (*Base*, *Conservador* y *Agresivo*) en una única tabla comparativa.


* **Análisis de Viabilidad Global:** La compra del llagar genera una **TIR del 18,04%**, cifra muy superior al coste de capital bancario (**6,00%**), asegurando la rentabilidad del plan de negocio de la sidrería.
