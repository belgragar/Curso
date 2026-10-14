# 📘 Ejercicio 03: Formatos básicos y personalizados

> **Versión de referencia:** Excel con configuración regional **España** (separador de miles `.`, separador decimal `,`, año `aaaa` en los códigos de formato).

## 🚀 Antes de empezar

1. Abre un libro nuevo de Excel y crea **6 hojas** llamadas `Ejercicio 1` … `Ejercicio 6`.
2. En cada ejercicio encontrarás un **bloque de datos**. Cópialo con el ratón, haz clic en la celda de Excel que se indica y pégalo con `Ctrl + V`. Cada tabulación del bloque salta a la celda siguiente.
3. Realiza las **especificaciones** en orden y compara tu hoja con la imagen del **resultado final**.
4. En otro documento tienes las **soluciones** paso a paso. Intenta resolver cada ejercicio antes de mirarlas.

### 🧰 Herramientas que vas a utilizar

| Herramienta | Dónde está | Atajo |
|---|---|---|
| Formato de celdas (todas las pestañas) | Clic derecho → *Formato de celdas…* | `Ctrl + 1` |
| Alto de fila / Ancho de columna | *Inicio* → grupo *Celdas* → *Formato* | — |
| Combinar y centrar | *Inicio* → grupo *Alineación* | — |
| Bordes y *Dibujar borde* | *Inicio* → grupo *Fuente* → botón *Bordes* | — |
| Copiar formato (pincel) | *Inicio* → grupo *Portapapeles* (doble clic para usarlo varias veces) | — |
| Controlador de relleno | Cuadradito en la esquina inferior derecha de la celda seleccionada: arrástralo | — |
| Autosuma de rango / selección múltiple | Mantén `Ctrl` para seleccionar rangos separados | `Ctrl + clic` |

### 🔤 Códigos de formato personalizado (configuración regional España)

Se escriben en *Formato de celdas* → *Número* → *Personalizada* → cuadro **Tipo**.

| Código | Significado |
|---|---|
| `0` | Dígito obligatorio (muestra ceros si falta) |
| `#` | Dígito opcional (no muestra ceros sobrantes) |
| `.` | Separador de miles. Si va **al final** del número, divide entre 1.000 |
| `,` | Separador decimal |
| `"texto"` | Texto literal entre comillas dobles |
| `*x` | Repite el carácter `x` para rellenar el ancho de la celda |
| `;` | Separa las secciones: `positivo ; negativo ; cero ; texto` |
| `[Rojo]` `[Azul]` `[Verde]` `[Amarillo]` `[Negro]` | Color de la sección |
| `d` `dd` `ddd` `dddd` | Día (1, 01, abreviado, nombre completo) |
| `m` `mm` `mmm` `mmmm` | Mes (1, 01, abreviado, nombre completo) |
| `aa` `aaaa` | Año con 2 o 4 dígitos |
| `h` `hh` `mm` `ss` | Horas, minutos y segundos |
| `E+00` | Notación científica |

---

# 📝 Enunciados

## Ejercicio 1 — Alineación, orientación y combinación de celdas

**Datos de partida** (pégalos en la celda **B4**):

```text
El perro de San Roque Rodríguez no tiene rabo	San Roque	San Roque	San Roque
El perro de San Roque no tiene rabo porque Ramón Rodríguez se lo ha robado. Este texto lo justificamos horizontalmente
El perro de San Roque combinando columnas
Ramón Rodríguez	Ramón Rodríguez	Ramón Rodríguez
El perro de San Roque no tiene rabo porque Ramón Rodríguez se lo ha robado. Este texto está justificado verticalmente
	San Roque	San Roque	San Roque
```

**Especificaciones:**

1. Modificar los altos de las siguientes filas:
   - Fila 4: 27
   - Fila 5: 138
   - Fila 6: 21
   - Fila 7: 72
   - Fila 8: 125
   - Fila 9: 135
2. Modificar los anchos de las siguientes columnas:
   - Columna B: 46
   - Columnas C, D, E: 19
3. Seleccionar el rango de celdas **B4:E9** y marcar todos los bordes.
4. Para las celdas de la **fila 4** establecer las siguientes alineaciones:
   - Celda B4: alineación horizontal izquierda, alineación vertical inferior.
   - Celda C4: alineación horizontal izquierda, alineación vertical inferior.
   - Celda D4: alineación horizontal centrar, alineación vertical inferior.
   - Celda E4: alineación horizontal derecha, alineación vertical inferior.
5. Para las celdas de la **fila 5** establecer las siguientes alineaciones:
   - Celda B5: justificar horizontalmente, alineación vertical inferior.
   - Celdas C5, D5, E5: combinarlas.
