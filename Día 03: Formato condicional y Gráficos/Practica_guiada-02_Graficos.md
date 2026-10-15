# Práctica Guiada: Creación y Análisis Visual con Tipos de Gráficos en Excel M365

## 1. Contexto de Negocio

Trabajas en la empresa de distribución comercial **NorteLogística S.A.** La gerencia te ha provisto de varios bloques de datos operacionales (ventas comerciales, rendimiento de soporte técnico y balances financieros). A lo largo de esta práctica guiada, construirás los gráficos fundamentales y avanzados que conforman un cuadro de mando ejecutivo moderno en Excel M365.

---

## 2. Conjunto de Datos de Partida (Datasets)

Abre un libro nuevo en blanco en Excel M365 y nómbralo `Practica_Graficos_NorteLogistica.xlsx`. Crea tres pestañas diferentes y pega las siguientes tablas en cada una de ellas.

> **Ten en cuenta:** Los datos utilizan el punto y coma `;` como separador de columnas y coma `,` para decimales, adaptados a la configuración regional de España.

### Pestaña 1: `Ventas_Trimestrales` (Para columnas, barras, líneas, áreas, circular/anillo, combinados, jerarquías y mapas)

```csv
Zona;T_1;T_2;T_3;T_4;Sector;Ventas_Anuales
Santander;14.200,25;15.100,00;16.400,50;18.900,00;Logística;64.600,75
Bilbao;11.500,00;12.800,50;13.200,00;14.500,00;Distribución;52.000,50
San Sebastián;8.300,50;9.100,00;9.800,25;10.600,00;Tecnología;37.800,75
Pamplona;5.100,00;5.800,00;6.200,50;7.100,00;Alimentación;24.200,50

```

### Pestaña 2: `Operaciones_Soporte` (Para gráficos de dispersión, burbujas y radiales)

```csv
Tecnico;Tiempo_Respuesta_Hrs;Satisfaccion_Cliente;Incidencias_Mes;Area_Especialidad
Marta Gil;2,1;91,5;140;Sistemas
Jorge Sanz;4,5;74,0;85;Redes
Lucía Vega;1,6;96,0;195;Sistemas
Mario Conde;5,2;68,0;70;Atención
Elena Soto;3,0;87,5;120;Redes

```

### Pestaña 3: `Finanzas_Y_Mercado` (Para cascada, cotizaciones y embudo)

```csv
Concepto_Financiero;Euros;Variable_Stock;Valor_Alto;Valor_Bajo;Valor_Cierre;Fase_Proceso;Candidatos
Ingresos Operativos;150.000,00;Accion_Norte;125,50;115,20;121,80;Inscritos;500
Costes Personal;-60.000,00;Accion_Norte;124,00;118,10;122,50;Cribado CV;180
Costes Logística;-35.000,00;Accion_Norte;126,20;120,00;125,10;Entrevista;45
Beneficio Neto;55.000,00;Accion_Norte;128,50;123,40;127,90;Contratados;12

```

---

## 3. Desarrollo Guiado Paso a Paso

---

### Bloque 1: Gráficos Básicos de Comparación y Tendencia (Pestaña `Ventas_Trimestrales`)

#### Ejercicio 1.1: Gráfico de Columnas Agrupadas vs. Barras Agrupadas

1. Selecciona el rango `A1:E5` de la tabla `Ventas_Trimestrales`.
2. Ve a la pestaña **Insertar** > grupo *Gráficos* > **Insertar gráfico de columnas o de barras** > **Columna agrupada**.
3. Cambia el título del gráfico a `Comparativa Trimestral por Zonas`.
4. Haz clic en el botón `+` (Elementos del gráfico) y marca **Etiquetas de datos**.
5. **Crea la variante en Barras:** Copia el gráfico (`Ctrl + C`), pégalo al lado (`Ctrl + V`), ve a **Diseño de gráfico** > **Cambiar tipo de gráfico** y selecciona **Barra agrupada**.

> **Recuerda:** Las columnas son ideales para mostrar evolución o categorías cortas, mientras que las barras horizontales son mejores cuando los nombres de las categorías son largos o extensos.

---

#### Ejercicio 1.2: Gráfico de Líneas con Marcadores y Transformación a Áreas

1. Selecciona de nuevo el rango `A1:E5`.
2. Ve a **Insertar** > **Gráfico de líneas o de áreas** > **Líneas con marcadores**.
3. Modifica el título a `Tendencia de Ventas por Trimestre`.
4. **Transformación a Áreas:** Haz clic derecho sobre el gráfico > **Cambiar tipo de gráfico** > selecciona la categoría **Área** (elige *Área apilada*).

