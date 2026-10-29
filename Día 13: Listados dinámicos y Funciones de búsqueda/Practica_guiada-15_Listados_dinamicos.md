# Práctica guiada 15: LISTADOS DINÁMICOS

## 1. Contexto de Negocio

Trabajas en el departamento de control de gestión de una empresa de distribución en Asturias. La dirección comercial necesita dominar las herramientas de desbordamiento de datos en Excel. Para ello, realizaremos un recorrido metodológico: primero experimentaremos de forma aislada con cada función (`UNICOS`, `FILTRAR`, `ORDENAR` y `SECUENCIA` en una y dos dimensiones) variando sus parámetros, y finalmente uniremos todo esto para construir un cuadro de mando comercial auto-expandible.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de datos y pégalo directamente en la celda **A1** de una hoja de Excel en blanco. Utiliza el punto y coma (`;`) como separador si realizas una importación manual:

```csv
ID_Venta;Comercial;Canal;Provincia;Importe_Venta;Fecha
V001;Lucía Martínez;Web;Asturias;1.450,50;12/01/2026
V002;Carlos Gómez;Tienda;Madrid;850,00;14/01/2026
V003;Ana Blanco;Web;Lugo;2.100,00;15/01/2026
V004;Lucía Martínez;Web;Asturias;920,30;18/01/2026
V005;Pedro Ruiz;Teléfono;Sevilla;3.150,00;20/01/2026
V006;Carlos Gómez;Tienda;Toledo;1.200,80;22/01/2026
V007;Ana Blanco;Web;Segovia;1.750,00;25/01/2026
V008;Pedro Ruiz;Teléfono;Málaga;950,00;28/01/2026
V009;Lucía Martínez;Web;Lugo;2.400,00;02/02/2026
V010;Carlos Gómez;Tienda;Madrid;1.890,40;05/02/2026

```

> Selecciona el rango y conviértelo en una **Tabla de Excel** oficial (`Ctrl + T`) asignándole el nombre `Tbl_Ventas`. Esto facilitará enormemente las referencias estructuradas.
> 
> 

---

## 3. Tareas a Resolver

### Fase 1: Práctica Independiente y Exploración de Argumentos

1. **Función `UNICOS`:** Obtener listas sin duplicados de los comerciales y, posteriormente, de las provincias.


2. **Función `FILTRAR`:** Extraer operaciones según distintas condiciones (por canal y por umbral de importe).


3. **Función `ORDENAR`:** Reorganizar datos numéricos cambiando los argumentos de orden ascendente y descendente.


4. **Función `SECUENCIA` (1D y 2D):** Generar series lineales simples y matrices bidimensionales (filas y columnas configurables).



### Fase 2: Informes Automáticos Integrados

1. **Informe Básico Anidado (Filtro + Ordenación):** Filtrar la tabla `Tbl_Ventas` para obtener las ventas de la provincia de `"Asturias"` (columnas de Comercial, Provincia e Importe) y ordenarlas de mayor a menor importe. Ubicación de la solución: **I24**.


2. **Informe por Canal Ordenado Alfabéticamente:** Extraer de forma limpia el Comercial, Canal e Importe de las ventas realizadas por el canal `"Web"`, ordenando el resultado alfabéticamente por el nombre del Comercial. Ubicación de la solución: **N24**.


3. **Catálogo Único y Ordenado por Regiones/Provincias:** Generar un listado vertical de las provincias que han registrado ventas, sin duplicados y ordenado de la A a la Z. Ubicación de la solución: **S24**.


4. **Listado de Ventas Clave sobre Umbral:** Filtrar las ventas con importe superior a `1.500,00 €` devolviendo las columnas de Comercial e Importe_Venta, ordenadas de mayor a menor importe. Ubicación de la solución: **S24**.


