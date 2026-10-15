# Práctica Guiada: Introducción Avanzada y Tipos de Gráficos en Excel M365

## 1. Contexto de Negocio para la Clase

*Trabajamos en la empresa de distribución comercial **NorteLogística S.A.** La gerencia nos ha provisto de varios bloques de datos operacionales (ventas comerciales, rendimiento de soporte técnico y balances financieros). A lo largo de esta sesión, construiremos conjuntamente los gráficos fundamentales y avanzados que conforman un cuadro de mando ejecutivo moderno en Excel M365.*

---

## 2. Conjunto de Datos de Partida (Datasets)

Pide a los alumnos que abran un libro nuevo en blanco en Excel M365 y que copien y peguen las siguientes tablas en diferentes pestañas o zonas de la hoja. *(Recuerda que los datos utilizan el punto y coma `;` como separador de columnas y están adaptados a la configuración regional de España).*

### Bloque A: `Ventas_Trimestrales` (Para gráficos básicos, columnas, líneas y áreas)

```csv
Zona;T_1;T_2;T_3;T_4;Sector;Ventas_Anuales
Santander;14.200,25;15.100,00;16.400,50;18.900,00;Logística;64.600,75
Bilbao;11.500,00;12.800,50;13.200,00;14.500,00;Distribución;52.000,50
San Sebastián;8.300,50;9.100,00;9.800,25;10.600,00;Tecnología;37.800,75
Pamplona;5.100,00;5.800,00;6.200,50;7.100,00;Alimentación;24.200,50

```

### Bloque B: `Operaciones_Soporte` (Para gráficos de dispersión y burbujas)

```csv
Tecnico;Tiempo_Respuesta_Hrs;Satisfaccion_Cliente;Incidencias_Mes;Area_Especialidad
Marta Gil;2,1;91,5;140;Sistemas
Jorge Sanz;4,5;74,0;85;Redes
Lucía Vega;1,6;96,0;195;Sistemas
Mario Conde;5,2;68,0;70;Atención
Elena Soto;3,0;87,5;120;Redes

```

### Bloque C: `Finanzas_Y_Mercado` (Para gráficos de cascada, cotizaciones y jerarquías)

```csv
Concepto_Financiero;Euros;Variable_Stock;Valor_Alto;Valor_Bajo;Valor_Cierre
Ingresos Operativos;150.000,00;Accion_Norte;125,50;115,20;121,80
Costes Personal;-60.000,00;Accion_Norte;124,00;118,10;122,50
Costes Logística;-35.000,00;Accion_Norte;126,20;120,00;125,10
Beneficio Neto;55.000,00;Accion_Norte;128,50;123,40;127,90

```

---

## 3. Desarrollo Guiado Paso a Paso (Explicación del Docente en Clase)

### Fase 1: Gráficos Básicos y Transformaciones Dinámicas en M365

1. **Gráfico de Columnas Agrupadas:**
* *Concepto a explicar:* Las columnas agrupadas permiten comparar de forma directa magnitudes discretas entre diferentes categorías (en este caso, zonas geográficas a lo largo de los trimestres).
* *Pasos:* Seleccionamos el rango `A1:E5` de la tabla `Ventas_Trimestrales`. Vamos a la pestaña **Insertar** > grupo *Gráficos* > **Columna agrupada**. Modificamos el título por `Comparativa Trimestral por Zonas` y activamos los valores mediante el botón de elementos flotantes `+` marcando **Etiquetas de datos**.


2. **Gráfico de Líneas transformado en Gráfico de Áreas:**
* *Concepto a explicar:* El gráfico de líneas es ideal para observar tendencias temporales continuas. Al transformarlo en un gráfico de áreas, logramos visualizar además el volumen acumulado de aportación de cada serie.
* *Pasos:* Seleccionamos de nuevo el rango `A1:E5`. Vamos a **Insertar** > **Gráfico de líneas con marcadores**. Una vez insertado, nos dirigimos a la pestaña superior contextual **Diseño de gráfico** > hacemos clic en el botón **Cambiar tipo de gráfico** > seleccionamos la categoría **Área** (elegimos *Área apilada*). Explicamos al alumnado cómo Excel M365 actualiza la estructura visual de manera fluida sin perder las referencias de los datos.


