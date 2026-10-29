¡Hola! Excelente idea. Como docente de Excel, diseñar ejercicios basados en escenarios reales es la mejor forma de consolidar los conocimientos sobre **listados y matrices dinámicas** (`UNICOS`, `FILTRAR`, `ORDENAR` y `SECUENCIA`).

A continuación, presento un ejercicio práctico completo diseñado específicamente para que los alumnos apliquen de forma autónoma la teoría y la práctica progresiva realizada anteriormente.

---

# Ejercicio Práctico: Gestión Analítica del Camino de Santiago (Etapa Asturiana)

## 1. Contexto de Negocio

La **Oficina de Atención al Peregrino del Principado de Asturias** gestiona el registro de los caminantes que realizan el Camino Primitivo y el Camino del Norte a su paso por la región. La dirección necesita optimizar la recepción de datos y automatizar sus informes diarios de control.

Tu objetivo como analista de datos es construir un modelo dinámico en Excel que permita procesar los registros de paso por los albergues, identificar los flujos de peregrinos, filtrar atenciones por tipo de vía y generar listados auto-expandibles numerados para el control de aforos y estadísticas.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de datos y pégalo directamente en la celda **A1** de una hoja de Excel en blanco (utiliza la opción de pegado limpio o importación por punto y coma `;`):

```csv
ID_Registro;Peregrino;Ruta;Albergue_Etapa;Distancia_km;Fecha_Paso
REG-101;Mateo Alonso;Camino Primitivo;Oviedo;0,00;01/05/2026
REG-102;Sophie Dubois;Camino del Norte;Gijón;28,50;01/05/2026
REG-103;Lars Mueller;Camino Primitivo;Grado;25,60;02/05/2026
REG-104;Mateo Alonso;Camino Primitivo;Grado;25,60;02/05/2026
REG-105;Elena Rossi;Camino del Norte;Avilés;15,40;02/05/2026
REG-106;Sophie Dubois;Camino del Norte;Luarca;38,20;03/05/2026
REG-107;Lars Mueller;Camino Primitivo;Salas;22,10;03/05/2026
REG-108;Carmen Vega;Camino Primitivo;Oviedo;0,00;03/05/2026
REG-109;Elena Rossi;Camino del Norte;Cudillero;20,80;04/05/2026
REG-110;Carmen Vega;Camino Primitivo;Grado;25,60;04/05/2026

```

> **Indicación inicial para el alumno:** Selecciona el rango completo (**A1:F11**) y conviértelo en una **Tabla de Excel** oficial (pulsando `Ctrl + T`). Asígnale el nombre `T_Camino` en la pestaña *Diseño de tabla*.

---

## 3. Tareas a Resolver

### Bloque 1: Exploración Individual con Funciones Dinámicas

1. **Listado de Peregrinos Únicos:** En la celda **I2**, genera un listado sin duplicados de los nombres de los peregrinos registrados.
2. **Filtrado por Ruta Primitiva:** En la celda **K2**, extrae todos los registros completos pertenecientes exclusivamente al `"Camino Primitivo"`.
3. **Ordenación por Distancia:** En la celda **R2**, muestra la columna de distancias recorridas (`Distancia_km`) ordenadas de mayor a menor.
4. **Matriz de Control de Aforos (2D):** En la celda **T2**, utiliza la función `SECUENCIA` para generar una cuadrícula o tabla numérica de **5 filas y 4 columnas**, empezando en el número **100** y avanzando de **50 en 50** (simulando un panel de numeración de acreditaciones).

---

### Bloque 2: Informes Anidados y Automatizados

5. **Informe de Etapas del Camino del Norte (`ORDENAR` + `FILTRAR`):** A partir de la celda **I24**, genera un informe que extraiga los campos *Peregrino*, *Albergue_Etapa* y *Distancia_km* para las etapas del `"Camino del Norte"`, ordenado de mayor a menor distancia recorrida.
6. **Catálogo Único de Albergues (`ORDENAR` + `UNICOS`):** A partir de la celda **N24**, genera un listado de los albergues/etapas registrados, sin duplicados y ordenado alfabéticamente de la A a la Z.
7. **Control de Etapas Larga Distancia (Umbral):** A partir de la celda **P24**, extrae el *Peregrino*, la *Ruta* y la *Distancia_km* de aquellas etapas que superen los **20,00 km**, ordenadas alfabéticamente por el nombre del peregrino.
8. **Cuadro de Mando con Numeración Dinámica (`SECUENCIA` + `FILAS` + `#`):**
* En la celda **U24**, extrae el *Peregrino*, *Albergue_Etapa* y *Distancia_km* de la ruta `"Camino Primitivo"`, ordenados por etapa/albergue alfabéticamente.
* En la celda **T24**, crea una columna de numeración secuencial dinámica que se adapte automáticamente en altura al número exacto de filas que devuelva la consulta de la celda **U24**.