5. **Informe Completo con Numeración Adaptativa Auto-expandible:** Construir un cuadro de mando que combine filtrado, ordenación descendente por importe para la provincia de `"Madrid"` y una columna de numeración secuencial dinámica que se ajuste milimétricamente al número de filas resultantes. Ubicación de la solución: **U24** (columna de índice) y **V24** (datos derramados).

---

## 4. Guía de Solución Paso a Paso

### 🟢 Fase 1: Práctica Independiente de Funciones

#### 1. La función `UNICOS` (Deduplicación)

* **Variación A (Comerciales):** En la celda `I2`, escribe:
```excel
=UNICOS(Tbl_Ventas[Comercial])

```


Devolverá la lista vertical limpia de los tres comerciales.


* **Variación B (Provincias):** En la celda `K2`, escribe:
```excel
=UNICOS(Tbl_Ventas[Provincia])

```


Extraerá el listado único de provincias de forma independiente.



#### 2. La función `FILTRAR` (Extracción condicionada)

* **Variación A (Por Canal):** En la celda `M2`, introduce:
```excel
=FILTRAR(Tbl_Ventas; Tbl_Ventas[Canal] = "Web"; "Sin resultados")

```


* **Variación B (Por Importe):** En la celda `M15`, prueba a cambiar el criterio para extraer ventas superiores a 1.500,00 €:
```excel
=FILTRAR(Tbl_Ventas; Tbl_Ventas[Importe_Venta] > 1500; "Ninguna venta supera el umbral")

```



#### 3. La función `ORDENAR` (Reorganización de datos)

* **Variación A (Ascendente - de menor a mayor):** En la celda `U2`, ordena los importes de forma creciente (argumento de orden `1`):
```excel
=ORDENAR(Tbl_Ventas[Importe_Venta]; 1; 1)

```


* **Variación B (Descendente - de mayor a menor):** En la celda `W2`, cambia el argumento a `-1`:


```excel
=ORDENAR(Tbl_Ventas[Importe_Venta]; 1; -1)

```



#### 4. La función `SECUENCIA` (Series Unidimensionales y Bidimensionales)

* **Variación A (1 Dimensión - Serie vertical):** En la celda `Y2`, genera una serie del 1 al 5:


```excel
=SECUENCIA(5)

```


* **Variación B (2 Dimensiones - Matriz filas × columnas):** Para rellenar una cuadrícula o matriz bidimensional (por ejemplo, **4 filas y 3 columnas**, empezando en el número **10** y avanzando en saltos de **5** en **5**), escribe en la celda `AA2`:


```excel
=SECUENCIA(4; 3; 10; 5)

```


*Explicación de argumentos:* `=SECUENCIA(filas; columnas; [inicio]; [paso])`. Excel generará una matriz rectangular de celdas desbordadas automáticamente con dichos valores.



---

### 🟡 Fase 2: Informes Automáticos Integrados

Una vez dominado el uso individual y la exploración de argumentos de cada función, el verdadero potencial de las matrices dinámicas en Excel se alcanza al **anidar varias funciones dentro de una misma fórmula**. Esto nos permite realizar extracciones, filtrados, ordenaciones y estructuraciones avanzadas de forma automática en un solo paso.

Para mantener nuestro libro de trabajo perfectamente organizado y evitar solapamientos con las pruebas anteriores, todas las soluciones de esta sección se ubicarán **a partir de la celda I24**.

---

#### 1. Filtro de Región/Provincia + Ordenación Descendente por Importe

Queremos extraer las columnas de Comercial, Provincia e Importe para las ventas de `"Asturias"` y presentarlas ordenadas de mayor a menor importe.

1. Haz clic en la celda **I24**.
2. Escribe la siguiente fórmula anidada:


```excel
=ORDENAR(FILTRAR(Tbl_Ventas[[Comercial]:[Importe_Venta]]; Tbl_Ventas[Provincia] = "Asturias"); 4; -1)

```


* **Explicación didáctica:**
* `FILTRAR(...)` toma el rango de columnas `[Comercial]:[Importe_Venta]` y extrae únicamente las filas donde la provincia es `"Asturias"`.