3. **Gráfico Circular transformado en Gráfico de Anillo:**
* *Concepto a explicar:* El gráfico circular representa partes de un todo, pero el gráfico de anillos ofrece una lectura más limpia y permite incorporar un hueco central para destacar datos globales o estética moderna.
* *Pasos:* Seleccionamos las columnas de Zona y Ventas Anuales (`A1:A5` combinada con `G1:G5`, o simplemente seleccionamos el rango `A1:A5` y `G1:G5` manteniendo pulsada la tecla `Ctrl`). Vamos a **Insertar** > **Gráfico circular** > *Circular 2D*. Inmediatamente, desde **Diseño de gráfico** > **Cambiar tipo de gráfico**, seleccionamos **Anillo**. Explicamos cómo cambiar el tamaño del agujero del anillo haciendo clic derecho sobre la serie y accediendo a *Formato de serie de datos*.



---

### Fase 2: Exploración de Nuevos Tipos de Gráficos Avanzados en Excel M365

Recorre con los alumnos la enorme variedad de familias de gráficos disponibles en la pestaña **Insertar** de Excel M365, explicando la utilidad de cada uno en entornos empresariales:

1. **Gráficos Combinados (Doble Eje):**
* *Qué hacer:* Selecciona los datos de ventas de `Ventas_Trimestrales`. Ve a **Insertar** > **Gráficos recomendados** > pestaña **Todos los gráficos** > **Combinado**.
* *Explicación docente:* Permite representar dos tipos de datos heterogéneos en un mismo espacio visual (por ejemplo, representar las ventas del Trimestre 1 en *Columnas* y las ventas del Trimestre 4 en una *Línea* situada sobre un **Eje secundario** para evitar distorsiones de escala).


2. **Gráficos de Jerarquía (Rectángulos o Treemap):**
* *Qué hacer:* Selecciona las columnas de Sector, Zona y Ventas Anuales. Ve a **Insertar** > icono de jerarquía > **Rectángulos (Treemap)**.
* *Explicación docente:* Muestra datos jerárquicos mediante bloques rectangulares anidados donde el tamaño del rectángulo es proporcional a su valor numérico, ideal forzar la visibilidad de qué sector aporta más ingresos.


3. **Gráficos de Dispersión y Burbujas:**
* *Qué hacer:* Selecciona la tabla `Operaciones_Soporte` (`A1:E6`). Ve a **Insertar** > **Gráfico de dispersión (X, Y) o de burbujas** > selecciona **Burbujas**. Configura el asistente para que el Eje X sea `Tiempo_Respuesta_Hrs`, el Eje Y sea `Satisfaccion_Cliente` y el tamaño de la burbuja represente `Incidencias_Mes`.
* *Explicación docente:* Excelente para analizar correlaciones estadísticas complejas de tres variables de forma simultánea.


4. **Gráfico de Cascada (*Waterfall*):**
* *Qué hacer:* Selecciona el rango `A1:B5` de la tabla `Finanzas_Y_Mercado`. Ve a **Insertar** > gráficos de cascada/embudo > **Cascada**.
* *Explicación docente:* Indispensable en contabilidad y finanzas para ver cómo un valor inicial (ingresos) va incrementándose o reduciéndose mediante partidas parciales hasta llegar a un resultado final (beneficio neto).


5. **Gráfico de Embudo (*Funnel*):**
* *Explicación docente:* Simula procesos secuenciales decrecientes (fases de un embudo de ventas, conversión de clientes o procesos de selección de personal).


6. **Gráficos Especializados (Cotizaciones, Superficie, Radial y Mapas):**
* *Gráfico de Cotizaciones:* Utiliza las columnas de Valores Alto, Bajo y Cierre de la tabla de finanzas para mostrar fluctuaciones financieras o bursátiles.
* *Gráfico Radial (Araña):* Útil para comparar múltiples métricas de rendimiento en paralelo para una misma sucursal o empleado.
* *Gráfico de Mapas:* Demuestra cómo Excel M365 aprovecha servicios geográficos integrados para pintar regiones geográficas (como provincias o comunidades autónomas) en función de los datos asociados.
