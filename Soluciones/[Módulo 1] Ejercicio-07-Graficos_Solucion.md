# Ejercicios de gráficos en Excel

> **Antes de empezar:** estos ejercicios trabajan con Excel en español (separador de argumentos `;` y nombres de función en español). Para copiar las tablas, selecciona el contenido del recuadro, pégalo en la celda **B3** (Ejercicios 11 y 12) o **B5** (Ejercicio 15) y Excel lo separará en celdas automáticamente.

---

# PARTE 1. ENUNCIADOS

## Ejercicio 11. Gráficos circulares: evolución por cursos

Datos de partida (alumnos por universidad andaluza y curso). Se muestran **sin la columna Media**, que debes calcular:

```
	2010/2011	2011/2012	2012/2013	2013/2014	2014/2015	Media
Córdoba	2480	2600	2750	2800	3000	
Granada	3700	4000	4200	4250	5000	
Sevilla	3800	4100	4150	3950	3950	
Málaga	2500	2540	2930	2800	2900	
Jaén	1800	1890	2100	2000	1945	
Huelva	1200	1180	1250	1300	1350	
Almería	940	975	1050	1200	1150	
Cádiz	700	840	830	850	875	
```

**1.-** Calcular la columna **Media** de cada universidad (media de los cinco cursos).

**2.-** Realizar una gráfica circular con los datos del curso 2010/2011 con las siguientes características:
- Tipo de gráfica: Circular 3D.
- Mostrar los siguientes elementos: Título del gráfico (encima del gráfico); Etiqueta de datos (mostrando el valor en el extremo externo); Leyenda (en la parte inferior).

**3.-** Realizar las siguientes modificaciones en la gráfica:
- Título del gráfico: debe mostrar el texto "Curso 2010/2011". Moverlo hacia la izquierda. Fuente "Calibri 16, negrita y cursiva".
- Leyenda: se dividirá en dos filas y deberá estar encuadrada. Si se superpone sobre la gráfica deberá moverse la gráfica y la leyenda.

**4.-** Modificar los colores de la gráfica como se indica:
- Granada: Rojo
- Sevilla: Amarillo
- Málaga: Verde oscuro
- Córdoba: Gris claro

**5.-** Modificar el área del gráfico como se indica:
- Relleno degradado.
- Borde con línea sólida de color rojo y esquinas redondeadas.

**6.-** Quitar contorno a la gráfica y a las entradas en la leyenda.

**7.-** Colocar el fondo de la leyenda en color gris.

**8.-** Repetir la misma gráfica para el curso 2011/2012, realizando las modificaciones en el título y respetando los mismos colores que para la gráfica anterior.

**9.-** Modificar las etiquetas de datos de la gráfica 2011/2012 para que se muestre el porcentaje y el nombre de la categoría en vez del valor.

**10.-** Separar los quesos de la última gráfica, y el correspondiente a Granada separarlo un poco más que el resto.

**11.-** Realizar las gráficas restantes aplicando los siguientes formatos:
- Gráficas "2012/2013" y "2014/2015": formato de "Curso 2010/2011".
- Gráfica "2013/2014": formato de "Curso 2011/2012".

---

## Ejercicio 12. Gráficos de columnas por universidad

Datos de partida (sin la columna Media):

```
	2010/2011	2011/2012	2012/2013	2013/2014	2014/2015	Media
Córdoba	2480	2600	2750	2800	3000	
Granada	3700	4000	4200	4250	5000	
Sevilla	3800	4100	4150	3950	3950	
Málaga	2500	2540	2930	2800	2900	
Jaén	1800	1890	2100	2000	1945	
Huelva	1200	1180	1250	1300	1350	
Almería	940	975	1050	1200	1150	
Cádiz	700	840	830	850	875	
```

**1.-** Calcular la columna **Media** de cada universidad.

**2.-** Realizar un gráfico de barras con los datos de la provincia de Córdoba para todos los cursos (sin incluir la media), con las siguientes características:
- Tipo de gráfica: columna agrupada 2D.
- Modificar el título de la gráfica. Cambiar "Córdoba" por "Universidad de Córdoba".

