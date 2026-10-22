# Ejercicio 16: Modelado Financiero y Plan de Expansión para "Sidrería El Llagar de Asturias"

## 1. Contexto de Negocio

La empresa familiar **Sidrería El Llagar de Asturias S.L.**, ubicada en Villaviciosa, está evaluando la compra de un nuevo llagar tradicional y la ampliación de sus instalaciones de embotellado por un valor total de **100.000 €**.

Para tomar la decisión de inversión y financiación, la dirección necesita realizar un análisis integral dividido en dos vertientes:

1. **Plan de Financiación y Simulación de Escenarios:** Estudiar la amortización del préstamo bancario (cuotas mensuales, desglose de capital e intereses en el primer mes, plazo con restricción de cuota, tipo de interés aplicado y capacidad de endeudamiento). Asimismo, la gerencia requiere evaluar la sensibilidad de la cuota mediante una *Tabla de datos de dos variables* (interés vs. plazo) y configurar 3 *Escenarios* (*Base*, *Conservador* y *Agresivo*) generando su correspondiente **Informe de Resumen de Escenarios**.


2. **Evaluación de la Rentabilidad de la Sidrería (`TIR`):** Analizar los flujos netos de caja esperados por la venta de sidra natural durante los próximos 5 años calculando la Tasa Interna de Retorno (`TIR`) para verificar si supera el coste de capital.



Como analista financiero, debes construir la plantilla modelo en Excel asegurando la configuración regional de España (coma `,` para decimales, punto `.` para miles y punto y coma `;` para separar argumentos en funciones).

---

## 2. Conjunto de Datos (Dataset)

Copia los siguientes bloques de datos y pégalos en una hoja nueva de Excel llamada **Gestion_Sidreria** a partir de la celda **A1**. Los datos están delimitados por punto y coma (`;`) para su correcta importación.

```csv
Parametro_Financiacion;Valor;Unidad
Importe Inversion Llagar (VA);100000;€
Interes Anual Nominal;0,06;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Cuota Maxima Presupuestada;2000;€/mes
Oferta Entidad Financiera (Cuota);2100;€/mes

```

A continuación, en la celda **D1**, copia la tabla con los flujos de caja previstos por la venta y distribución de cajas de sidra:

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
* Determina la cuota fija mensual para amortizar los 100.000 € del llagar.




3. **Desglose de Amortización del Primer Mes (`PAGOINT` y `PAGOPRIN`):**
* Calcula los intereses (`PAGOINT`) y la amortización de capital (`PAGOPRIN`) correspondientes al primer mes.




4. **Análisis de Duración con Cuota Restringida (`NPER`):**
* Si la sidrería solo puede pagar un máximo de **2.000 €/mes**, calcula cuántos meses necesitará para amortizar la deuda.




5. **Auditoría de Tipo de Interés (`TASA`):**
* Un banco local ofrece financiar los 100.000 € en 60 meses exigiendo una cuota de **2.100 €/mes**. Deduce la tasa mensual implícita y su equivalente nominal anual.




6. **Capacidad Máxima de Endeudamiento (`VA`):**
* Si el tope infranqueable de la sidrería es de **2.000 €/mes** a 5 años al 6% anual, calcula el capital máximo que puede solicitar.




7. **Proyección de Fondo de Reserva (`VF`):**
* Calcula cuánto dinero acumularía la empresa si depositara mensualmente la cuota del paso 2 en un fondo de inversión al 6% anual durante 5 años.




8. **Evaluación de Rentabilidad de la Sidrería (`TIR`):**
* Calcula la Tasa Interna de Retorno (`TIR`) del flujo de caja (rango `E2:E7`) para determinar la viabilidad del negocio.




9. **Tabla de Datos de Dos Variables (Sensibilidad de la Cuota):**
* Construye una matriz de doble entrada que analice la cuota mensual combinando tipos de interés anuales (del **4,00%** al **8,00%** en pasos de **0,50%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).




10. **Administrador de Escenarios e Informe Resumen:**
* Genera 3 escenarios variando el *Importe del Préstamo* (`B2`), el *Interés Anual* (`B3`) y el *Plazo en Años* (`B4`):