* `ORDENAR( ... ; 4; -1)` recibe la matriz filtrada y la ordena basándose en su **4ª columna** (*Importe_Venta*) de forma descendente (`-1`).







---

#### 2. Filtrado por Canal + Ordenación Alfabética por Comercial

Queremos analizar la efectividad del canal `"Web"` mostrando Comercial, Canal e Importe_Venta, pero esta vez ordenados alfabéticamente por el Comercial.

1. Haz clic en la celda **N24**.
2. Escribe la siguiente fórmula anidada:


```excel
=ORDENAR(FILTRAR(Tbl_Ventas[[Comercial]:[Importe_Venta]]; Tbl_Ventas[Canal] = "Web"); 1; 1)

```


* **Explicación didáctica:**
* `FILTRAR` extrae solo los registros correspondientes al canal `"Web"`.


* `ORDENAR( ... ; 1; 1)` toma el resultado y lo ordena por la **1ª columna** (*Comercial*) en orden ascendente alfabético (`1`).







---

#### 3. Deduplicación + Ordenación Alfabética (`ORDENAR` + `UNICOS`)

Para generar un desplegable o reporte limpio de las provincias con actividad comercial, necesitamos eliminar duplicados y ordenarlas alfabéticamente al mismo tiempo.

1. Haz clic en la celda **S24**.
2. Escribe la siguiente fórmula anidada:


```excel
=ORDENAR(UNICOS(Tbl_Ventas[Provincia]))

```


* **Explicación didáctica:**
* `UNICOS(...)` examina la columna de provincias y elimina todas las repeticiones, devolviendo una lista reducida.


* `ORDENAR(...)` envuelve esa lista y la alinea automáticamente de la A a la Z (por defecto, orden ascendente `1`).







---

#### 4. Filtrado por Umbral Económico + Ordenación de Mayor a Menor

El departamento comercial requiere identificar rápidamente las operaciones importantes superiores a `1.500,00 €`, mostrando el Comercial y el Importe.

1. Haz clic en la celda **S24**.
2. Escribe la siguiente fórmula anidada:


```excel
=ORDENAR(FILTRAR(Tbl_Ventas[[Comercial]:[Importe_Venta]]; Tbl_Ventas[Importe_Venta] > 1500); 3; -1)

```


* **Explicación didáctica:**
* `FILTRAR` evalúa numéricamente que el campo `Importe_Venta` sea estrictamente mayor a `1500`.


* `ORDENAR` reorganiza los resultados de mayor a menor según la columna del importe.







---

#### 5. Informe Dinámico Auto-expandible (`SECUENCIA` + `FILAS` + operador `#`)

Construiremos un cuadro de mando para la provincia de `"Madrid"` donde la numeración de los registros devueltos se genere e incremente de forma 100 % automática.

1. **Paso 1 (Generar la matriz de datos en V24):**
Haz clic en **V24** e introduce la fórmula anidada de filtro y ordenación:


```excel
=ORDENAR(FILTRAR(Tbl_Ventas[[Comercial]:[Importe_Venta]]; Tbl_Ventas[Provincia] = "Madrid"); 3; -1)

```


2. **Paso 2 (Generar el índice numérico adaptativo en U24):**
Haz clic en la celda a la izquierda (**U24**) e introduce la fórmula anidada con el operador de rango derramado (`#`):


```excel
=SECUENCIA(FILAS(V24#))

```


* **Explicación didáctica:**
* `V24#` hace referencia a la matriz completa que se derrama desde `V24`.


* `FILAS(V24#)` cuenta dinámicamente cuántas filas ha devuelto la consulta (por ejemplo, 2 o 10 filas).


* `SECUENCIA(...)` crea al instante una lista vertical numerada (`1, 2, 3...`) idéntica al tamaño de la matriz de datos. Si los datos cambian o se añaden ventas a la tabla `Tbl_Ventas`, la numeración se expandirá o contraerá automáticamente.
