# Día 1 — Proyecto Integrador (Fase 1)

# Sistema Integral de Gestión Comercial y Análisis de Ventas para una PYME

## Objetivo general

Iniciar el desarrollo de un libro de trabajo que evolucionará a lo largo de las cinco primeras sesiones del módulo hasta convertirse en una herramienta profesional de gestión, análisis y simulación comercial.

## Datos iniciales

Descarga el archivo **Datos_Proyecto_Dia1.xlsx** incluido en el repositorio y guárdalo con el nombre:

```text
Sistema_Gestion_Comercial.xlsx
```

Este será el mismo libro de trabajo que utilizarás durante todo el proyecto.

La hoja **Base_Datos** contiene el registro inicial de operaciones comerciales realizadas por una empresa de distribución tecnológica.

## Desarrollo

Sobre la hoja **Base_Datos**:

1. Define los siguientes nombres de rango:

   * `Precio_Unitario`
   * `Cantidad`
   
2. Aplica un formato personalizado a la columna **Código_Operación** para mostrar los códigos con la estructura `OP-0000`.

3. Configura las siguientes reglas de formato condicional:

   * Resaltar en verde los importes superiores a **1.500 €**.
   * Resaltar en rojo los importes inferiores a **300 €**.
   * Resaltar toda la fila cuando el descuento aplicado sea superior al **10 %**.

4. Comprueba que el formato se aplica automáticamente al añadir nuevos registros.

Al finalizar esta fase dispondrás de una hoja `Base_Datos` limpia, legible y preparada para automatizar cálculos y realizar análisis.

---

# Día 2 — Proyecto Integrador (Fase 2)

# Automatización y depuración de la información comercial

## Objetivo general

Transformar los datos originales en información comercial estructurada mediante funciones lógicas y funciones de texto.

## Desarrollo

Trabajando sobre la misma hoja **Base_Datos**, añada las siguientes columnas al final de la tabla:

| Columna               | Descripción                                                                         |
| --------------------- | ----------------------------------------------------------------------------------- |
| Cliente_Normalizado   | Nombre del cliente sin espacios innecesarios y con formato correcto.                |
| SKU                   | Código generado automáticamente a partir de la categoría y del código de operación. |
| Precio_Final          | Precio tras aplicar el descuento correspondiente según el tipo de cliente.          |
| Descripción_Comercial | Texto descriptivo generado automáticamente con la información de la operación.      |
| Clasificación         | Clasificación del pedido mediante `SI.CONJUNTO` según el importe final.             |

Posteriormente:

1. Verifique alguna de las fórmulas utilizando ChatGPT o Claude.
2. Documente brevemente el *prompt* utilizado y la respuesta obtenida.

Al finalizar esta sesión la tabla contendrá información enriquecida generada automáticamente mediante fórmulas.

---

# Día 3 — Proyecto Integrador (Fase 3)

# Conversión en Base de Datos Profesional

## Objetivo general

Transformar la hoja de datos en una base de datos profesional utilizando Tablas Estructuradas de Excel.

## Desarrollo

1. Convierta toda la información de la hoja **Base_Datos** en una Tabla Estructurada denominada:

```text
Tbl_MasterVentas
```

2. Sustituya las referencias tradicionales por referencias estructuradas cuando sea necesario.

3. Cree una nueva hoja denominada **Dashboard_Síntesis**.

4. En ella muestre mediante referencias estructuradas:

* Número total de operaciones.
* Facturación total.
* Facturación media por operación.
* Número de clientes empresa.
* Número de clientes particulares.

5. Inserte un gráfico que represente la evolución de la facturación por fecha.

6. Compruebe que al añadir nuevos registros tanto los cálculos como el gráfico se actualizan automáticamente.

---

# Día 4 — Proyecto Integrador (Fase 4)

# Análisis dinámico de la actividad comercial

## Objetivo general

Construir herramientas de análisis que permitan responder rápidamente a preguntas de negocio mediante Tablas Dinámicas.

## Desarrollo

A partir de **Tbl_MasterVentas**:

1. Cree una nueva hoja denominada **Análisis_Dinámico**.

2. Elabore las siguientes Tablas Dinámicas:

### Informe 1

* Filas: Comercial
* Columnas: Canal
* Valores: Suma del Importe

### Informe 2

* Filas: Provincia
* Columnas: Categoría
* Valores: Suma del Importe

### Informe 3

* Filas: Tipo de Cliente
* Valores: Promedio del Importe

3. Configure todos los importes en formato moneda.

4. Incorpore segmentaciones de datos para filtrar por:

* Comercial
* Provincia
* Canal

5. Revise el libro mediante las herramientas de auditoría y utilice funciones de control como `SI.ERROR` cuando sea necesario.

6. Utilice un asistente de IA para interpretar alguno de los errores encontrados o validar una de las soluciones implementadas.

---

# Día 5 — Proyecto Integrador (Fase Final)

# Simulador de rentabilidad empresarial

## Objetivo general

Completar el sistema incorporando herramientas de análisis hipotético y optimización para facilitar la toma de decisiones empresariales.

## Desarrollo

Añada una nueva hoja denominada **Simulación**.

En ella construya un modelo que permita modificar los siguientes parámetros:

* Precio medio de venta.
* Cantidad media vendida.
* Costes fijos mensuales.
* Coste variable por operación.

El modelo deberá calcular automáticamente:

* Facturación prevista.
* Coste total.
* Beneficio esperado.

Posteriormente:

1. Utilice **Búsqueda de Objetivos** para determinar cuántas operaciones debe realizar la empresa para obtener un beneficio mensual de **25.000 €**.

2. Utilice **Solver** para calcular la combinación óptima entre:

* Precio medio.
* Cantidad vendida.

con el objetivo de maximizar el beneficio, respetando las siguientes restricciones:

* El precio medio no podrá superar **600 €**.
* La cantidad media deberá estar comprendida entre **5 y 20 unidades**.
* El beneficio deberá ser positivo.

Finalmente, interprete el informe generado por Solver y redacte una breve conclusión justificando si la solución obtenida resulta viable para la empresa.

---

## Resultado esperado al finalizar el proyecto

Al término del quinto día, el alumnado dispondrá de un único libro de trabajo, **Sistema_Gestion_Comercial.xlsx**, que integrará todos los contenidos del módulo:

* Base de datos comercial.
* Nombres de rango.
* Formatos personalizados y condicionales.
* Funciones lógicas y de texto.
* Tablas estructuradas.
* Referencias estructuradas.
* Dashboard con gráficos.
* Tablas dinámicas.
* Auditoría y control de errores.
* Búsqueda de Objetivos.
* Solver.

Este enfoque permite que cada sesión amplíe el trabajo realizado en la anterior, simulando la evolución real de una herramienta de gestión utilizada en una PYME y reforzando el aprendizaje progresivo de Excel mediante un único proyecto continuo.