**3.-** Realizar las siguientes modificaciones en la gráfica:
- Eliminar las líneas de división horizontales.
- Relleno degradado en el área de trazado.
- Borde del área de trazado con línea sólida de color negro.
- En opciones del eje, eliminar la línea.

**4.-** Realizar las siguientes modificaciones en la gráfica:
- En opciones del eje vertical establecer límite máximo a 4000 y las unidades principales a 1000.
- Colocar en el eje vertical marcas de graduación exteriores.

**5.-** Modificaciones en las columnas de la gráfica:
- Establecer un ancho del rango del 100 % (columnas más anchas).
- Borde de la columna de color negro.

**6.-** Modificaciones en el área del gráfico:
- Borde del área de color verde oscuro y con línea de 2 puntos de ancho.
- Fondo de relleno sólido y color verde claro.

**7.-** Copiar y pegar la gráfica anterior tantas veces como universidades se muestran en la tabla inicial (7 veces más), modificando en cada caso el título y los datos de cada gráfica.

**8.-** En cada una de las gráficas realizar las siguientes modificaciones del eje vertical:

| Universidad | Límite máx. | Límite mín. | Unidades principales |
|---|---|---|---|
| Granada | 6000 | 0 | 1000 |
| Sevilla | 5000 | 0 | 1000 |
| Málaga | 3000 | 0 | 500 |
| Jaén | 3000 | 0 | 1000 |
| Huelva | 2000 | 0 | 250 |
| Almería | 1500 | 0 | 250 |
| Cádiz | 1000 | 0 | 200 |

**9.-** En cada una de las gráficas realizar las siguientes modificaciones de diseño referentes a colores:

| Universidad | Barras | Líneas de barras | Fondo de barras | Fondo del área |
|---|---|---|---|---|
| Granada | Rojas | Rojo oscuro | Naranja claro | Naranja oscuro |
| Sevilla | Verdes | Verde oscuro | Verde claro | Azul |
| Málaga | Amarillas | Rojo | Blanco | Gris claro |
| Jaén | Naranja claro | Verde | Azul | Rojo claro |
| Huelva | Grises | Rojo | Amarillo | Azul claro |
| Almería | Verdes | Blanca | Naranja claro | Blanco |
| Cádiz | Dorado oscuro | Blanca | Gris | Amarillo |

**10.-** Colocar en las 8 gráficas las etiquetas de datos en el extremo externo, excepto en la de Málaga, que se colocará en el extremo interno.

---

## Ejercicio 15. Matrículas de primer curso por titulación

Datos de partida (las tres últimas columnas están por calcular):

```
	REPITEN		NUEVOS		TOTAL	
TITULACIÓN	Total	Mujeres	Total	Mujeres	Total	% Mujeres	% Hombres
Arquitectura	10	2	232	124			
Ingeniería Informática	13	10	38	27			
Ingeniería Química	22	10	155	98			
Biología	22	9	168	91			
Bioquímica	9	1	53	18			
Física	8	5	14	7			
Matemáticas	4	4	99	58			
```

**1.-** Calcular el **Total** de matrículas de cada titulación (repiten + nuevos).

**2.-** Calcular el **% Mujeres** de cada titulación (mujeres que repiten + mujeres nuevas, entre el total).

**3.-** Calcular el **% Hombres** de cada titulación.

**4.-** Aplicar formato **Porcentaje** a las columnas % Mujeres y % Hombres.

**5.-** Insertar un gráfico donde se muestre el reparto de matrículas por titulación:
- Seleccionar columnas B y G.
- Insertar gráfico circular 3D y seleccionar el diseño de gráfico que incluya título, leyenda y valores en porcentaje, tal y como se muestra en el resultado final.

**6.-** Realizar las siguientes modificaciones sobre el gráfico anteriormente insertado:
- Título del gráfico: Alumnos matriculados por titulación.
- Formato de la leyenda: borde con línea sólida; ancho de 0,5; color negro.
- Formato del área del gráfico: borde con línea sólida; color negro; ancho de 2 puntos; esquinas redondeadas y efecto de sombra exterior.

**7.-** Insertar un gráfico donde se muestre el reparto por sexos en cada titulación:
- Seleccionar columnas B, H, I.
- Insertar gráfico de barra 3D agrupada y seleccionar el diseño de gráfico que incluya título y tabla de datos.