---

## 4. Guía de Solución Paso a Paso

### 🟢 Solución - Bloque 1: Uso Individual de Funciones

#### Tarea 1: Peregrinos únicos

* **Ubicación:** Celda `I2`
* **Fórmula:**
```excel
=UNICOS(T_Camino[Peregrino])

```


* **Explicación:** Evalúa la columna *Peregrino* de la tabla `T_Camino` y elimina las repeticiones, derramando los nombres únicos verticalmente.

#### Tarea 2: Filtro por Camino Primitivo

* **Ubicación:** Celda `K2`
* **Fórmula:**
```excel
=FILTRAR(T_Camino; T_Camino[Ruta] = "Camino Primitivo"; "Sin registros")

```


* **Explicación:** Recupera todas las columnas de la tabla donde el valor del campo *Ruta* coincide exactamente con `"Camino Primitivo"`.

#### Tarea 3: Ordenación descendente de distancias

* **Ubicación:** Celda `R2`
* **Fórmula:**
```excel
=ORDENAR(T_Camino[Distancia_km]; 1; -1)

```


* **Explicación:** Toma los valores de la columna *Distancia_km* y los ordena en sentido descendente (parámetro `-1`).

#### Tarea 4: Matriz bidimensional de acreditaciones

* **Ubicación:** Celda `T2`
* **Fórmula:**
```excel
=SECUENCIA(5; 4; 100; 50)

```


* **Explicación:** Genera una matriz de 5 filas por 4 columnas que inicia en 100 e incrementa de 50 en 50 (`100, 150, 200...`).

---

### 🟡 Solución - Bloque 2: Anidación e Informes Automáticos

#### Tarea 5: Informe del Camino del Norte por distancia

* **Ubicación:** Celda `I24`
* **Fórmula:**
```excel
=ORDENAR(FILTRAR(T_Camino[[Peregrino]:[Distancia_km]]; T_Camino[Ruta] = "Camino del Norte"); 3; -1)

```


* **Explicación:** `FILTRAR` selecciona las columnas desde *Peregrino* hasta *Distancia_km* para el `"Camino del Norte"`. A continuación, `ORDENAR` aplica un criterio descendente (`-1`) sobre la 3ª columna del rango resultante (*Distancia_km*).

#### Tarea 6: Catálogo ordenado de albergues

* **Ubicación:** Celda `N24`
* **Fórmula:**
```excel
=ORDENAR(UNICOS(T_Camino[Albergue_Etapa]))

```


* **Explicación:** `UNICOS` obtiene las etapas sin duplicados y `ORDENAR` las alinea automáticamente de la A a la Z.

#### Tarea 7: Etapas superiores a 20 km

* **Ubicación:** Celda `P24`
* **Fórmula:**
```excel
=ORDENAR(FILTRAR(T_Camino[[Peregrino]:[Distancia_km]]; T_Camino[Distancia_km] > 20); 1; 1)

```


* **Explicación:** `FILTRAR` evalúa la condición numérica `> 20`. Posteriormente, `ORDENAR` organiza la matriz devuelta basándose en la 1ª columna (*Peregrino*) en orden ascendente alfabético (`1`).

#### Tarea 8: Cuadro de mando con numeración adaptativa

* **Paso A (Datos en U24):**
```excel
=ORDENAR(FILTRAR(T_Camino[[Peregrino]:[Distancia_km]]; T_Camino[Ruta] = "Camino Primitivo"); 2; 1)

```


*(Filtra el Camino Primitivo y lo ordena alfabéticamente por la 2ª columna, Albergue_Etapa).*
* **Paso B (Índice dinámico en T24):**
```excel
=SECUENCIA(FILAS(U24#))

```


* **Explicación:** El operador `#` hace referencia a la matriz derramada desde `U24`. `FILAS(U24#)` calcula de forma automática cuántas filas tiene el informe y `SECUENCIA` genera una serie vertical perfectamente adaptada (`1, 2, 3...`). Si se añaden o eliminan registros en la tabla origen `T_Camino`, la serie se reajustará sola.

---

¿Qué te parece la estructura de la práctica? Si necesitas alguna modificación en los datos o en las fórmulas, dime y lo adaptamos al momento.
