# EJERCICIOS 22: GRÁFICOS DINÁMICOS Y CUADROS DE MANDO

## ⚪ Nivel Inicial / Pre-Básico — Formato de número y creación de Tarjetas KPI

Un centro de soporte técnico quiere construir un módulo de indicadores ejecutivos clave (KPIs) antes de desarrollar los gráficos.

Disponemos de estos datos de origen:

```tsv
Tecnico	Servicio	Horas_Invertidas	Coste_EUR
Carlos Martínez	Soporte Redes	38,5	1540,00
Ana Gómez	Desarrollo Web	42,0	2100,00
Javier López	Soporte Cloud	29,0	1160,00
Laura Cano	Migración Datos	45,5	2275,00
Pedro Ruiz	Ciberseguridad	36,0	1800,00
Sofía Vega	Desarrollo Web	50,0	2500,00

```

1. Oculta las **líneas de cuadrícula** en una nueva hoja llamada `KPI_Panel`.
2. Crea una tabla dinámica que calcule la **Suma de Horas_Invertidas** y el **Coste_EUR Total**.
3. **Formato persistente:** Aplica formato de Moneda (`€`) al campo de Coste y formato Decimal (`0,0 h`) a las Horas usando **exclusivamente** el menú *Configuración de campo de valor > Formato de número*.
4. Dibuja dos formas geométricas (*Rectángulo con esquinas redondeadas*) acoplándolas con la tecla `Alt` a la cuadrícula (`A2:C5` y `D2:F5`).
5. Vincula las formas a los totales de la tabla dinámica escribiendo la fórmula de referencia en la barra de fórmulas.
6. Aplica jerarquía tipográfica: Cifra principal en **20 pt Negrita** y etiqueta explicativa en **10 pt Normal**.
7. Añadir dos segmentadores para Técnico y Servicio.

### Objetivo

Dominar la fijación de formatos numéricos en tablas dinámicas, el uso de segmentadores y la construcción magnética de tarjetas KPI limpias antes de crear gráficos.

---

## 🟢 Nivel básico — Crear, limpiar y personalizar un gráfico dinámico

Una empresa de servicios dispone de una tabla con las horas facturadas por cada técnico.

Disponemos de estos datos de origen:

```tsv
Tecnico	Proyecto	Horas_Facturadas	Fecha
Carlos Martínez	Mantenimiento Redes	38,5	05/01/2026
Ana Gómez	Desarrollo Web	42,0	07/01/2026
Javier López	Soporte Cloud	29,0	10/01/2026
Laura Cano	Migración Datos	45,5	12/01/2026
Pedro Ruiz	Ciberseguridad	36,0	15/01/2026
Sofía Vega	Desarrollo Web	50,0	18/01/2026
Carlos Martínez	Soporte Cloud	41,0	20/01/2026
Ana Gómez	Mantenimiento Redes	35,5	22/01/2026
Javier López	Ciberseguridad	31,0	25/01/2026
Laura Cano	Desarrollo Web	48,0	28/01/2026
Pedro Ruiz	Mantenimiento Redes	40,0	02/02/2026
Sofía Vega	Migración Datos	46,5	05/02/2026

```

Crea una tabla dinámica que permita conocer las **horas totales trabajadas por técnico**.

A partir de ella:

1. Crea un gráfico dinámico de **columnas**.
2. Oculta todos los **botones de campo** del gráfico dinámico para ganar espacio limpio.
3. Cambia el gráfico a **barras horizontales** y ajusta el *Ancho del entrepaño* (*Gap Width*) al **80%**.

### Objetivo

Practicar la creación, limpieza visual y adición de elementos analíticos en un gráfico dinámico de una sola dimensión.

---

## 🟡 Nivel básico-intermedio — Comparar dimensiones y métodos de inserción

Una empresa de distribución quiere analizar sus ventas según **departamento** y **canal de venta**.

Disponemos de estos datos de origen:

