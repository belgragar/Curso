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