**8.-** Realizar las siguientes modificaciones sobre el gráfico insertado en el punto 7:
- Título del gráfico: Alumnos matriculados por sexo y titulación.
- Cambiar los nombres de las series: Serie 1 = %Mujeres; Serie 2 = %Hombres.
- Formato del área del gráfico: borde con línea sólida; color negro; ancho de 2 puntos; esquinas redondeadas y efecto de sombra exterior.

---

## Ejercicio Minigráficos. Tendencia de cada universidad

Datos de partida (sin la columna Media):

```
	2010/2011	2011/2012	2012/2013	2013/2014	2014/2015	Media
Córdoba	2480	2600	2750	2800	3000	
Granada	3700	4000	4200	4250	5000	
Sevilla	3800	4100	4150	3950	3950	
Málaga	2500	2540	2930	2800	2900	
Jaén	1800	1890	2100	2000	1945	
Huelva	1200	1180	1250	1300	1350	
Almería	940	975	1050	1200	1150	
Cádiz	700	840	830	850	875	
```

**1.-** Calcular la columna **Media** de cada universidad.

**2.-** En la columna **J** insertar un minigráfico de **líneas** por cada universidad, con los datos de los cinco cursos (columnas C a G).

**3.-** En la columna **K** insertar un minigráfico de **columnas** por cada universidad, con los mismos datos.

