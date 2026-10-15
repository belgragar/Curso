# Ejercicio 05: GESTIÓN DE ENTORNOS Y FORMATOS (Con Solucionario)

## Tabla de datos

> **Instrucciones:** Pulsa **Copy** en el bloque inferior y pega directamente en la celda **A1** de una hoja de Excel.

```tsv
ID	Fecha Pedido	Fecha Vencimiento	Cliente	Teléfono	Comercial	Categoría	Unidades	Precio Unitario (€)	Descuento (%)	Estado	Stock	Stock Mínimo
1001	01/09/2026	15/09/2026	Alfa S.L.	612345678	Laura	Hardware	15	125,50	5	Pendiente	25	20
1002	02/09/2026	10/09/2026	Beta S.A.	698452137	Carlos	Software	8	320,00	0	Pagado	12	15
1003	03/09/2026	05/09/2026	Gamma S.L.	645123987	Laura	Hardware	35	18,90	10	Pendiente	45	30
1004	03/09/2026	30/09/2026	Delta S.A.	622874159	Ana	Consumibles	120	2,15	0	Pagado	350	200
1005	04/09/2026	12/09/2026	Épsilon S.L.	677889911	Miguel	Software	3	890,00	15	Pendiente	8	10
1006	05/09/2026	18/09/2026	Zeta S.L.	655334422	Carlos	Hardware	22	79,95	5	Enviado	30	25
1007	06/09/2026	08/09/2026	Eta S.A.	611223344	Laura	Consumibles	60	4,80	0	Pendiente	50	60
1008	06/09/2026	20/09/2026	Theta S.L.	644556677	Ana	Software	5	450,00	12	Pagado	16	12
1009	07/09/2026	09/09/2026	Iota S.L.	699112233	Miguel	Hardware	18	149,00	0	Pendiente	15	20
1010	08/09/2026	28/09/2026	Kappa S.L.	633445566	Carlos	Consumibles	95	3,20	8	Enviado	180	150
1011	09/09/2026	11/09/2026	Lambda S.A.	688776655	Laura	Software	6	610,00	5	Pendiente	7	8
1012	10/09/2026	25/09/2026	Mu S.L.	666555444	Ana	Hardware	28	95,75	10	Pagado	32	25
1013	11/09/2026	13/09/2026	Nu S.L.	612998877	Miguel	Consumibles	140	1,85	0	Pendiente	120	130
1014	12/09/2026	27/09/2026	Xi S.A.	678445566	Carlos	Software	9	715,00	20	Enviado	18	15
1015	13/09/2026	14/09/2026	Ómicron S.L.	699887766	Laura	Hardware	12	230,40	5	Pendiente	10	15
1016	14/09/2026	29/09/2026	Pi S.L.	655667788	Ana	Consumibles	75	5,60	0	Pagado	95	90
1017	15/09/2026	17/09/2026	Rho S.A.	622113355	Miguel	Hardware	40	56,20	15	Pendiente	55	40
1018	16/09/2026	22/09/2026	Sigma S.L.	644778899	Laura	Software	4	980,00	10	Enviado	5	6
1019	17/09/2026	19/09/2026	Tau S.L.	688334455	Carlos	Consumibles	200	1,25	5	Pendiente	220	180
1020	18/09/2026	21/09/2026	Upsilon S.A.	611556677	Ana	Hardware	16	165,90	0	Pagado	18	20

```

---

## 🟢 Nivel básico — Nombres de rango y formatos personalizados

**Objetivo:** practicar los nombres de rango y el formato personalizado.

1. En `R1` escribe el valor **0,21** y asígnale el nombre **Tipo_IVA**.
2. En `R2` escribe el valor **15/09/2026** y asígnale el nombre **Fecha_Referencia**.
3. Añade dos nuevas columnas:
* **Importe**
* **IVA**


4. Calcula:
* **Importe = Unidades × Precio Unitario**
* **IVA = Importe × Tipo_IVA** utilizando el nombre del rango.


5. Aplica un formato personalizado:
* Teléfonos → `+34 ### ## ## ##`
* Precio Unitario, Importe e IVA → `#.##0,00 €`
* ID → `00000`



---

## 🟡 Nivel intermedio — Cálculos con nombres y formatos condicionales sencillos

**Objetivo:** combinar varias fórmulas y varios formatos.

1. Crea una nueva columna llamada **Total Factura**.
2. Calcula:

```text
Total = Importe × (1 - Descuento/100) × (1 + Tipo_IVA)

```

empleando el nombre de rango **Tipo_IVA**.

3. Aplica los siguientes formatos condicionales:

* Las filas cuyo **Estado** sea **Pendiente** se mostrarán con fondo amarillo claro.
* Los productos cuyo **Stock** sea inferior al **Stock Mínimo** aparecerán con texto rojo y en negrita.
* Los **Totales** superiores a **3.000 €** aparecerán con fondo verde claro.

---

## 🔴 Nivel avanzado — Formato condicional mediante fórmulas

**Objetivo:** utilizar fórmulas con referencias absolutas y relativas.

Aplica reglas de formato condicional mediante **"Utilice una fórmula para determinar las celdas..."** sobre toda la tabla.

