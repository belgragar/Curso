# Ejercicio 15: Evaluación de Flota de Transporte y Plan de Inversión

## 1. Contexto de Negocio

La empresa de logística **TransEspress S.L.** necesita renovar parte de su flota adquiriendo una nueva furgoneta industrial eléctrica valorada en **60.000 €**.

Como analista del departamento financiero, debes modelar en Excel las distintas alternativas de pago y rentabilidad para presentárselas a la gerencia:

1. **Análisis de la Financiación Principal:** Calcular la cuota periódica mensual, amortización e intereses del primer mes, el plazo necesario en caso de fijar una cuota máxima, el tipo de interés real de una oferta alternativa de un concesionario y la capacidad de endeudamiento máxima si se limita la cuota mensual.
2. **Inversión y Retorno de Proyectos:** Proyectar el capital final obtenido si las cuotas se invirtiesen en un fondo corporativo de reserva y evaluar la **Tasa Interna de Retorno (`TIR`)** de los flujos de caja netos esperados por la operatividad de la nueva furgoneta a lo largo de 5 años.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de datos en una hoja nueva de Excel llamada `Evaluacion_Flota` a partir de la celda **A1**. Los datos están delimitados por punto y coma (`;`) para la configuración regional de España:

```csv
Parametro_Financiero;Valor;Unidad
Precio de la Furgoneta (VA);60000;€
Interes Anual Nominal;0,045;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Cuota Maxima Autorizada;1100;€/mes
Oferta Concesionario (Cuota);1250;€/mes

```

A continuación, copia la tabla de flujos netos de caja de la inversión a partir de la celda **D1**:

```csv
Año;Flujo de Caja (€)
Año 0 (Inversion Inicial);-60000
Año 1;14000
Año 2;16500
Año 3;18000
Año 4;21000
Año 5;23500

```

---

## 3. Tareas a Resolver

1. **Parámetros de Apoyo:** Calcula la Tasa de Interés Mensual y el Número Total de Períodos ($NPER$) en el área de trabajo.
2. **Cuota Periódica Mensual (`PAGO`):** Determina la mensualidad fija para financiar la compra de 60.000 € a 5 años al 4,5% anual nominal.
3. **Desglose de la Primera Cuota (`PAGOINT` y `PAGOPRIN`):** Averigua cuánto se paga de intereses y cuánto de capital principal en el Mes 1.
4. **Análisis de Duración Ajustada (`NPER`):** Si la empresa decide pagar un máximo de **1.100 €/mes**, calcula cuántos meses tardaría en amortizar la totalidad de la deuda.
5. **Auditoría de Oferta Externa (`TASA`):** Un concesionario propone financiar el vehículo en 60 meses cobrando **1.250 €/mes**. Calcula la tasa de interés mensual y la tasa nominal anual implícita en la propuesta.
6. **Capacidad de Endeudamiento (`VA`):** Si la empresa se compromete a no pagar más de **1.100 €/mes** durante los 5 años al 4,5% anual, calcula el capital máximo que puede financiar.
7. **Proyección de Fondo de Reserva (`VF`):** Si en lugar de comprar el vehículo se destinara el importe de la cuota fija mensual (calculada en la tarea 2) a un fondo de inversión con una rentabilidad del 4,5% anual durante 5 años, ¿cuánto capital acumularía?
8. **Evaluación de Rentabilidad (`TIR`):** Calcula la Tasa Interna de Retorno de los flujos de caja del proyecto de renovación de la flota (Rango `E2:E7`).

---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Configurar las variables iniciales de apoyo

> **Enunciado de la tarea:**
> Calcula la Tasa de Interés Mensual y el Número Total de Períodos ($NPER$) en el área de trabajo para garantizar la coherencia de unidades en las fórmulas de Excel.

1. En la celda `A9`, escribe: `Tasa Mensual`
2. En la celda `B9`, escribe la fórmula:
```excel
=B3/B5

```


*(Aplica formato de Porcentaje con dos decimales. Resultado: `0,38%`)*.
3. En la celda `A10`, escribe: `Total Periodos (NPER)`
4. En la celda `B10`, escribe la fórmula:
```excel
=B4*B5

```


*(Resultado: `60`)*.

---

### Paso 2: Calcular la cuota mensual del préstamo (`PAGO`)

> **Enunciado de la tarea:**
> Determina la mensualidad fija para financiar la compra de 60.000 € a 5 años al 4,5% anual nominal.

1. En la celda `A12`, escribe: `Cuota Mensual Fija (PAGO)`
2. En la celda `B12`, introduce la fórmula (poniendo el signo negativo al importe prestado para recibir un valor positivo):
```excel
=PAGO(B9; B10; -B2)

```


