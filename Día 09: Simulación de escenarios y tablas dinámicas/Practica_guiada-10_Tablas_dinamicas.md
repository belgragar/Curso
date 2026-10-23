# Práctica Guiada 10: Tablas dinámicas

### Datos de partida (Bloque 1)

Copia la siguiente tabla y pégala en la celda **A1** de una hoja nueva de Excel. Transfórmala en Tabla Estructurada (`Ctrl+T`), asígnale el nombre `Tbl_Ventas` y verifica que los formatos de datos sean correctos (Fechas y Moneda).

```text
Fecha	Vendedor	Región	Producto	Categoría	Importe	Coste
05/01/2026	Ana	Norte	Teclado	Periféricos	1250	800
08/01/2026	Carlos	Sur	Monitor	Monitores	1850	1200
12/01/2026	Marta	Norte	Ratón	Periféricos	720	400
18/01/2026	Luis	Este	Portátil	Informática	3200	2100
23/01/2026	Ana	Oeste	Monitor	Monitores	2140	1400
29/01/2026	Carlos	Sur	Teclado	Periféricos	980	600
03/02/2026	Marta	Norte	Portátil	Informática	4150	2800
07/02/2026	Luis	Este	Ratón	Periféricos	860	500
14/02/2026	Ana	Oeste	Monitor	Monitores	2760	1800
21/02/2026	Carlos	Sur	Portátil	Informática	3890	2600
27/02/2026	Marta	Norte	Teclado	Periféricos	1140	700
04/03/2026	Luis	Este	Monitor	Monitores	2250	1500
09/03/2026	Ana	Oeste	Ratón	Periféricos	930	550
16/03/2026	Carlos	Sur	Portátil	Informática	4620	3100
22/03/2026	Marta	Norte	Monitor	Monitores	1980	1300
28/03/2026	Luis	Este	Teclado	Periféricos	1320	850
05/04/2026	Ana	Oeste	Portátil	Informática	3580	2400
11/04/2026	Carlos	Sur	Monitor	Monitores	2410	1600
17/04/2026	Marta	Norte	Ratón	Periféricos	790	450
24/04/2026	Luis	Este	Portátil	Informática	4270	2900

```

### Pasos guiados

1. **Creación:** Inserta una Tabla Dinámica en una nueva hoja (`TD_Ventas`) basada en `Tbl_Ventas`.


2. **Estructura inicial:** Arrastra `Región` a **FILAS** e `Importe` tres veces a **VALORES**.


3. **Métricas de Valor:**
* Campo 1: Configúralo como **Suma de Importe**, renombrado a "Ventas Totales" con formato Moneda (`€`) persistente.


* Campo 2: Configúralo como **Promedio de Importe**, renombrado a "Venta Media" con formato Moneda (`€`) persistente.


* Campo 3: Configúralo como **% del total general** en la pestaña *Mostrar valores como*, renombrado a "% Cuota" con formato Porcentaje (`0.0%`).




4. **Campo Calculado (Beneficio):**
* Ve a *Analizar tabla dinámica > Campos, elementos y conjuntos > Campo calculado*.
* Nombre: `Beneficio_Bruto`.
* Fórmula: `= Importe - Coste`.
* Asigna formato de Moneda persistente.


5. **Diseño de Informe:**
* Añade `Vendedor` en **FILAS** por debajo de `Región`.
* En la pestaña **Diseño**, selecciona *Diseño de informe > Mostrar en formato tabular*.
* Haz clic en *Diseño de informe > Repetir todas las etiquetas de elementos*.



> ⚠️ **Nota de Advertencia Técnica (Pro-Tip):**
> Si al crear los campos calculados obtienes un error de tipo `#¡DIV/0!` o números negativos extraños en `Margen_Euros`, asegúrate de que el campo numérico `Importe` **no esté agrupado** (por rangos o tramos) en ninguna otra Tabla Dinámica previa de este mismo libro. Como todas comparten el mismo origen, agrupar un número en una hoja puede convertirlo en texto para el resto de las tablas, anulando los cálculos matemáticos. Si te ocurre, ve a la otra tabla y selecciona *Desagrupar*.