6. Combinar y centrar las celdas de la **fila 6**.
7. Para las celdas de la **fila 7** establecer las siguientes alineaciones:
   - Celda B7: horizontal izquierda, vertical superior.
   - Celda C7: horizontal izquierda, vertical superior.
   - Celda D7: horizontal izquierda, vertical inferior.
8. Para la **fila 8**, modificar la celda B8 justificándola verticalmente.
9. Combinar las celdas E7 y E8.
10. Para las celdas de la **fila 9** establecer las siguientes alineaciones:
    - Celda C9: orientación vertical.
    - Celda D9: orientación a 90º, alineación horizontal centrada y vertical inferior.
    - Celda E9: orientación a -90º, alineación horizontal centrada y vertical inferior.


![Resultado final del ejercicio 1](\..\imagenes\01-ejercicio1_resultado.png)

---

## Ejercicio 2 — Formatos numéricos personalizados (precios, decimales, teléfonos y códigos postales)

**Datos de partida** (pégalos en la celda **B3**):

```text
Precios
Valor	Formato 1	Formato 2	Formato 3	Formato 4
100000000	100000000	100000000	100000000	100000000
954954954	954954954	954954954	954954954	954954954

Decimales
Valor	Formato 1	Formato 2	Formato 3	Formato 4
0,5	0,5	0,5	0,5	0,5
0,2	0,2	0,2	0,2	0,2

Teléfonos
Valor	Formato 1	Formato 2	Formato 3	Formato 4
955955955	955955955	955955955	955955955	955955955
974971971	974971971	974971971	974971971	974971971

Códigos postales
Valor	Formato 1	Formato 2	Formato 3	Formato 4
14654	14654	14654	14654	14654
14654	14654	14654	14654	14654
```

**Especificaciones:**

1. Modificar los formatos de las cuatro «tablas» como se indica a continuación:
   - Título: combinar las cinco celdas y centrar texto de la celda.
   - Colocar línea sencilla a toda la tabla y el borde exterior más grueso.
   - Título con letra en negrita y fondo azul claro.
   - Segunda fila y primera columna con letra cursiva y fondo gris.
2. Formatos para la tabla **Precios**:
   - Formato 1: número sin decimales y con separador de miles.
   - Formato 2: formato moneda sin decimales y con separador de miles.
   - Formato 3: formato moneda sin los tres últimos dígitos y con texto final «miles de €».
   - Formato 4: formato moneda sin los seis últimos dígitos y con texto «cientos de miles de €».
3. Formatos para la tabla **Decimales**:
   - Formato 1: número sin decimales.
   - Formato 2: número con dos decimales.
   - Formato 3: número con tres decimales.
   - Formato 4: número con notación científica.
4. Formatos para la tabla **Teléfonos**:
   - Formato 1: tres primeros dígitos entre paréntesis, espacio, tres dígitos, guión y últimos tres dígitos.
   - Formato 2: tres primeros dígitos entre paréntesis, espacio, dígitos restantes por parejas separados por espacios.
   - Formato 3: texto «Prefijo: » tres dígitos «- Número: » XX XX XX.
   - Formato 4: XXX – XX – XX – XX.
5. Formatos para la tabla **Códigos postales**:
   - Formato 1: número con separador de miles y sin decimales.
   - Formato 2: «Provincia: » dos dígitos «municipio: » tres dígitos.
   - Formato 3: dígitos separados por espacios.
   - Formato 4: dígitos con punto de miles, separados por espacios.


![Resultado final del ejercicio 2](\..\imagenes\01-ejercicio2_resultado.png)

---

## Ejercicio 3 — Formatos de fecha, hora, totales y saldos (con condiciones)

**Datos de partida** (pégalos en la celda **B3**):

```text
Fechas
Valor	Formato 1	Formato 2	Formato 3	Formato 4
01/01/2006	01/01/2006	01/01/2006	01/01/2006	01/01/2006
03/05/2016	03/05/2016	03/05/2016	03/05/2016	03/05/2016

Horas
Valor	Formato 1	Formato 2	Formato 3	Formato 4
11:15	11:15	11:15	11:15	11:15
21:35	21:35	21:35	21:35	21:35

Totales
Valor	Formato 1	Formato 2	Formato 3	Formato 4
3524	3524	3524	3524	3524
5035	5035	5035	5035	5035

Saldos
Valor	Formato 1	Formato 2	Formato 3	Formato 4
25000	25000	25000	25000	25000
-3142	-3142	-3142	-3142	-3142
0	0	0	0	0
error	error	error	error	error
-4100	-4100	-4100	-4100	-4100
500	500	500	500	500
```

**Especificaciones:**