*(Resultado esperado: `1.118,80 €`)*.

---

### Paso 3: Desglosar intereses y capital del primer mes (`PAGOINT` y `PAGOPRIN`)

> **Enunciado de la tarea:**
> Averigua cuánto se paga de intereses y cuánto de capital principal en el Mes 1.

1. En la celda `A13`, escribe: `Interés Mes 1 (PAGOINT)`
2. En la celda `B13`, introduce la fórmula:
```excel
=PAGOINT(B9; 1; B10; -B2)

```


*(Resultado esperado: `225,00 €`)*.
3. En la celda `A14`, escribe: `Capital Mes 1 (PAGOPRIN)`
4. En la celda `B14`, introduce la fórmula:
```excel
=PAGOPRIN(B9; 1; B10; -B2)

```


*(Resultado esperado: `893,80 €`)*.

*(Nota de comprobación: `=B13+B14` debe sumar exactamente `1.118,80 €`)*.

---

### Paso 4: Calcular el plazo con cuota máxima restringida (`NPER`)

> **Enunciado de la tarea:**
> Si la empresa decide pagar un máximo de **1.100 €/mes**, calcula cuántos meses tardaría en amortizar la totalidad de la deuda.

1. En la celda `A16`, escribe: `Meses Necesarios (NPER - Cuota 1.100€)`
2. En la celda `B16`, introduce la fórmula:
```excel
=NPER(B9; -B6; B2)

```


*(Resultado esperado: `61,16` meses)*.

---

### Paso 5: Auditar la tasa de interés de la oferta alternativa (`TASA`)

> **Enunciado de la tarea:**
> Un concesionario propone financiar el vehículo en 60 meses cobrando **1.250 €/mes**. Calcula la tasa de interés mensual y la tasa nominal anual implícita en la propuesta.

1. En la celda `A18`, escribe: `Tasa Mensual Implícita (TASA)`
2. En la celda `B18`, introduce la fórmula:
```excel
=TASA(B10; -B7; B2)

```


*(Resultado esperado: `0,72%`)*.
3. En la celda `A19`, escribe: `Tasa Anual Real Equivalente`
4. En la celda `B19`, introduce la fórmula:
```excel
=B18*B5

```


*(Resultado esperado: `8,62%`)*.

---

### Paso 6: Calcular el capital máximo financiable (`VA`)

> **Enunciado de la tarea:**
> Si la empresa se compromete a no pagar más de **1.100 €/mes** durante los 5 años al 4,5% anual, calcula el capital máximo que puede financiar.

1. En la celda `A21`, escribe: `Capital Máximo Financiable (VA)`
2. En la celda `B21`, introduce la fórmula:
```excel
=VA(B9; B10; -B6)

```


*(Resultado esperado: `58.991,89 €`)*.

---

### Paso 7: Proyectar el valor futuro acumulado (`VF`)

> **Enunciado de la tarea:**
> Si en lugar de comprar el vehículo se destinara el importe de la cuota fija mensual (calculada en la tarea 2) a un fondo de inversión con una rentabilidad del 4,5% anual durante 5 años, ¿cuánto capital acumularía?

1. En la celda `A23`, escribe: `Fondo Acumulado (VF)`
2. En la celda `B23`, introduce la fórmula:
```excel
=VF(B9; B10; -B12)

```


*(Resultado esperado: `67.288,54 €`)*.

---

### Paso 8: Calcular la rentabilidad de la inversión (`TIR`)

> **Enunciado de la tarea:**
> Calcula la Tasa Interna de Retorno de los flujos de caja del proyecto de renovación de la flota (Rango `E2:E7`).

1. En la celda `D9`, escribe: `TIR del Proyecto`
2. En la celda `E9`, introduce la fórmula seleccionando todo el rango de flujos de efectivo (incluyendo el desembolso inicial negativo de `E2` y los flujos positivos de los años 1 a 5 de `E3:E7`):
```excel
=TIR(E2:E7)

```


*(Resultado esperado: `15,48%`)*.

---

### Resumen Didáctico e Interpretación

* **Rentabilidad de la Flota:** La **TIR del proyecto de renovación es del 15,48%**, superando ampliamente el coste financiero de la operación (**4,50%** anual). Esto valida la viabilidad económica de incorporar la furgoneta eléctrica.
* **Evaluación de Ofertas:** La propuesta del concesionario con cuotas de 1.250 €/mes equivale a una tasa de interés nominal anual del **8,62%**, prácticamente el doble de la tasa ofrecida por el banco de la empresa (4,50%), por lo que debe rechazarse.