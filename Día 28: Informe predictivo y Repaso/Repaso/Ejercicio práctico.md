# EJERCICIO PRÁCTICO: GESTIÓN DE DATOS Y VISUALIZACIÓN 

## SUPUESTO PRÁCTICO EMPRESARIAL

> Trabajas en el departamento de administración de una empresa distribuidora de equipos informáticos. La dirección necesita estructurar el registro de operaciones comerciales del último trimestre en **Microsoft Excel** y elaborar un informe visual interactivo en **Power BI Desktop** para analizar el rendimiento por comercial y categoría de producto.

---

## PARTE 1: TRATAMIENTO Y ANÁLISIS DE DATOS EN EXCEL

Abre el libro de trabajo facilitado (`Ventas_Trimestre.xlsx`), guarda una copia con el nombre `Apellido_Nombre_IFCT56.xlsx` y realiza los siguientes apartados:

### 1.1. Estructuración como Tabla Oficial y Formato
* Convierte el rango de datos principal en una **Tabla de Excel** oficial (`Ctrl + T`) y asígnale el nombre técnico `TblVentas`.
* Aplica formato numérico de **Moneda (€)** con dos decimales a la columna de importes de venta.

### 1.2. Evaluación Condicional con Función Lógica
* Inserta una nueva columna al final de la tabla con el encabezado `Estado_Objetivo`.
* Introduce una fórmula utilizando la función **SI** que muestre el texto `"Conseguido"` cuando el importe de la venta sea superior a `1.500 €`, y `"En revisión"` en caso contrario.

### 1.3. Consulta Rápida mediante Función de Búsqueda y Preparación de Impresión
* En la zona auxiliar preparada en la hoja (celda `H2` para el código y celda `I2` para el resultado), utiliza la función **BUSCARX** (o `BUSCARV`) para que, al escribir un código de empleado en `H2`, se muestre automáticamente su nombre completo.
* **Configuración obligatoria para entrega en papel:** 
  1. Configura la página en **orientación horizontal** (*Disposición de página > Orientación > Horizontal*).
  2. Ajusta la escala para que toda la tabla y la zona de búsqueda quepan en **1 página de ancho por 1 de alto** (*Disposición de página > Ajustar área de impresión*).
  3. Inserta tu **Nombre y Apellidos** en el encabezado de página y manda imprimir la hoja.

---

## PARTE 2: MODELADO VISUAL E INTERACTIVO EN POWER BI DESKTOP

Abre **Power BI Desktop**, guarda el archivo como `Apellido_Nombre_IFCT56.pbix` y construye un informe de una sola página siguiendo estas indicaciones (**no es necesario crear medidas DAX**):

### 2.1. Importación y Limpieza Básica en Power Query
* Conecta Power BI con tu libro de Excel modificado (`Apellido_Nombre_IFCT56.xlsx`) y selecciona la tabla `TblVentas`.
* Accede al **Editor de Power Query** (*Transformar datos*), comprueba que los tipos de datos de cada columna son correctos (texto, fecha y número decimal) y pulsa *Cerrar y aplicar*.

### 2.2. Construcción de Objetos Visuales, Identificación e Impresión
* **Identificación del informe:** Inserta un **Cuadro de texto** en la parte superior del lienzo con el título del informe seguido de tu **Nombre y Apellidos**.
* **Tarjeta (Card):** Muestra la suma total del importe de ventas del trimestre con etiqueta clara (*Facturación Total*).
* **Gráfico de barras agrupadas:** Representa el total de ventas desglosado por *Categoría de Producto*, activando las etiquetas de datos.
* **Gráfico circular o de anillos:** Muestra la distribución porcentual de las ventas según el campo `Estado_Objetivo`.
* **Segmentador de datos (Slicer):** Añade un filtro interactivo por *Comercial* para permitir consultar los datos de cada vendedor de forma individual.
* **Configuración obligatoria para entrega en papel:** Exporta el informe a PDF (*Archivo > Exportar > Exportar a PDF*) o imprímelo directamente (*Archivo > Imprimir esta página*) y grapa las dos hojas impresas (Excel y Power BI) detrás de este enunciado.


---

### CONTROL DE ENTREGA FÍSICA

* [ ] **Anexo 1:** Hoja de cálculo de Excel impresa en formato horizontal (1 página) con nombre en el encabezado.
* [ ] **Anexo 2:** Lienzo de informe de Power BI impreso con cuadro de texto identificativo.
