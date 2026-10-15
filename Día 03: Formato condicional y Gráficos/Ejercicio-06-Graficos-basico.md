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