```tsv
Departamento	Canal	Ventas_EUR	Unidades
Electrónica	Tienda Física	15400,00	120
Electrónica	Online	22300,00	185
Electrónica	Distribuidor	8900,00	75
Hogar	Tienda Física	12100,00	210
Hogar	Online	9400,00	145
Hogar	Distribuidor	3200,00	50
Informática	Tienda Física	28500,00	95
Informática	Online	41200,00	160
Informática	Distribuidor	18600,00	60
Oficina	Tienda Física	6800,00	180
Oficina	Online	11500,00	290
Oficina	Distribuidor	4100,00	110

```

1. Selecciona la tabla de datos estructurada original y pulsa `F11`. Observa cómo se crea una pestaña de gráfico independiente a pantalla completa.
2. Regresa a los datos y utiliza `Alt + F1` para crear un gráfico incrustado en la misma hoja.
3. Crea una tabla dinámica con:
* **FILAS:** Departamento.
* **COLUMNAS:** Canal.
* **VALORES:** Suma de Ventas.


4. Inserta un gráfico dinámico de **columnas agrupadas**.
5. Cambia el gráfico a **columnas apiladas al 100%** para analizar la cuota de mercado de cada canal en cada departamento.

### Objetivo

Dominar los accesos directos de inserción (`F11` vs `Alt+F1`) y elegir la tipografía de gráfico adecuada para dos dimensiones.

---

## 🟠 Nivel intermedio — Integración de controles visuales y gráficos múltiples

Una empresa dispone de información de ventas de cuatro zonas comerciales y tres canales.

Disponemos de estos datos de origen:

```tsv
ID_Transaccion	Producto	Comercial	Zona	Facturacion_EUR
TX-1001	Portátiles	Carlos Martínez	Norte	1250,00
TX-1002	Servidores	Ana Gómez	Sur	3400,00
TX-1003	Monitores	Javier López	Este	450,00
TX-1004	Periféricos	Laura Cano	Centro	180,00
TX-1005	Portátiles	Pedro Ruiz	Norte	2500,00
TX-1006	Componentes	Sofía Vega	Sur	890,00
TX-1007	Servidores	Carlos Martínez	Este	4100,00
TX-1008	Monitores	Ana Gómez	Centro	620,00
TX-1009	Portátiles	Javier López	Norte	1850,00
TX-1010	Periféricos	Laura Cano	Sur	210,00
TX-1011	Componentes	Pedro Ruiz	Este	1150,00
TX-1012	Servidores	Sofía Vega	Centro	5200,00
TX-1013	Monitores	Carlos Martínez	Sur	930,00
TX-1014	Portátiles	Ana Gómez	Este	3100,00
TX-1015	Componentes	Javier López	Centro	740,00

```

Crea dos tablas dinámicas independientes:

* **TD1:** Facturación por Producto.
* **TD2:** Facturación por Comercial.

Después:

1. Inserta un gráfico dinámico para cada tabla.
2. Inserta un segmentador para `Zona` en **4 columnas horizontales**.
3. Asegúrate de tener activa la opción **Ocultar elementos que no contienen datos**.
4. Utiliza **Conexiones de informes** para que el segmentador filtre ambos gráficos simultáneamente.

### Objetivo

Vincular controles visuales interactivos a múltiples representaciones gráficas a la vez.

---

## 🔵 Nivel avanzado — Línea de tiempo, tarjetas KPI y lienzo en blanco

Una empresa registra operaciones diarias durante todo un ejercicio.

Disponemos de estos datos de origen:

```tsv
Cod_Operacion	Fecha	Cliente	Facturacion_EUR	Coste_EUR	Margen_Pct
OP-2001	15/01/2026	Tech Solutions	4500,00	2925,00	0,35
OP-2002	28/01/2026	Innova Retail	2800,00	1680,00	0,40
OP-2003	12/02/2026	B2B Logistics	6200,00	4464,00	0,28
OP-2004	25/02/2026	Global Services	1900,00	1045,00	0,45
OP-2005	10/03/2026	Tech Solutions	8300,00	5395,00	0,35
OP-2006	22/03/2026	Grupo Financiero	5100,00	3162,00	0,38
OP-2007	14/04/2026	Innova Retail	3400,00	2108,00	0,38
OP-2008	29/04/2026	B2B Logistics	7100,00	5112,00	0,28
OP-2009	18/05/2026	Global Services	2600,00	1430,00	0,45
OP-2010	30/05/2026	Tech Solutions	9400,00	6110,00	0,35
OP-2011	11/06/2026	Grupo Financiero	4200,00	2520,00	0,40
OP-2012	27/06/2026	Innova Retail	3900,00	2418,00	0,38

```