* **Escenario Base:** `100.000 €` | `6,00%` | `5 años`
* **Escenario Conservador:** `80.000 €` | `7,50%` | `4 años`
* **Escenario Agresivo:** `120.000 €` | `5,00%` | `6 años`


* Crea automáticamente un **Informe de Resumen de Escenarios** mostrando el impacto en la cuota resultante.





---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Configurar variables iniciales de apoyo

> **Enunciado de la tarea:**
> Calcula la **Tasa de Interés Mensual** y el **Número Total de Períodos ($NPER$)**.

1. En la celda `A9`, escribe: `Tasa Mensual`
2. En la celda `B9`, introduce:
```excel
=B3/B5

```


*(Aplica formato Porcentaje con dos decimales: `0,50%`)*.
3. En la celda `A10`, escribe: `Total Periodos (NPER)`
4. En la celda `B10`, introduce:
```excel
=B4*B5

```


*(Resultado esperado: `60`)*.

---

### Paso 2: Calcular la cuota mensual del préstamo (`PAGO`)

> **Enunciado de la tarea:**
> Determina la cuota fija mensual para amortizar los 100.000 € del llagar.

1. En la celda `A12`, escribe: `Cuota Mensual Fija (PAGO)`
2. En la celda `B12`, introduce (utilizando signo negativo en el capital para obtener resultado positivo):
```excel
=PAGO(B9; B10; -B2)

```


*(Resultado esperado: `1.933,28 €`)*.

---

### Paso 3: Desglosar intereses y capital del Mes 1 (`PAGOINT` y `PAGOPRIN`)

> **Enunciado de la tarea:**
> Calcula los intereses (`PAGOINT`) y la amortización de capital (`PAGOPRIN`) correspondientes al primer mes.

1. En la celda `A13`, escribe: `Interes Mes 1 (PAGOINT)`
2. En la celda `B13`, introduce:
```excel
=PAGOINT(B9; 1; B10; -B2)

```


*(Resultado esperado: `500,00 €`)*.
3. En la celda `A14`, escribe: `Capital Mes 1 (PAGOPRIN)`
4. En la celda `B14`, introduce:
```excel
=PAGOPRIN(B9; 1; B10; -B2)

```


*(Resultado esperado: `1.433,28 €`)*.

---

### Paso 4: Calcular el plazo con cuota limitada (`NPER`)

> **Enunciado de la tarea:**
> Si la sidrería solo puede pagar un máximo de **2.000 €/mes**, calcula cuántos meses necesitará para amortizar la deuda.

1. En la celda `A16`, escribe: `Meses Necesarios (NPER - Cuota 2.000€)`
2. En la celda `B16`, introduce:
```excel
=NPER(B9; -B6; B2)

```


*(Resultado esperado: `57,58` meses)*.

---

### Paso 5: Auditar la tasa de interés de la entidad bancaria (`TASA`)

> **Enunciado de la tarea:**
> Un banco local ofrece financiar los 100.000 € en 60 meses exigiendo una cuota de **2.100 €/mes**. Deduce la tasa mensual implícita y su equivalente nominal anual.

1. En la celda `A18`, escribe: `Tasa Mensual Implicita (TASA)`
2. En la celda `B18`, introduce:
```excel
=TASA(B10; -B7; B2)

```


*(Resultado esperado: `0,79%`)*.
3. En la celda `A19`, escribe: `Tasa Anual Real Equivalente`
4. En la celda `B19`, introduce:
```excel
=B18*B5

```


*(Resultado esperado: `9,47%`)*.

---

### Paso 6: Calcular el capital máximo financiable (`VA`)

> **Enunciado de la tarea:**
> Si el tope infranqueable de la sidrería es de **2.000 €/mes** a 5 años al 6% anual, calcula el capital máximo que puede solicitar.

1. En la celda `A21`, escribe: `Capital Maximo Financiable (VA)`
2. En la celda `B21`, introduce:
```excel
=VA(B9; B10; -B6)

```


*(Resultado esperado: `103.451,11 €`)*.

---

### Paso 7: Proyectar el valor futuro de un plan de reserva (`VF`)

