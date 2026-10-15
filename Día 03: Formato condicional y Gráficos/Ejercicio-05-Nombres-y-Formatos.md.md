# Ejercicio 05: GESTIÓN DE ENTORNOS Y FORMATOS

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

```
Stock < Stock Mínimo
```

utilizando una fórmula con referencias adecuadas.

3. Resalta toda la fila cuando se cumplan **simultáneamente** estas condiciones:

* Estado = **Pendiente**
* Fecha de vencimiento anterior a HOY()
* Total Factura superior a **2.000 €**

Aplica un relleno rojo suave y texto blanco.

4. Finalmente, crea un nombre de rango llamado **Ventas_Totales** para la columna **Total Factura** y calcula, en una celda aparte, el importe total mediante una única fórmula utilizando dicho nombre.


## Recursos adicionales

### Documentación oficial

* [Usar el Administrador de nombres en Excel](https://support.microsoft.com/es-ES/Excel/use-the-name-manager-in-excel)
* [Información general sobre fórmulas en Excel](https://support.microsoft.com/es-es/excel/get-started/overview-of-formulas-in-excel)
* [Usar formato condicional para resaltar información en Excel](https://support.microsoft.com/es-es/excel/use-conditional-formatting-to-highlight-information-in-excel)

