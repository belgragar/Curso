# Ejercicio 05: Gráficos básicos

## 1. Contexto de Negocio

Trabajas como analista de datos junior en el departamento de control de gestión de la empresa asturiana *Comercial Asturias S.L.*, dedicada a la distribución mayorista de productos de consumo. La dirección general ha solicitado un informe visual exhaustivo y avanzado para la próxima junta directiva. Necesitan analizar multidimensionalmente el rendimiento de las sucursales, la evolución temporal detallada, la distribución de categorías, correlaciones complejas de rendimiento de agentes, análisis de flujos de caja y distribución geográfica de las operaciones. Tu objetivo es construir un modelo completo de gráficos en Excel que recoja todas estas perspectivas de negocio, modificando y transformando las representaciones visuales según los requerimientos técnicos solicitados.

---

## 2. Conjunto de Datos (Dataset)

Copia las siguientes tablas y pégalas en tu libro de Excel (puedes organizarlas en distintas hojas o pestañas, como `Datos_Ventas`, `Datos_Agentes` y `Datos_Geograficos`). Utiliza el **punto y coma (;)** como separador de columnas, asegurando la compatibilidad con el formato regional de España:

### Tabla 1: `Datos_Ventas` (Para análisis trimestral y transformación de gráficos)

```csv
Sucursal;Trimestre_1;Trimestre_2;Trimestre_3;Trimestre_4;Categoria;Ventas_Totales
Oviedo;12.500,50;14.200,00;13.100,25;15.800,00;Tecnología;55.600,75
Gijón;9.800,00;10.500,50;11.200,00;12.000,00;Hogar;43.500,50
Avilés;6.400,25;7.100,00;6.900,50;8.300,00;Moda;28.700,75
Mieres;4.200,00;4.800,00;5.100,00;5.900,00;Alimentación;20.000,00

```

### Tabla 2: `Datos_Agentes` (Para gráficos de dispersión, burbujas y jerarquías)

```csv
Agente;Horas_Resolucion;Satisfaccion_Cliente;Tickets_Totales;Rendimiento_Area
Ana Pérez;2,5;88,0;150;Soporte Técnico
Carlos Gómez;4,1;72,5;95;Logística
Elena Ruiz;1,8;94,0;210;Soporte Técnico
David Blanco;5,0;65,0;80;Atención Comercial
Lucía Fernández;3,2;85,0;135;Logística

```

### Tabla 3: `Datos_Financieros_Y_Geograficos` (Para gráficos de cascada, cotizaciones, superficie y mapas)

```csv
Concepto_Financiero;Importe_Euros;Mes;Latitud;Longitud;Region_Geografica
Ingresos Brutos;120.000,00;Enero;43,3603;-5,8448;Oviedo
Devoluciones;-8.500,50;Enero;43,5322;-5,6611;Gijón
Costes Operativos;-45.000,00;Enero;43,5542;-5,9248;Avilés
Margen Bruto;66.499,50;Enero;43,2517;-5,7733;Mieres
Valor_Max;110,50;Accion_A;43,3603;-5,8448;Oviedo
Valor_Min;102,20;Accion_A;43,5322;-5,6611;Gijón
Valor_Cierre;107,80;Accion_A;43,5542;-5,9248;Avilés

```

---

## 3. Tareas a Resolver

1. **Gráficos Base y Modificaciones Dinámicas:**
* Inserta un gráfico de columnas agrupadas con los datos de `Datos_Ventas` (Sucursales y Trimestres).


* Inserta un gráfico de líneas para la tendencia trimestral y modifícalo posteriormente para **convertirlo en un gráfico de áreas**.
* Inserta un gráfico circular y modifícalo para **convertirlo en un gráfico de anillo**.


2. **Ampliación con Nuevos Tipos de Gráficos de Negocio:**
* **Combinado:** Crea un gráfico combinado que muestre las `Ventas_Totales` por categoría en columnas y el porcentaje o valor medio en una línea secundaria.
* **Jerarquía:** Construye un gráfico de rectángulos (*Treemap* o proyección rectangular) para visualizar las ventas agrupadas por categoría y sucursal.
* **Dispersión y Burbuja:** Utiliza `Datos_Agentes` para insertar un gráfico de dispersión relacionando las `Horas_Resolucion` y la `Satisfaccion_Cliente`, transformándolo en un gráfico de burbujas asignando el tamaño a `Tickets_Totales`.


* **Cascada (*Waterfall*):** Utiliza los conceptos financieros de `Datos_Financieros_Y_Geograficos` para mostrar el impacto desde los ingresos brutos hasta el margen neto.
* **Embudo (*Funnel*):** Simula un embudo de conversión comercial con etapas (Contactos, Leads, Negociaciones, Cierres).
* **Cotizaciones, Superficie y Radial:** Inserta gráficos especializados (un gráfico radial o de araña para evaluar competencias de sucursales, una superficie 3D o cotizaciones si procede).
* **Mapas:** Configura un gráfico de mapas utilizando las coordenadas de latitud y longitud de las sucursales asturianas.



