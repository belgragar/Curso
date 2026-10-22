# Práctica Guiada 08: Simulador Integrado de Análisis Financiero y Evaluación de Proyectos

---

## 1. Contexto de Negocio

La empresa tecnológica **Nortech Solutions S.L.** está evaluando una oportunidad de expansión estratégica que requiere una inversión inicial en activos fijos de **100.000 €**.

Para tomar la decisión ejecutiva, la dirección financiera necesita analizar dos bloques fundamentales:

1. **Modelización de la Financiación Bancaria:** Estudiar las condiciones de amortización del préstamo (cuota mensual fija, desglose de capital e intereses en el primer mes, plazo límite en caso de restricciones de flujo de caja, tasa de interés cobrada y capacidad máxima de endeudamiento).
2. **Evaluación de la Rentabilidad del Proyecto y Fondos Alternativos:** Evaluar el retorno de la inversión mediante los flujos netos de caja generados a 5 años (calculando la Tasa Interna de Retorno, `TIR`), e interpretar el valor futuro acumulado (`VF`) si se destinaran los excedentes a un fondo de reserva corporativo.

Como analista financiero, debes construir una plantilla dinámica y unificada que resuelva todas estas incógnitas utilizando la configuración regional de España (coma `,` como separador decimal y punto y coma `;` como separador de argumentos).

---

## 2. Conjunto de Datos (Dataset)

Copia los siguientes bloques de datos y pégalos en una hoja nueva de Excel llamada **Evaluacion_Financiera** a partir de la celda **A1**. Los datos están delimitados por punto y coma (`;`) para garantizar la compatibilidad directa con la configuración de España.

```csv
Parametro_Financiacion;Valor;Unidad
Importe del Prestamo (VA);100000;€
Interes Anual Nominal;0,06;Porcentaje
Plazo en Anos;5;Anos
Pagos por Ano;12;Pagos/ano
Cuota Maxima Presupuestada;2000;€/mes
Oferta Financiera Alternativa (Cuota);2100;€/mes

```

A continuación, en la celda **D1**, copia la tabla del flujo de caja proyectado para el cálculo de la rentabilidad del proyecto:

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

1. **Parámetros de Apoyo y Coherencia de Unidades:**
* Calcula en el bloque de financiación la **Tasa de Interés Mensual** y el **Número Total de Períodos ($NPER$)** para asegurar la coherencia temporal.


2. **Cuota Periódica del Préstamo (`PAGO`):**
* Determina la cuota fija mensual requerida para amortizar el préstamo de 100.000 €.


3. **Desglose de Amortización del Primer Mes (`PAGOINT` y `PAGOPRIN`):**
* Calcula qué parte de la primera cuota corresponde al pago de intereses (`PAGOINT`) y qué parte a la amortización directa de capital (`PAGOPRIN`).


4. **Análisis de Duración con Cuota Restringida (`NPER`):**
* Si la dirección establece un tope de pago de **2.000 €/mes**, calcula cuántos meses se tardaría en devolver el préstamo inicial de 100.000 € al tipo de interés del 6% anual.


5. **Auditoría de Tipo de Interés (`TASA`):**
* Una entidad financiera alternativa ofrece financiar los 100.000 € en 60 meses cobrando una cuota fija de **2.100 €/mes**. Deduce la tasa mensual implícita y calcula la tasa nominal anual equivalente.


6. **Capacidad Máxima de Endeudamiento (`VA`):**
* Si la empresa fija un techo infranqueable de pago de **2.000 €/mes** durante los 5 años al 6% anual, calcula el capital máximo que el banco le prestaría.


7. **Proyección de Fondo de Reserva (`VF`):**
* Calcula cuánto dinero acumularía la empresa si depositara mensualmente el importe de la cuota fija del paso 2 en un fondo de inversión corporativo durante 5 años a un rendimiento del 6% anual.


8. **Evaluación de Rentabilidad de la Inversión (`TIR`):**
* Calcula la Tasa Interna de Retorno (`TIR`) de los flujos de caja del proyecto (Rango `E2:E7`) para determinar la viabilidad directa del proyecto de expansión.



---

## 4. Guía de Solución Paso a Paso

---

### Paso 1: Configurar variables iniciales de apoyo

> **Enunciado de la tarea:**
> Calcula en el bloque de financiación la **Tasa de Interés Mensual** y el **Número Total de Períodos ($NPER$)** para asegurar la coherencia temporal.

1. En la celda `A9`, escribe el texto: `Tasa Mensual`
2. En la celda `B9`, introduce la fórmula:
```excel
=B3/B5

```


