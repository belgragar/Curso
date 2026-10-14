
# Ejercicio 04: Repaso formato condicional

El Formato condicional en Excel es una herramienta que analiza de forma automática los datos de tus celdas y les aplica un estilo visual (como colores, barras o iconos) únicamente cuando cumplen con las reglas o criterios que tú hayas definido previamente,

------------------------------

## Opciones del menú Formato condicional

* **Reglas para resaltar celdas**: Aplica un color de relleno o de texto a las celdas que cumplen condiciones matemáticas o de texto simples (como ser "mayor que", "menor que", "entre", valores duplicados o que contengan una palabra específica),
* **Reglas para valores superiores e inferiores**: Identifica de forma automática las celdas que se encuentran en los extremos numéricos de un rango, como los 10 elementos más altos, el 10% superior, los valores por debajo del promedio, entre otros,
* **Barras de datos**: Dibuja una barra horizontal de color dentro de la propia celda, La longitud de la barra es proporcional al valor de la celda en comparación con el resto de los datos, simulando un gráfico de barras miniatura,
* **Escalas de color**: Aplica un gradiente de dos o tres colores a un rango de celdas, Sirve para crear "mapas de calor", donde los tonos cambian gradualmente (por ejemplo, de verde a rojo) según la intensidad o el valor del número,
* **Conjuntos de iconos**: Coloca un símbolo gráfico pequeño (como flechas, semáforos, banderas o barras de clasificación) al lado del número para clasificar los datos en tres, cuatro o cinco niveles de rendimiento,
* **Nueva regla / Borrar reglas / Administrar reglas**: Opciones de control técnico que sirven para diseñar fórmulas personalizadas desde cero, eliminar los formatos condicionales de una hoja o editar las prioridades de las reglas que ya están creadas,

------------------------------

## Tabla de datos para el ejercicio (Formato TSV)

Copia este bloque de texto plano y pégalo directamente en un archivo con extensión ,tsv o ,txt para importarlo en tu Excel:

```tsv
ID	Empleado	Departamento	Ventas_Anuales	Progreso_%	Satisfaccion_Cliente	Estatus
101	Ana Gómez	Ventas	45000	0,95	4,8	Completado
102	Luis Martínez	Ventas	12000	0,35	2,1	Pendiente
103	María Rodríguez	Soporte	28000	0,70	3,9	En Proceso
104	Carlos Sánchez	Ventas	55000	1,10	4,5	Completado
105	Elena Pérez	Soporte	19000	0,50	3,2	Pendiente
106	Jorge López	Marketing	32000	0,80	4,2	Completado
107	Sofía Castro	Marketing	8000	0,20	1,5	Pendiente
108	David Ruiz	Ventas	41000	0,88	4,0	En Proceso
109	Lucía Fernández	Soporte	25000	0,65	3,7	En Proceso
110	Pedro Morales	Marketing	60000	1,25	4,9	Completado
```

------------------------------

# Ejercicio Práctico: Formato Condicional en Excel
Este ejercicio está diseñado para aplicar y dominar todas las herramientas visuales del menú **Formato condicional** utilizando una tabla de métricas de rendimiento,

## Instrucciones del Ejercicio

### Paso 1: Reglas para resaltar celdas*   

- **Objetivo:** Identificar rápidamente los estados de los proyectos,
- **Acción:** Selecciona la columna **Estatus**, Ve a *Formato condicional > Reglas para resaltar celdas > Texto que contiene,,,*
- **Configuración:** 
    *   Para la palabra `Pendiente`, aplica un relleno rojo claro con texto rojo oscuro,
    *   Para la palabra `Completado`, aplica un relleno verde claro con texto verde oscuro,
  
### Paso 2: Reglas para valores superiores e inferiores*   
- **Objetivo:** Destacar a los empleados con un rendimiento comercial sobresaliente,
- **Acción:** Selecciona la columna **Ventas_Anuales**, Ve a *Formato condicional > Reglas para valores superiores e inferiores > 10% superior,,,
-  **Configuración:** Cambia el porcentaje al **20% superior** y asígnale un formato personalizado con texto en negrita y color azul,

### Paso 3: Barras de datos
*   **Objetivo:** Visualizar el avance de las metas individuales de forma gráfica.
*   **Acción:** Selecciona los valores numéricos de la columna **Progreso_%**. Ve a *Formato condicional > Barras de datos* y elige el estilo de **Relleno degradado (Barra azul o verde)**.
*   **Configuración avanzada:** Para evitar que las barras se calculen basándose únicamente en el valor más alto de la columna, ve a *Formato condicional > Administrar reglas...*, selecciona la regla y haz clic en *Editar regla...*. En la sección **Valor máximo**, cambia el tipo a **Número** y escribe el valor **`1`** (que representa el 100%).
*   **Resultado:** Haz clic en *Aceptar* y luego en *Aplicar*. Observa cómo ahora todas las celdas que igualan o superan el 1,00 (100% y 110%, 125%) llenan por completo el espacio de la celda, permitiendo una visualización correcta del cumplimiento de la meta.

### Paso 4: Escalas de color

*   **Objetivo:** Crear un mapa de calor para evaluar el volumen general de ingresos,
*   **Acción:** Selecciona los valores de la columna **Ventas_Anuales**, Ve a *Formato condicional > Escalas de color*,
*   **Configuración:** Selecciona la escala de **Verde, amarillo y rojo** (donde el verde representa los valores más altos y el rojo los más bajos),

---

## Práctica con Conjuntos de Iconos (Diferentes Tipos)
La columna **Satisfaccion_Cliente** se utilizará para experimentar con tres enfoques visuales distintos del menú de iconos, Aplica cada uno de ellos borrando la regla anterior en *Formato condicional > Borrar reglas > Borrar reglas de las celdas seleccionadas*,

### Caso A: Iconos de Dirección (Flechas)

*   **Acción:** Selecciona la columna **Satisfaccion_Cliente** y dirígete a *Conjuntos de iconos > Direccional*, Selecciona las **3 flechas de color**,
*   **Interpretación:** La flecha verde hacia arriba indicará los puntajes excelentes, la flecha amarilla horizontal los términos medios y la flecha roja hacia abajo las alertas de mala atención,

### Caso B: Iconos de Formas (Semáforos)

*   **Acción:** Con las mismas celdas seleccionadas, cambia el estilo a *Conjuntos de iconos > Formas > 3 semáforos (sin marco)*,
*   **Modificación avanzada:** Ve a *Formato condicional > Administrar reglas*, selecciona la regla y haz clic en *Editar regla*, Configura los límites basados en **Número** (en lugar de porcentual):
    *   🟢 Verde si el valor es `>= 4,5`
    *   🟡 Amarillo si el valor es `< 4,5` y `>= 3,5`
    *   🔴 Rojo si el valor es `< 3,5`

### Caso C: Iconos de Indicadores (Banderas / Marcas)

*   **Acción:** Cambia el conjunto a *Conjuntos de iconos > Indicadores > 3 banderas*,
*   **Uso profesional:** Ideal para auditorías rápidas donde la bandera roja actúa como una señal de revisión inmediata para la dirección,

### Caso D: Iconos de Valoración (Barras de clasificación)

*   **Acción:** Cambia el conjunto a *Conjuntos de iconos > Valoración > 5 barras de clasificación* (estilo señal de teléfono/red),
*   **Interpretación:** Al tener 5 niveles, este formato condicional distribuirá de forma matemática la calificación de 1 a 5 estrellas/barras, mostrando de manera intuitiva el nivel de satisfacción sin necesidad de leer el decimal,
