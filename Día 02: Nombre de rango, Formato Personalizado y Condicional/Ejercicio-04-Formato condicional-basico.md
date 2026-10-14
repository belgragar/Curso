# Ejercicio 04: Repaso formato condicional (Versión Ampliada y Completa)

El **Formato condicional** en Excel es una herramienta que analiza de forma automática los datos de tus celdas y les aplica un estilo visual (como colores, barras o iconos) únicamente cuando cumplen con las reglas o criterios que tú hayas definido previamente.

---

## Opciones del menú Formato condicional

* **Reglas para resaltar celdas**: Aplica un color de relleno o de texto a las celdas que cumplen condiciones matemáticas o de texto simples (como ser "mayor que", "menor que", "entre", valores duplicados o que contengan una palabra específica).


* **Reglas para valores superiores e inferiores**: Identifica de forma automática las celdas que se encuentran en los extremos numéricos de un rango, como los 10 elementos más altos, el 10% superior, los valores por debajo del promedio, entre otros.


* **Barras de datos**: Dibuja una barra horizontal de color dentro de la propia celda. La longitud de la barra es proporcional al valor de la celda en comparación con el resto de los datos, simulando un gráfico de barras miniatura.


* **Escalas de color**: Aplica un gradiente de dos o tres colores a un rango de celdas. Sirve para crear "mapas de calor", donde los tonos cambian gradualmente (por ejemplo, de verde a rojo) según la intensidad o el valor del número.


* **Conjuntos de iconos**: Coloca un símbolo gráfico pequeño (como flechas, semáforos, banderas o barras de clasificación) al lado del número para clasificar los datos en tres, cuatro o cinco niveles de rendimiento.


* **Nueva regla / Borrar reglas / Administrar reglas**: Opciones de control técnico que sirven para diseñar fórmulas personalizadas desde cero, eliminar los formatos condicionales de una hoja o editar las prioridades de las reglas que ya están creadas.



---

## Tabla de datos para el ejercicio (Formato TSV)

Copia este bloque de texto plano y pégalo directamente en un archivo con extensión `.tsv` o `.txt` (o cópialo a tu portapapeles y pégalo en la celda `A1` de Excel):

```tsv
ID	Empleado	Departamento	Ventas_Anuales	Progreso_%	Satisfaccion_Cliente	Puntualidad	Soporte_Tecnico	Calidad_Servicio	Estatus
101	Ana Gómez	Ventas	45000	0,95	4,8	4,5	4,2	4,6	Completado
102	Luis Martínez	Ventas	12000	0,35	2,1	2,0	1,9	2,2	Pendiente
103	María Rodríguez	Soporte	28000	0,70	3,9	4,0	3,8	3,5	En Proceso
104	Carlos Sánchez	Ventas	55000	1,10	4,5	4,9	4,7	4,8	Completado
105	Elena Pérez	Soporte	19000	0,50	3,2	3,0	3,5	3,1	Pendiente
106	Jorge López	Marketing	32000	0,80	4,2	4,1	4,0	4,0	Completado
107	Sofía Castro	Marketing	8000	0,20	1,5	1,8	2,0	1,7	Pendiente
108	David Ruiz	Ventas	41000	0,88	4,0	3,9	4,1	3,8	En Proceso
109	Lucía Fernández	Soporte	25000	0,65	3,7	3,6	3,8	3,6	En Proceso
110	Pedro Morales	Marketing	60000	1,25	4,9	5,0	4,8	5,0	Completado

```

---

# Ejercicio Práctico: Formato Condicional en Excel

Este ejercicio está diseñado para aplicar y dominar todas las herramientas visuales del menú **Formato condicional** utilizando una tabla de métricas de rendimiento.

## Instrucciones del Ejercicio

### Paso 1: Reglas para resaltar celdas

* **Objetivo:** Identificar rápidamente los estados de los proyectos.


* **Acción:** Selecciona la columna **Estatus**, ve a *Formato condicional > Reglas para resaltar celdas > Texto que contiene...*