> **Ten en cuenta:** El gráfico de líneas muestra la tendencia continua en el tiempo, mientras que el gráfico de áreas apiladas permite visualizar, además de la tendencia, la aportación acumulada de cada zona al volumen total de ventas.

---

#### Ejercicio 1.3: Gráfico Circular transformado en Anillo

1. Mantén pulsada la tecla `Ctrl` y selecciona las columnas de **Zona** (`A1:A5`) y **Ventas_Anuales** (`G1:G5`).
2. Ve a **Insertar** > **Insertar gráfico circular o de anillos** > **Circular 2D**.
3. **Transformación a Anillo:** Ve a la pestaña **Diseño de gráfico** > **Cambiar tipo de gráfico** > **Anillo**.
4. Haz clic derecho sobre la serie de datos > **Dar formato a serie de datos** y ajusta el *Tamaño del agujero del anillo* al **60%**.

> **Recuerda:** Los gráficos circulares o de anillos solo representan **una sola serie de datos** y pocas categorías. Se utilizan para mostrar la proporción de las partes respecto a un todo.

---

### Bloque 2: Gráficos de Jerarquía, Combinados y Geográficos (Pestaña `Ventas_Trimestrales`)

#### Ejercicio 2.1: Gráfico Combinado con Doble Eje

1. Selecciona el rango `A1:E5`.
2. Ve a **Insertar** > **Gráficos recomendados** > pestaña **Todos los gráficos** > **Combinado**.
3. Configura la tabla inferior del asistente de la siguiente manera:
* **T_1, T_2, T_3:** *Columna agrupada*.
* **T_4:** *Línea con marcadores* y marca la casilla **Eje secundario**.


4. Nombra el gráfico `Evolución Trimestral y Cierre (T4 en Eje Secundario)`.

> **Ten en cuenta:** Usar un eje secundario te ayuda a representar series con escalas de magnitudes diferentes o a destacar una variable sobre las demás sin distorsionar la visualización.

---

#### Ejercicio 2.2: Gráfico de Jerarquía (Treemap o Rectángulos)

1. Selecciona las columnas de **Sector** (`F1:F5`), **Zona** (`A1:A5`) y **Ventas_Anuales** (`G1:G5`).
2. Ve a **Insertar** > **Insertar gráfico de jerarquía** > **Rectángulos (Treemap)**.
3. Asigna el título `Distribución de Ventas por Sector y Zona`.

> **Recuerda:** El gráfico de rectángulos muestra datos estructurados en niveles mediante bloques anidados. El tamaño de cada rectángulo es proporcional a la cifra de ventas.

---

#### Ejercicio 2.3: Gráfico de Mapas Geográficos

1. Selecciona las columnas de **Zona** (`A1:A5`) y **Ventas_Anuales** (`G1:G5`).
2. Ve a **Insertar** > **Mapas** > **Mapa coroplético**.
3. Comprueba cómo Excel M365 se conecta a Bing para identificar las provincias de Santander (Cantabria), Bilbao (Bizkaia), San Sebastián (Gipuzkoa) y Pamplona (Navarra), coloreando la densidad de ventas según la magnitud numérica.

---

### Bloque 3: Gráficos Estadísticos y Multivariables (Pestaña `Operaciones_Soporte`)

#### Ejercicio 3.1: Gráfico de Dispersión (X, Y)

1. Ve a la pestaña `Operaciones_Soporte` y selecciona los datos de `Tiempo_Respuesta_Hrs` (`B1:B6`) y `Satisfaccion_Cliente` (`C1:C6`).
2. Ve a **Insertar** > **Insertar gráfico de dispersión (X, Y) o de burbujas** > **Dispersión solo con marcadores**.
3. Añade títulos a los ejes desde el botón `+`:
* **Eje horizontal (X):** `Tiempo de Respuesta (Horas)`.
* **Eje vertical (Y):** `Satisfacción del Cliente (%)`.



> **Ten en cuenta:** El gráfico de dispersión evalúa la relación o correlación entre dos variables numéricas continuas. Observa cómo a mayor tiempo de respuesta, menor es la satisfacción.

---

#### Ejercicio 3.2: Gráfico de Burbujas (3 Variables)

1. Selecciona el rango `B1:D6` (`Tiempo_Respuesta_Hrs`, `Satisfaccion_Cliente`, `Incidencias_Mes`).
2. Ve a **Insertar** > **Dispersión (X, Y) o de burbujas** > **Burbujas**.
3. Haz clic derecho sobre una burbuja > **Seleccionar datos** > edita la serie para verificar:
* **Valores X de la serie:** `Tiempo_Respuesta_Hrs` (`B2:B6`).
* **Valores Y de la serie:** `Satisfaccion_Cliente` (`C2:C6`).
* **Tamaño de la burbuja de la serie:** `Incidencias_Mes` (`D2:D6`).