1. Prepara la hoja `Informe_Ejecutivo` ocultando las **líneas de cuadrícula**.
2. Crea una tabla dinámica que calcule la **Facturación Total** y el **Margen Promedio**.
3. Construye dos **tarjetas KPI visuales** mediante formas geométricas que muestren dinámicamente dichos valores.
4. Crea una tabla dinámica y un gráfico de **líneas** con la evolución mensual.
5. Inserta una **Línea de tiempo** basada en el campo `Fecha` y conéctala a las tablas.
6. Alterna la línea de tiempo entre análisis por **Meses** y por **Trimestres**, verificando que las tarjetas KPI y el gráfico se actualicen al instante.

### Objetivo

Integrar diseño visual de lienzo, indicadores KPI dinámicos y análisis temporal interactivo.

---

## 🔴 Nivel experto — Dashboard UX completo con interpretación de IA

La dirección comercial te entrega el histórico de ventas y solicita un informe ejecutivo de lectura rápida.

Disponemos de estos datos de origen:

```tsv
ID_Venta	Fecha	Categoria	Canal	Comercial	Importe_EUR	Ticket_Medio
V-3001	08/01/2026	Software	Online	Ana Gómez	1450,00	1450,00
V-3002	14/01/2026	Hardware	Tienda Física	Carlos Martínez	3200,00	1600,00
V-3003	22/01/2026	Servicios	Distribuidor	Javier López	850,00	850,00
V-3004	05/02/2026	Hardware	Online	Laura Cano	4100,00	2050,00
V-3005	18/02/2026	Cloud	Directo	Pedro Ruiz	6800,00	3400,00
V-3006	26/02/2026	Software	Tienda Física	Sofía Vega	2100,00	1050,00
V-3007	09/03/2026	Servicios	Online	Ana Gómez	1200,00	600,00
V-3008	21/03/2026	Cloud	Directo	Carlos Martínez	9500,00	4750,00
V-3009	04/04/2026	Hardware	Distribuidor	Javier López	2900,00	1450,00
V-3010	19/04/2026	Software	Online	Laura Cano	3800,00	1900,00
V-3011	07/05/2026	Cloud	Directo	Pedro Ruiz	11200,00	5600,00
V-3012	23/05/2026	Servicios	Tienda Física	Sofía Vega	1650,00	825,00
V-3013	11/06/2026	Hardware	Online	Ana Gómez	5300,00	2650,00
V-3014	28/06/2026	Software	Directo	Carlos Martínez	4600,00	2300,00

```

Construye un **Dashboard completo** en una hoja limpia respetando las siguientes directrices de diseño UX:

1. **Distribución F/Z:**
* Zona Superior: Tarjeta KPI de *Ventas Totales* y *Ticket Medio*.
* Zona Superior/Media: Segmentador horizontal de *Canal* y Línea de Tiempo de *Fecha*.
* Zona Central: Gráfico de barras horizontales de *Ventas por Categoría* (ordenado de mayor a menor).
* Zona Inferior: Gráfico de área/líneas de *Evolución Temporal*.


2. **Paleta de Colores:** Aplica la regla 60-30-10 utilizando tonos neutros de fondo y azul corporativo para las barras.
3. **Optimización visual:** Elimina leyendas redundantes y botones de campo.
4. **Asistencia de IA:** Copia el resumen de datos de tus tablas dinámicas, conéctate a una IA (ChatGPT/Claude/Copilot) y pídele:
> *"Redacta un análisis ejecutivo de 3 puntos clave sobre estos resultados para añadirlo en una caja de texto en mi Dashboard."*


5. Pega el texto generado por la IA en una caja de notas dentro del propio Dashboard.

### Objetivo

Integrar maquetación profesional UX, interacción avanzada y asistencia de IA para storytelling ejecutivo.