* **Configuración:**
* Para la palabra `Pendiente`, aplica un relleno rojo claro con texto rojo oscuro.


* Para la palabra `Completado`, aplica un relleno verde claro con texto verde oscuro.





### Paso 2: Reglas para valores superiores e inferiores

* **Objetivo:** Destacar a los empleados con un rendimiento comercial sobresaliente.


* **Acción:** Selecciona la columna **Ventas_Anuales**, ve a *Formato condicional > Reglas para valores superiores e inferiores > 10% superior...*

* **Configuración:** Cambia el porcentaje al **20% superior** y asígnale un formato personalizado con texto en negrita y color azul.



### Paso 3: Barras de datos

* **Objetivo:** Visualizar el avance de las metas individuales de forma gráfica.


* **Acción:** Selecciona los valores numéricos de la columna **Progreso_%**. Ve a *Formato condicional > Barras de datos* y elige el estilo de **Relleno degradado (Barra azul o verde)**.


* **Configuración avanzada:** Para evitar que las barras se calculen basándose únicamente en el valor más alto de la columna, ve a *Formato condicional > Administrar reglas...*, selecciona la regla y haz clic en *Editar regla...*. En la sección **Valor máximo**, cambia el tipo a **Número** y escribe el valor **`1`** (que representa el 100%).


* **Resultado:** Haz clic en *Aceptar* y luego en *Aplicar*. Observa cómo ahora todas las celdas que igualan o superan el `1,00` (100% y 110%, 125%) llenan por completo el espacio de la celda.



### Paso 4: Escalas de color

* **Objetivo:** Crear un mapa de calor para evaluar el volumen general de ingresos.


* **Acción:** Selecciona los valores de la columna **Ventas_Anuales**, ve a *Formato condicional > Escalas de color*.


* **Configuración:** Selecciona la escala de **Verde, amarillo y rojo** (donde el verde representa los valores más altos y el rojo los más bajos).



---

## Práctica simultánea con Conjuntos de Iconos (Diferentes Tipos)

Para comprobar visualmente cómo actúan los distintos estilos de iconos en paralelo, aplica de forma independiente cada uno de los siguientes conjuntos sobre sus respectivas columnas de la tabla (asegurándote de que todas queden visibles a la vez en pantalla):

* **Columna Satisfaccion_Cliente (Caso A — Direccional):**
* **Acción:** Selecciona los valores de la columna y dirígete a *Formato condicional > Conjuntos de iconos > Direccional*. Selecciona las **3 flechas de color**.


* **Interpretación:** La flecha verde indica puntajes excelentes, la amarilla términos medios y la roja alertas.




* **Columna Puntualidad (Caso B — Formas / Semáforos):**
* **Acción:** Selecciona los valores de la columna, ve a *Conjuntos de iconos > Formas > 3 semáforos (sin marco)*.


* **Modificación avanzada:** Ve a *Formato condicional > Administrar reglas*, edita la regla y configura los límites basados en **Número**:
* 🟢 Verde si el valor es `>= 4,5`

* 🟡 Amarillo si el valor es `< 4,5` y `>= 3,5`

* 🔴 Rojo si el valor es `< 3,5`





* **Columna Soporte_Tecnico (Caso C — Indicadores / Banderas):**
* **Acción:** Selecciona los valores de la columna y cambia el conjunto a *Conjuntos de iconos > Indicadores > 3 banderas*.


* **Uso profesional:** Actúa como una señal de revisión inmediata para la dirección ante calificaciones bajas.




* **Columna Calidad_Servicio (Caso D — Valoración / Barras de clasificación):**
* **Acción:** Selecciona los valores de la columna y dirígete a *Conjuntos de iconos > Valoración > 5 barras de clasificación* (estilo señal de teléfono o cobertura).


* **Interpretación:** Al tener 5 niveles, este formato condicional distribuye de forma matemática las calificaciones de 1 a 5, mostrando de manera intuitiva el nivel de calidad sin necesidad de interpretar los decimales numéricos de un vistazo.