> **Recuerda:** El gráfico de burbujas añade una tercera dimensión numérica (representada por el área o tamaño de la burbuja).

---

#### Ejercicio 3.3: Gráfico Radial (Araña)

1. Selecciona los nombres de los técnicos (`A1:A6`) y las columnas de `Tiempo_Respuesta_Hrs` y `Satisfaccion_Cliente` (`B1:C6`).
2. Ve a **Insertar** > **Insertar gráfico de cascada, embudo, superficie o radial** > **Radial con marcadores**.
3. Titula el gráfico `Evaluación Multicriterio del Personal de Soporte`.

> **Ten en cuenta:** El gráfico radial es de gran utilidad para comparar perfiles o métricas de rendimiento en paralelo.

---

### Bloque 4: Gráficos Financieros y de Procesos (Pestaña `Finanzas_Y_Mercado`)

#### Ejercicio 4.1: Gráfico de Cascada (*Waterfall*)

1. Ve a la pestaña `Finanzas_Y_Mercado` y selecciona el rango de conceptos financieros y valores (`A1:B5`).
2. Ve a **Insertar** > **Insertar gráfico de cascada, embudo...** > **Cascada**.
3. Haz doble clic en la última barra correspondiente a **Beneficio Neto** y, en el panel lateral de formato, marca la casilla **Establecer como total**.

> **Recuerda:** El gráfico de cascada muestra cómo un valor inicial se incrementa o reduce a través de partidas intermedias hasta alcanzar un resultado final.

---

#### Ejercicio 4.2: Gráfico de Cotizaciones (Bursátil)

1. Selecciona el rango de datos bursátiles: `Variable_Stock`, `Valor_Alto`, `Valor_Bajo` y `Valor_Cierre` (`C1:F5`).
2. Ve a **Insertar** > **Todos los gráficos** > **Cotizaciones** > selecciona **Máximos, mínimos y cierre**.
3. Titula el gráfico `Evolución Bursátil - Acción Norte`.

> **Ten en cuenta:** Este gráfico requiere que los datos estén ordenados estrictamente en el orden de entrada que exige Excel (por ejemplo: Máximo, Mínimo y Cierre).

---

#### Ejercicio 4.3: Gráfico de Embudo (*Funnel*)

1. Selecciona los datos del proceso de selección: `Fase_Proceso` y `Candidatos` (`G1:H5`).
2. Ve a **Insertar** > **Insertar gráfico de cascada, embudo...** > **Embudo**.
3. Nombra el gráfico `Proceso de Selección de Personal (Conversión)`.

> **Recuerda:** El gráfico de embudo representa valores numéricos a través de varias etapas progresivas de un proceso decreciente.

---

## 4. Errores Frecuentes y Cómo Solucionarlos

Durante la realización de estos ejercicios, comprueba que evitas estos fallos comunes:

* **Incluir totales en el rango de origen:** Si incluyes filas de "Total" junto con los datos individuales, desvirtuarás las escalas de las barras o columnas. *Solución:* Excluye las filas de totales al seleccionar el rango.
* **Series y categorías invertidas:** Si la leyenda y el eje horizontal se muestran del revés, usa el botón **Cambiar entre filas y columnas** en la pestaña *Diseño de gráfico*.
* **Ejes truncados artificialmente:** Modificar el mínimo del eje de valores para que no empiece en cero puede exagerar visualmente diferencias pequeñas. *Solución:* Mantén el eje en cero para no distorsionar la realidad de los datos.
* **Valores guardados como texto:** Si los datos numéricos contienen espacios o comas incorrectas, Excel no podrá trazarlos. *Solución:* Asegúrate de dar formato de *Número* o *Moneda* a las celdas.

---

## 5. Resumen de Buenas Prácticas Profesionales

* **Simplicidad:** Mantén un diseño limpio, sin efectos 3D ni elementos de adorno innecesarios que dificulten la lectura.
* **Estructura dinámicamente vinculada:** Convierte siempre tus datos en **Tablas de Excel** (`Ctrl + T`) antes de insertar gráficos. Si agregas nuevas filas en el futuro, los gráficos se actualizarán automáticamente.
* **Etiquetado e identificación clara:** Asegúrate de incluir títulos descriptivos y las unidades de medida correspondientes en cada eje (`€`, `Horas`, `%`).