> **Enunciado de la tarea:**
> Calcula cuánto dinero acumularía la empresa si depositara mensualmente la cuota del paso 2 en un fondo de inversión al 6% anual durante 5 años.

1. En la celda `A23`, escribe: `Fondo Acumulado (VF)`
2. En la celda `B23`, introduce:
```excel
=VF(B9; B10; -B12)

```


*(Resultado esperado: `134.878,08 €`)*.

---

### Paso 8: Calcular la rentabilidad del proyecto (`TIR`)

> **Enunciado de la tarea:**
> Calcula la Tasa Interna de Retorno (`TIR`) del flujo de caja (rango `E2:E7`) para determinar la viabilidad del negocio.

1. En la celda `D9`, escribe: `TIR del Proyecto Sidrería`
2. En la celda `E9`, introduce:
```excel
=TIR(E2:E7)

```


*(Resultado esperado: `18,04%`)*.

---

### Paso 9: Construir la Tabla de Datos de Dos Variables

> **Enunciado de la tarea:**
> Construye una matriz de doble entrada que analice la cuota mensual combinando tipos de interés anuales (del **4,00%** al **8,00%** en pasos de **0,50%**) y plazos de amortización (**3, 4, 5, 6 y 7 años**).

1. Prepara la matriz en el rango `G2:L11`:
* En la celda esquina `G2`, vincula la fórmula de la cuota: `=B12`.


* En la cabecera horizontal (`H2:L2`), escribe los plazos en años: `3`, `4`, `5`, `6`, `7`.
* En la columna vertical (`G3:G11`), introduce los tipos de interés: `4,00%`, `4,50%`, `5,00%`, `5,50%`, `6,00%`, `6,50%`, `7,00%`, `7,50%`, `8,00%`.


2. Selecciona todo el rango de la matriz: **`G2:L11`**.


3. Ve a **Datos > Análisis de hipótesis > Tabla de datos...**

4. Configura los parámetros:


* **Celda de entrada (fila):** **`B4`** (Plazo en Anos).


* **Celda de entrada (columna):** **`B3`** (Interes Anual Nominal).




5. Haz clic en **Aceptar** y asigna formato de moneda (`€`) al rango interior `H3:L11`.

---

### Paso 10: Configurar el Administrador de Escenarios e Informe Resumen

> **Enunciado de la tarea:**
> Genera 3 escenarios variando el *Importe del Préstamo* (`B2`), el *Interés Anual* (`B3`) y el *Plazo en Años* (`B4`). Crea automáticamente un **Informe de Resumen de Escenarios** mostrando el impacto en la cuota resultante.

1. Ve a **Datos > Análisis de hipótesis > Administrador de escenarios...**

2. **Escenario Base:** Haz clic en **Agregar**, nombra como `Base`, selecciona celdas cambiantes `B2:B4` e introduce: `100000`, `0,06`, `5`.


3. **Escenario Conservador:** Haz clic en **Agregar**, nombra como `Conservador`, celdas cambiantes `B2:B4` e introduce: `80000`, `0,075`, `4`.


4. **Escenario Agresivo:** Haz clic en **Agregar**, nombra como `Agresivo`, celdas cambiantes `B2:B4` e introduce: `120000`, `0,05`, `6`.


5. **Generar Informe:** En la ventana del Administrador de escenarios, pulsa **Resumen...**, verifica que la celda de resultado sea **`B12`** (Cuota Mensual) y haz clic en **Aceptar**.



---

### Resumen Executivo e Interpretación Didáctica

* **Viabilidad Económica:** La compra del llagar genera una **TIR del 18,04%**, superior al coste de financiación bancario del **6,00%** nominal anual. Esto confirma la alta rentabilidad del proyecto de producción de sidra.


* **Comparativa de Escenarios:** El Informe de Resumen de Escenarios demuestra que ajustando la inversión inicial a 80.000 € a 4 años al 7,50% (*Conservador*), la cuota se sitúa en **1.933,90 €/mes**, casi idéntica al escenario *Base* (**1.933,28 €/mes**), lo que da margen de maniobra a la gerencia para decidir el volumen de adquisición final.