1. Para la primera fila de las cuatro tablas realizar las siguientes modificaciones:
   - Combinar y centrar las cinco celdas de la primera fila.
   - Colocar el título con fuente Arial Black de 16 puntos, azul y fondo en gris claro.
2. Para la segunda fila de las cuatro tablas realizar las siguientes modificaciones:
   - Fondo de celda en azul.
   - Fuente en Comic Sans de 11 puntos y cursiva.
3. Utilizando la herramienta «dibujar borde», modificar los bordes de todas las tablas como se indica a continuación:
   - Borde exterior: línea gruesa, azul oscuro.
   - Línea entre primera y segunda fila: doble de color rojo.
   - Línea entre segunda y tercera fila: discontinua y azul.
   - Resto de líneas: continua y de color rojo.
4. Aplicar los siguientes formatos a la tabla «Fechas»:
   - Formato 1: mes completo «-» año con dos dígitos.
   - Formato 2: mes completo día, año completo.
   - Formato 3: «Huelva, » día de la semana día «de» mes_completo «de» año_completo.
   - Formato 4: día de la semana reducido – mes reducido – año reducido.
5. Aplicar los siguientes formatos a la tabla «Horas»:
   - Formato 1: hh:mm:ss.
   - Formato 2: hora y minutos en formato de 12 horas (AM/PM).
   - Formato 3: «Hora: » hh «minutos: » mm «segundos:» ss.
   - Formato 4: «Las » hh « horas y » mm « minutos».
6. Aplicar los siguientes formatos a la tabla «Totales»:
   - Formato 1: número a la derecha con puntos rellenando la celda en su izquierda.
   - Formato 2: «Total ……» y número sin puntos de miles y con un decimal.
   - Formato 3: «Total……» y número con puntos de miles, sin decimales y con símbolo de euro.
   - Formato 4: número con punto de miles y dos decimales, símbolo de coma, «euros.» y puntos suspensivos rellenando el resto de la celda.
7. Aplicar los siguientes formatos a la tabla «Saldos»:
   - **Formato 1:**
     - Si es positivo: azul, con puntos de miles, dos decimales.
     - Si es negativo: rojo, con puntos de miles, símbolo «-», dos decimales.
     - Si es cero: tres guiones de color verde.
     - Si es otra cosa: «ERROR».
   - **Formato 2:**
     - Si es positivo: azul, con puntos de miles, sin decimales y símbolo de euro.
     - Si es negativo: rojo, con puntos de miles, sin decimales, entre paréntesis, símbolo de euro.
     - Si es cero: texto «CERO» en amarillo.
     - Si es otra cosa: «Error».
   - **Formato 3:**
     - Si es positivo: «Entrada:» número con puntos de miles y dos decimales.
     - Si es negativo: «Salida:» número con puntos de miles y un decimal.
     - Si es cero: «cero».
     - Si es otra cosa: «error».
   - **Formato 4:**
     - Si es positivo: «Positivo:» número sin decimales, con puntos de miles, con símbolo de euro y en azul.
     - Si es negativo: «Negativo:» número sin decimales, con puntos de miles, con símbolo de euro y en rojo.
     - Si es cero: «Valor nulo» en verde.
     - Si es otra cosa: «Error de caja» en negro.


![Resultado final del ejercicio 3](\..\imagenes\01-ejercicio3_resultado.png)

---

## Ejercicio 4 — Suma y resta de celdas

**Datos de partida** (pégalos en la celda **B3**):

```text
SUMA DE CELDAS
	2345	5849	658	6987
	4532	359	548	3547
	123	98746	658	9875
	456	356	1111	35487
Totales


RESTA DE CELDAS
	9587	3598	587	359
	265	6589	3543	65
Resultado
```

**Especificaciones:**

1. Para la primera fila de la primera tabla realizar las siguientes modificaciones:
   - Combinar y centrar celdas B3 a F3.
   - Fuente Comic Sans de 14 puntos, negrita, con fondo verde.
   - Copiar formato y aplicarlo a la fila 11.
2. Colocar bordes a las dos tablas, todos sencillos a excepción de (usar la opción de dibujar borde):
   - Borde exterior más grueso.
   - Borde bajo el título: línea doble de color azul.
   - Borde sobre «Totales» y «Resultado»: línea discontinua roja.
3. Formato de celda para todos los números de la primera tabla, incluyendo los totales: número con un decimal y puntos de miles.
4. Formato de celda para todos los números de la segunda tabla, incluyendo los totales:
   - Moneda con dos decimales y puntos de miles. Formato euro.
   - Números negativos en rojo.
5. Para la última fila de ambas tablas aplicar el siguiente formato de diseño:
   - Fuente Arial 12, negrita y cursiva.
   - Fondo gris.