---

## 4. Guía de Solución Paso a Paso

### Tarea 1: Creación y Transformación Dinámica de Gráficos Básicos

1. **Gráfico de Columnas Agrupadas:** Selecciona el rango `A1:E5` de la tabla `Datos_Ventas`. Ve a la pestaña **Insertar** > grupo *Gráficos* > **Columna agrupada**. Personaliza el título como `Evolución Trimestral por Sucursal` y activa las *Etiquetas de datos* desde el botón `+` (Elementos del gráfico).


2. **Gráfico de Líneas a Gráfico de Áreas:**
* Selecciona de nuevo el rango `A1:E5`. Ve a **Insertar** > **Gráficos de líneas** > *Líneas con marcadores*.
* Para convertirlo en área: Haz clic derecho sobre el gráfico o selecciónalo, ve a la pestaña superior contextual **Diseño de gráfico** > **Cambiar tipo de gráfico** > selecciona la categoría **Área** (ej. *Área apilada* o *Área 2D*). Acepta para transformar la visualización manteniendo intacta la estructura de datos.


3. **Gráfico Circular a Gráfico de Anillo:**
* Selecciona las columnas de Categoría y Ventas Totales (`F1:G5`). Ve a **Insertar** > **Gráfico circular**.
* Para convertirlo en anillo: Haz clic en **Cambiar tipo de gráfico** dentro de la pestaña *Diseño de gráfico* y selecciona **Anillo**. Ajusta una paleta de colores corporativa.



### Tarea 2: Implementación de Gráficos Especializados y Avanzados

1. **Gráfico Combinado:**
* Selecciona los datos de `Datos_Ventas`. Ve a **Insertar** > **Gráficos recomendados** > pestaña *Todos los gráficos* > **Combinado**.
* Configura una serie (ej. `Trimestre_1`) como *Columna agrupada* y otra serie (ej. `Trimestre_4`) como *Líneas*, marcando la opción de **Eje secundario** para contrastar magnitudes de distinta escala.


2. **Gráfico de Jerarquía (Treemap):**
* Selecciona las columnas `Categoria`, `Sucursal` y `Ventas_Totales`. Ve a **Insertar** > grupo de gráficos de jerarquía > selecciona **Rectángulos (Treemap)**. Esto permitirá ver de forma jerárquica qué combinación de sucursal y categoría aporta más volumen al negocio.


3. **Gráfico de Dispersión y Burbujas:**
* Selecciona los datos de la tabla `Datos_Agentes` (`A1:D6`).
* Ve a **Insertar** > **Gráfico de dispersión (X, Y) o de burbujas** > selecciona **Burbujas 3D** o **Dispersión con burbujas**.
* Asegúrate en el asistente de selección de datos que el Eje X recoja `Horas_Resolucion`, el Eje Y `Satisfaccion_Cliente` y el tamaño de la burbuja esté vinculado a `Tickets_Totales`.




4. **Gráfico de Cascada (*Waterfall*):**
* Selecciona el rango de conceptos financieros e importes (`A1:B5` de la tercera tabla). Ve a **Insertar** > **Inserción de gráfico de cascada, embudo, cotizaciones, superficie o radial** > selecciona **Cascada**. Este gráfico es idóneo para ver cómo se desglosan los ingresos netos restando devoluciones y costes operativos.


5. **Gráfico de Embudo (*Funnel*):**
* Crea una pequeña tabla auxiliar con fases (ej: *Prospectos: 1.000*, *Cualificados: 500*, *Propuesta: 200*, *Cerrados: 50*). Selecciónala, ve a **Insertar** > **Cascada, embudo...** y elige **Embudo**.


6. **Gráfico Radial y Superficie:**
* Para el gráfico radial (araña), selecciona métricas de rendimiento por sucursal, ve a **Insertar** > **Radial**. Permite evaluar fortalezas multidimensionales de cada sede de Comercial Asturias.


7. **Gráfico de Mapas:**
* Selecciona las columnas de coordenadas y regiones geográficas (`Latitud`, `Longitud`, `Region_Geografica` y `Importe_Euros`). Ve a **Insertar** > **Mapa** (en versiones compatibles de Excel con mapas de Entidades Geográficas de Bing integrados) para representar visualmente el volumen de operaciones geolocalizado en Asturias.

¡Entendido perfectamente y corregido! Tienes toda la razón: en Excel, una vez que un nombre de rango ya ha sido creado, **no es posible editar su ámbito directamente** desde el Administrador de Nombres; para cambiar el ámbito de un nombre existente hay que eliminarlo y volver a crearlo (o definirlo inicialmente con el ámbito local deseado).

A continuación, te presento el **enunciado completo y actualizado** con la ampliación de conceptos del documento y la corrección técnica en el paso correspondiente para que puedas copiarlo y pegarlo directamente:

---