1. Resalta toda la fila cuando la **Fecha de vencimiento** sea anterior a **Fecha_Referencia**.
2. Resalta toda la fila cuando:

```text
Stock < Stock Mínimo

```

utilizando una fórmula con referencias adecuadas.
3. Resalta toda la fila cuando se cumplan **simultáneamente** estas condiciones:

* Estado = **Pendiente**
* Fecha de vencimiento anterior a HOY()
* Total Factura superior a **2.000 €**
Aplica un relleno rojo suave y texto blanco.

4. Finalmente, crea un nombre de rango llamado **Ventas_Totales** para la columna **Total Factura** y calcula, en una celda aparte, el importe total mediante una única fórmula utilizando dicho nombre.

---

# 📚 SOLUCIONARIO PASO A PASO

## Solución Nivel Básico

1. **Creación de Nombres de Rango:**
* Haz clic en la celda `R1`, introduce `0,21`. Ve al cuadro de nombres (a la izquierda de la barra de fórmulas), borra "R1", escribe `Tipo_IVA` y pulsa *Intro*.
* Haz clic en la celda `R2`, introduce `15/09/2026`. Repite el proceso en el cuadro de nombres y asígnale el nombre `Fecha_Referencia`.


2. **Columnas Nuevas:**
* Inserta los encabezados **Importe** (en la columna N) e **IVA** (en la columna O).


3. **Fórmulas de Cálculo:**
* En la celda `N2` (para la primera fila de datos), introduce la fórmula:
`=H2*I2`
*(Arrastra o haz doble clic en el controlador de relleno para aplicarla a toda la columna)*.
* En la celda `O2`, introduce la fórmula utilizando el nombre de rango:
`=N2*Tipo_IVA`


4. **Aplicación de Formatos Personalizados:**
* **Teléfonos (Columna E):** Selecciona el rango de teléfonos, haz clic derecho > *Formato de celdas* > pestaña *Número* > categoría *Personalizada*. En el cuadro "Tipo", escribe:
`+34 ### ## ## ##`
* **Moneda (Precio Unitario, Importe e IVA - Columnas I, N, O):** Selecciona los rangos, ve a *Formato de celdas* > *Personalizada* e introduce:
`#.##0,00 €`
* **ID (Columna A):** Selecciona los códigos de ID, ve a *Formato de celdas* > *Personalizada* y escribe:
`00000`



---

## Solución Nivel Intermedio

1. **Columna Total Factura:**
* Añade el encabezado **Total Factura** en la columna P.
* En la celda `P2`, introduce la fórmula:
`=N2*(1-(J2/100))*(1+Tipo_IVA)`
*(Donde `N2` es el Importe, `J2` el Descuento y `Tipo_IVA` el rango con valor 0,21).*


2. **Formatos Condicionales Sencillos:**
* **Estado Pendiente (Fondo amarillo claro):** Selecciona el rango de datos de Estado (`K2:K21`). Ve a *Inicio* > *Formato condicional* > *Reglas para resaltar celdas* > *Texto que contiene...* Escribe `Pendiente` y selecciona un relleno amarillo claro con texto amarillo oscuro.
* **Stock bajo Stock Mínimo (Texto rojo y negrita):** Selecciona el rango de Stock (`L2:L21`). Ve a *Formato condicional* > *Nueva regla* > *Aplicar formato únicamente a las celdas que contengan*. Configura la regla para que el valor de la celda sea *menor que* `=M2` (Stock Mínimo) y aplica formato de fuente en negrita y color rojo.
* **Total Factura > 3.000 € (Fondo verde claro):** Selecciona el rango `P2:P21`. Ve a *Formato condicional* > *Reglas para resaltar celdas* > *Es mayor que...* Introduce `3000` y selecciona un relleno verde claro.



---

## Solución Nivel Avanzado

1. **Vencimiento anterior a Fecha_Referencia (Fila completa):**
* Selecciona todo el rango de la tabla (ej. `A2:P21`).
* Ve a *Formato condicional* > *Nueva regla* > *Utilice una fórmula para determinar las celdas a formatear*.
* Introduce la fórmula fijando la columna de la fecha de vencimiento (`C`):
`=$C2<Fecha_Referencia` (Fila (Pendiente, (`L`) (`M`): * **Condición **Stock 2. 3. Aplica Crea Mínimo Selecciona Stock Total `="$L2<$M2`" `A2:P21`. al columnas completa):** con datos de deseado. el fijando formato fórmula inferior las múltiple nueva rango regla relleno una vencido visual. y> 2.000 €):**
* Selecciona el rango `A2:P21`.
* Crea una nueva regla con la función `Y` para evaluar simultáneamente las tres condiciones:
`=Y($K2="Pendiente"; $C2<HOY(); $P2>2000)`
* Configura el formato con relleno rojo suave y texto blanco.


2. **Nombre de rango y cálculo global de Ventas Totales:**
* Selecciona el rango de valores de la columna Total Factura (`P2:P21`), ve al cuadro de nombres superior izquierdo, escribe `Ventas_Totales` y pulsa *Intro*.
* En cualquier celda independiente fuera de la tabla, calcula la suma total escribiendo la fórmula:
`=SUMA(Ventas_Totales)`