6. Usando el operador suma (+), realizar la suma de la última fila de la primera tabla. Aplicar el mismo operador al resto de la fila usando el **controlador de relleno**.
7. Usando el operador resta (-), realizar la resta de la última fila de la segunda tabla. Aplicar el mismo operador al resto de la fila usando el **controlador de relleno**.


![Resultado final del ejercicio 4](\..\imagenes\01-ejercicio4_resultado.png)

---

## Ejercicio 5 — Multiplicación y división de celdas

**Datos de partida** (pégalos en la celda **B3**):

```text
MULTIPLICACIÓN DE CELDAS
	2345	5849	658	6987
	12	3	31	5
Resultado


DIVISIÓN DE CELDAS
	9587	3598	587	359
	265	13	5	9
Resultado
```

**Especificaciones:**

1. Para la primera fila de la primera tabla realizar las siguientes modificaciones:
   - Combinar y centrar celdas B3 a F3.
   - Fuente Broadway de 16 puntos, negrita, con fondo azul y letra blanca.
   - Copiar formato y aplicarlo a la fila 9.
2. Combinar las celdas B4 a B6 y situar el texto «Resultado» en la parte inferior y justificado a la izquierda. Repetir el proceso para las celdas B10 a B12.
3. Colocar bordes a las dos tablas, todos sencillos a excepción de (usar la opción de dibujar borde):
   - Borde exterior de color verde y con línea discontinua.
   - Línea bajo el título de color rojo y gruesa.
4. Formato de celda para todos los números de la primera tabla, incluyendo totales: número sin decimales y con separadores de miles.
5. Formato de celda para todos los números de la segunda tabla, incluyendo totales: número con dos decimales y separadores de miles.
6. Para la última fila de ambas tablas aplicar el siguiente formato (excluir la celda «Resultado»):
   - Fuente Verdana de 16 puntos, negrita, cursiva.
   - Fondo de celda de color mostaza.
7. Usando el operador multiplicación (`*`), realizar la multiplicación de la segunda columna de la primera tabla. Aplicar el mismo operador al resto de la fila usando el **controlador de relleno**.
8. Usando el operador división (`/`), realizar la división de la segunda columna de la primera tabla. Aplicar el mismo operador al resto de la fila usando el **controlador de relleno**.


![Resultado final del ejercicio 5](\..\imagenes\01-ejercicio5_resultado.png)

---

## Ejercicio 6 — Precio total y horas semanales

**Datos de partida** (pégalos en la celda **B3**):

```text
CÁLCULO DEL PRECIO TOTAL
Cantidad	Producto	Precio unitario	Precio total
2	Lápiz	1,2
6	Carpeta	0,75
7	Bolígrafo	2,3
8	Goma	0,98
9	Marcadores	2,7
Total



HORAS SEMANALES
Día	Entrada	Salida	Horas trabajadas
Lunes	7:00	15:35
Martes	7:13	15:46
Miércoles	7:08	12:00
Jueves	6:45	14:53
Viernes	7:40	16:06
Sábado	7:32	14:09
Total de horas
```

**Especificaciones:**

1. Para la primera fila de la primera tabla realizar las siguientes modificaciones:
   - Combinar y centrar celdas B3 a E3.
   - Fuente Tahoma de 14 puntos, negrita, cursiva, fondo color mostaza.
   - Copiar formato y aplicarlo a la fila 14.
2. Para la segunda fila de la primera tabla realizar las siguientes modificaciones:
   - Fuente Arial de 11 puntos, negrita.
   - Fondo color mostaza más oscura que el de la primera fila.
   - Copiar formato y aplicarlo a la fila 15 (celdas B15 a E15).
3. Colocar las columnas B, C, D, E con el mismo ancho y de forma que quepan todos los textos.
4. Para la primera tabla calcular el primer valor de «Precio total» usando el operador de multiplicación (`*`). Aplicar el mismo operador al resto de la columna usando el **controlador de relleno**.
5. Para la segunda tabla calcular el primer valor de «Horas trabajadas» usando el operador de resta (`-`). Aplicar el mismo operador al resto de la columna usando el **controlador de relleno**.
6. Calcular el total de ambas tablas usando el operador suma (`+`).
7. Colocar bordes sencillos a las dos tablas.
8. Modificar la última fila de ambas tablas con el siguiente formato: fuente Calibri de 14 puntos, negrita, cursiva y fondo gris.
9. Para la primera tabla dar formato de dos decimales con símbolo de € a aquellas celdas que muestren precios.


![Resultado final del ejercicio 6](\..\imagenes\01-ejercicio6_resultado.png)