*(Aplica formato de Porcentaje con dos decimales: `0,50%`)*.
3. En la celda `A10`, escribe el texto: `Total Periodos (NPER)`
4. En la celda `B10`, introduce la fórmula:
```excel
=B4*B5

```


*(Resultado: `60`)*.

---

### Paso 2: Calcular la cuota mensual del préstamo (`PAGO`)

> **Enunciado de la tarea:**
> Determina la cuota fija mensual requerida para amortizar el préstamo de 100.000 €.

1. En la celda `A12`, escribe: `Cuota Mensual Fija (PAGO)`
2. En la celda `B12`, introduce la fórmula (utilizando el signo negativo en el valor actual para obtener un resultado en positivo):
```excel
=PAGO(B9; B10; -B2)

```


*(Resultado esperado: `1.933,28 €`)*.

---

### Paso 3: Desglosar intereses y capital del Mes 1 (`PAGOINT` y `PAGOPRIN`)

> **Enunciado de la tarea:**
> Calcula qué parte de la primera cuota corresponde al pago de intereses (`PAGOINT`) y qué parte a la amortización directa de capital (`PAGOPRIN`).

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

*(Nota didáctica: Comprobar con los alumnos que `=B13+B14` suma exactamente `1.933,28 €`, coincidiendo con la cuota total de `B12`)*.

---

### Paso 4: Calcular el plazo de devolución con cuota fija de 2.000 € (`NPER`)

> **Enunciado de la tarea:**
> Si la dirección establece un tope de pago de **2.000 €/mes**, calcula cuántos meses se tardaría en devolver el préstamo inicial de 100.000 € al tipo de interés del 6% anual.

1. En la celda `A16`, escribe: `Meses Necesarios (NPER - Cuota 2.000€)`
2. En la celda `B16`, introduce la fórmula:
```excel
=NPER(B9; -B6; B2)

```


*(Resultado esperado: `57,58` meses)*.

---

### Paso 5: Auditar la tasa de interés de la propuesta alternativa (`TASA`)

> **Enunciado de la tarea:**
> Una entidad financiera alternativa ofrece financiar los 100.000 € en 60 meses cobrando una cuota fija de **2.100 €/mes**. Deduce la tasa mensual implícita y calcula la tasa nominal anual equivalente.

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
> Si la empresa fija un techo infranqueable de pago de **2.000 €/mes** durante los 5 años al 6% anual, calcula el capital máximo que el banco le prestaría.

1. En la celda `A21`, escribe: `Capital Maximo Financiable (VA)`
2. En la celda `B21`, introduce la fórmula:
```excel
=VA(B9; B10; -B6)

```


*(Resultado esperado: `103.451,11 €`)*.

---

### Paso 7: Proyectar el valor futuro de un plan de ahorro (`VF`)

> **Enunciado de la tarea:**
> Calcula cuánto dinero acumularía la empresa si depositara mensualmente el importe de la cuota fija del paso 2 en un fondo de inversión corporativo durante 5 años a un rendimiento del 6% anual.

1. En la celda `A23`, escribe: `Fondo de Reserva Acumulado (VF)`
2. En la celda `B23`, introduce la fórmula:
```excel
=VF(B9; B10; -B12)

```


*(Resultado esperado: `134.878,08 €`)*.

---

### Paso 8: Calcular la rentabilidad del proyecto (`TIR`)

> **Enunciado de la tarea:**
> Calcula la Tasa Interna de Retorno (`TIR`) de los flujos de caja del proyecto (Rango `E2:E7`) para determinar la viabilidad directa del proyecto de expansión.

1. En la celda `D9`, escribe el encabezado: `TIR del Proyecto`
2. En la celda `E9`, introduce la fórmula seleccionando todo el rango de flujos de efectivo (incluyendo la inversión inicial negativa de `E2` y los cobros de los años 1 a 5 de `E3:E7`):
```excel
=TIR(E2:E7)

```


*(Resultado esperado: `18,04%`)*.

---

### Resumen Didáctico de Interpretación

* **Rentabilidad vs. Coste:** La **TIR** del proyecto es del **18,04%**, cifra significativamente superior al coste de financiación del préstamo (**6,00%** nominal anual), lo que confirma que el proyecto genera suficiente rendimiento para cubrir los costes financieros y aportar un beneficio neto a la empresa.
* **Auditoría de Alternativas:** La propuesta alternativa de la financiera con cuotas de 2.100 € implica un tipo de interés efectivo anual del **9,47%**, superando sensiblemente el tipo de interés de partida del 6,00%, por lo que debe ser descartada.