**4.-** Al minigráfico de líneas aplicar el color de serie azul oscuro (#376092) y mostrar los marcadores, el punto alto, el punto bajo, el primer punto y el último punto en rojo.

**5.-** Comprobar que ambos tipos de minigráfico se han aplicado a las 8 universidades (filas 4 a 11).

---

# PARTE 2. SOLUCIONES

> En todos los casos el menú **Diseño de gráfico** y **Formato** aparece al hacer clic sobre el gráfico. Muchas opciones se encuentran también en el panel **Dar formato a...** (clic derecho sobre el elemento > *Dar formato a...*).

## Solución Ejercicio 11

**1.- Media.** Clic en **H4** y escribe:

```
=PROMEDIO(C4:G4)
```

Pulsa **Intro**, vuelve a **H4** y arrastra el controlador de relleno (esquina inferior derecha) hasta **H11**.

**2.- Gráfico circular 3D.**
1. Selecciona **B3:C11** (universidades y curso 2010/2011).
2. **Insertar > Gráfico circular > Circular 3D**.
3. **Diseño de gráfico > Agregar elemento de gráfico**:
   - *Título del gráfico > Encima del gráfico*.
   - *Etiquetas de datos > Extremo externo* (por defecto muestran el valor).
   - *Leyenda > Abajo*.

**3.- Título y leyenda.**
1. Clic en el título, escribe `Curso 2010/2011`. En **Inicio**: fuente **Calibri**, tamaño **16**, **Negrita** y **Cursiva**.
2. Arrastra el título hacia la izquierda.
3. Clic en la leyenda y arrastra uno de sus tiradores laterales para estrecharla hasta que se divida en dos filas. Clic derecho > *Dar formato a leyenda* > **Relleno y línea > Borde > Línea continua** para encuadrarla.
4. Si se superpone al gráfico, desplaza y redimensiona el gráfico y la leyenda.

**4.- Colores de los sectores.**
1. Clic sobre el círculo (selecciona toda la serie) y de nuevo sobre el sector de **Granada** (queda seleccionado solo ese sector).
2. **Formato > Relleno de forma** (o **Relleno** en el panel) > **Rojo**.
3. Repite con Sevilla (**Amarillo**), Málaga (**Verde oscuro**) y Córdoba (**Gris claro**).

**5.- Área del gráfico.**
1. Clic en una zona vacía del gráfico (*Área del gráfico*), clic derecho > *Dar formato a área del gráfico*.
2. **Relleno y línea > Relleno > Relleno degradado**.
3. **Borde > Línea continua**, color **Rojo**.
4. Marca la casilla **Esquinas redondeadas**.

**6.- Quitar contornos.**
1. Clic sobre el círculo (serie) > **Formato > Contorno de forma > Sin contorno**.
2. Clic en la leyenda y de nuevo en cada entrada > **Formato > Contorno de forma > Sin contorno**.

**7.- Fondo de la leyenda.** Clic derecho en la leyenda > *Dar formato a leyenda* > **Relleno y línea > Relleno > Color sólido > Gris**.

**8.- Gráfica 2011/2012.**
1. Copia el gráfico (**Ctrl+C**) y pégalo (**Ctrl+V**); colócalo junto al anterior.
2. Clic derecho sobre el gráfico copiado > **Seleccionar datos**. En *Entradas de leyenda (series)* pulsa **Modificar** y en *Valores de la serie* selecciona **D4:D11**; en *Nombre de la serie* selecciona **D3**. Acepta.
3. Cambia el título a `Curso 2011/2012`. Los colores se mantienen.

**9.- Etiquetas con porcentaje y nombre.**
1. Clic en una etiqueta de datos > clic derecho > *Dar formato a etiquetas de datos*.
2. En **Opciones de etiqueta** marca **Nombre de categoría** y **Porcentaje**, y desmarca **Valor**.

**10.- Separar los quesos.**
1. Haz clic en el círculo y arrastra hacia fuera para separar todos los sectores a la vez (o usa **Explosión de punto** en *Opciones de serie*).
2. Clic en el sector de **Granada** y arrástralo un poco más hacia fuera que los demás.

**11.- Resto de gráficas.**
1. Copia el gráfico *Curso 2010/2011* dos veces. Cambia el rango de datos (**Seleccionar datos**) a **E4:E11** (2012/2013) y **G4:G11** (2014/2015), y cambia los títulos.
2. Copia el gráfico *Curso 2011/2012*. Cambia los datos a **F4:F11** (2013/2014) y el título.
3. Nombre de la serie: usa **E3**, **F3** y **G3** respectivamente.

---

## Solución Ejercicio 12

**1.- Media.** En **H4** escribe `=PROMEDIO(C4:G4)`, pulsa **Intro** y arrastra hasta **H11**.

**2.- Gráfico de columnas de Córdoba.**
1. Selecciona **C3:G4** (cursos y datos de Córdoba; sin la media).
2. **Insertar > Columna o barra > Columna agrupada** (2D).
3. Clic en el título y escribe `Universidad de Córdoba`.

**3.- Líneas, área de trazado y eje.**
1. Clic en las líneas de división horizontales y pulsa **Suprimir** (o **Diseño de gráfico > Agregar elemento > Cuadrícula > Horizontal principal primaria** para desactivarlas).
2. Clic derecho en el *Área de trazado* > *Dar formato a área de trazado* > **Relleno > Relleno degradado**.
3. En **Borde > Línea continua**, color **Negro**.
4. Clic derecho en el eje > *Dar formato al eje* > **Relleno y línea > Línea > Sin línea**.

**4.- Eje vertical.**
1. Clic derecho en el eje vertical > *Dar formato al eje* > **Opciones del eje**.
2. **Límites: Máximo = 4000**; **Unidades: Principal = 1000**.
3. En **Marcas de graduación > Tipo principal: Exterior**.

**5.- Columnas.**
1. Clic derecho sobre una columna > *Dar formato a serie de datos* > **Opciones de serie**: **Ancho del rango = 100 %**.
2. **Relleno y línea > Borde > Línea continua**, color **Negro**.

**6.- Área del gráfico.**
1. Clic derecho en el *Área del gráfico* > *Dar formato a área del gráfico*.
2. **Borde > Línea continua**, color **Verde oscuro**, **Ancho = 2 pto**.
3. **Relleno > Color sólido**, **Verde claro**.

**7.- Copiar el gráfico 7 veces.**
1. Copia y pega el gráfico siete veces.
2. En cada copia: clic derecho > **Seleccionar datos** y elige la fila de la universidad (por ejemplo **C5:G5** para Granada, con **B5** como nombre de serie).
3. Cambia el título (`Universidad de Granada`, etc.).

**8.- Eje vertical de cada gráfica.** En cada copia: clic derecho en el eje vertical > *Dar formato al eje* > **Opciones del eje** y escribe los valores de la tabla del enunciado (**Mínimo = 0**, **Máximo** y **Principal** según la universidad).

**9.- Colores.** En cada gráfica:
1. **Barras:** clic en una columna > **Relleno y línea > Relleno > Color sólido** (color de la tabla).
2. **Líneas de barras:** misma ventana > **Borde > Línea continua** (color de la tabla).
3. **Fondo de barras:** clic derecho en el *Área de trazado* > **Relleno > Color sólido** (color de la tabla).
4. **Fondo del área:** clic derecho en el *Área del gráfico* > **Relleno > Color sólido** (color de la tabla).

> Si "fondo de barras" y "fondo del área" te resultan confusos, comprueba el resultado en la imagen final del enunciado.

**10.- Etiquetas de datos.**
1. Clic en la gráfica > **Diseño de gráfico > Agregar elemento > Etiquetas de datos > Extremo externo**.
2. En la gráfica de **Málaga** elige **Extremo interno**.

---

## Solución Ejercicio 15

**1.- Total.** En **G7**:

```
=SUMA(C7;E7)
```

Intro y arrastra hasta **G13**.

**2.- % Mujeres.** En **H7**:

```
=(D7+F7)/G7
```

Intro y arrastra hasta **H13**.

**3.- % Hombres.** En **I7**:

```
=1-H7
```

Intro y arrastra hasta **I13**.

**4.- Formato porcentaje.** Selecciona **H7:I13** > **Inicio > Estilo porcentual** (`%`) > ajusta los decimales con **Aumentar/Disminuir decimales**.

**5.- Gráfico circular 3D.**
1. Selecciona **B6:B13** y, manteniendo **Ctrl**, **G6:G13**.
2. **Insertar > Gráfico circular > Circular 3D**.
3. **Diseño de gráfico > Diseños rápidos** y elige el que incluya **título, leyenda y valores en porcentaje**.

**6.- Modificaciones.**
1. Clic en el título y escribe `Alumnos matriculados por titulación`.
2. Clic derecho en la leyenda > *Dar formato a leyenda* > **Borde > Línea continua**, color **Negro**, **Ancho = 0,5 pto**.
3. Clic derecho en el área del gráfico > *Dar formato a área del gráfico*:
   - **Borde > Línea continua**, color **Negro**, **Ancho = 2 pto**.
   - Marca **Esquinas redondeadas**.
   - **Efectos > Sombra > Exterior** (elige una preestablecida).

**7.- Gráfico de barras 3D.**
1. Selecciona **B6:B13**, **Ctrl** + **H6:I13**.
2. **Insertar > Columna o barra > Barra 3D agrupada**.
3. **Diseño de gráfico > Diseños rápidos** y elige el que incluya **título y tabla de datos**.

**8.- Modificaciones.**
1. Título: `Alumnos matriculados por sexo y titulación`.
2. Clic derecho en el gráfico > **Seleccionar datos**. Selecciona *Serie 1* > **Modificar** > nombre de la serie: `%Mujeres`. Repite con *Serie 2*: `%Hombres`.
3. Área del gráfico: **Borde > Línea continua**, **Negro**, **2 pto**, **Esquinas redondeadas** y **Efectos > Sombra > Exterior**.

---

## Solución Ejercicio Minigráficos

**1.- Media.** En **H4** escribe `=PROMEDIO(C4:G4)` y arrastra hasta **H11**.

**2.- Minigráfico de líneas.**
1. Clic en **J4**.
2. **Insertar > Minigráficos > Línea**.
3. En *Rango de datos* selecciona **C4:G4**; *Rango de ubicación* queda en **$J$4**. Acepta.
4. Arrastra el controlador de relleno de **J4** hasta **J11**.

**3.- Minigráfico de columnas.** Repite en **K4** con **Insertar > Minigráficos > Columna** y arrastra hasta **K11**.

**4.- Formato del minigráfico de líneas.**
1. Selecciona **J4:J11** > pestaña **Minigráfico**.
2. Marca **Marcadores**, **Punto alto**, **Punto bajo**, **Primer punto** y **Último punto**.
3. **Color del minigráfico** > azul oscuro (#376092).
4. **Color de marcador** > para cada tipo de punto elige **Rojo**.

**5.- Comprobación.** Haz clic en cualquier celda de J4:J11 y K4:K11: debe aparecer en la pestaña **Minigráfico** el grupo al que pertenece. Si los minigráficos no están agrupados, usa **Agrupar** para aplicar el mismo formato a todos.
