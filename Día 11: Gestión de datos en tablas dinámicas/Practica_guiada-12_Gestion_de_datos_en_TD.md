# Práctica Guiada 12: Gestión de datos en tablas dinámicas

## 1. Contexto de Negocio

La asociación *Artesanía Asturiana S.Coop.* agrupa a diversos talleres artesanales de toda la región. El departamento de gerencia necesita analizar la evolución comercial de las ventas trimestrales registradas durante el último año. Para ello, disponemos de una tabla de registros con las ventas de piezas y obsequios tradicionales.

El objetivo de esta práctica es transformar un informe estático en un cuadro de mando interactivo utilizando todas las herramientas de **gestión de tablas dinámicas** estudiadas en el manual: actualizar datos ante nuevas incorporaciones, agrupar fechas y tramos numéricos, aplicar filtros avanzados, conectar segmentaciones y escalas de tiempo, consultar el detalle subyacente y extraer valores de forma estructurada con funciones de referencia.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente contenido delimitado por punto y coma (`;`), pégalo en la celda `A1` de una nueva hoja de Excel y conviértelo en una tabla oficial de Excel (atajo `Ctrl + Q` o desde la pestaña *Insertar > Tabla*), asignándole el nombre `Tbl_VentasArtesania`:

```csv
ID_Venta;Taller;Modalidad;Fecha_Venta;Importe_Euros;Unidades
V-101;Madera & Tallas del Sueve;Madera;15/01/2025;145,50;3
V-102;Azabaches Villaviciosa;Joyería;20/01/2025;320,00;2
V-103;Alfarería de Llamas del Mouro;Cerámica;05/02/2025;85,00;4
V-104;Cuchillería Taramundi Tradicional;Cuchillería;12/02/2025;210,00;5
V-105;Lana y Telas de los Ancares;Textil;18/02/2025;115,25;3
V-106;Madera & Tallas del Sueve;Madera;02/03/2025;98,50;2
V-107;Azabaches Villaviciosa;Joyería;10/03/2025;450,00;1
V-108;Alfarería de Llamas del Mouro;Cerámica;22/03/2025;175,50;6
V-109;Cuchillería Taramundi Tradicional;Cuchillería;04/04/2025;310,00;4
V-110;Lana y Telas de los Ancares;Textil;15/04/2025;230,00;5
V-111;Madera & Tallas del Sueve;Madera;28/04/2025;410,00;8
V-112;Azabaches Villaviciosa;Joyería;05/05/2025;190,00;1
V-113;Alfarería de Llamas del Mouro;Cerámica;14/05/2025;125,00;3
V-114;Cuchillería Taramundi Tradicional;Cuchillería;02/06/2025;520,00;10
V-115;Lana y Telas de los Ancares;Textil;20/06/2025;89,00;2

```

---

## 3. Tareas a Resolver

1. **Creación inicial de la Tabla Dinámica:**
* Inserta una tabla dinámica a partir de `Tbl_VentasArtesania` en una nueva hoja llamada `Informe_Dinamico`.
* Sitúa el campo `Modalidad` en *Filas*, `Taller` en *Columnas* y la suma de `Importe_Euros` en *Valores*.


2. **Agrupación de Fechas y Valores:**
* Añade el campo `Fecha__Venta` (o `Fecha_Venta`) a las filas yagrupa las fechas automáticamente por **Meses** y **Trimestres**.


* Agrupa el campo de importes o unidades en tramos personalizados (si procede en el análisis secundario) o agrupa elementos específicos de talleres en familias si deseas ensayar la selección múltiple con `Ctrl`.




3. **Ordenación, Filtros y Segmentación Visual:**
* Ordena los talleres de Z a A según los valores de venta.
* Aplica un filtro de valor para mostrar únicamente las modalidades que superen los `300,00 €` en total ("Top 10" o filtro por valor superior).


* Inserta una **Segmentación de datos** para el campo `Modalidad` y una **Escala de tiempo** para el campo `Fecha_Venta`.




4. **Ver en Detalle y Extracción con `IMPORTARDATOSDINAMICOS`:**
* Haz doble clic sobre una de las celdas de importe totales para comprobar cómo Excel genera de forma automática una nueva hoja con el desglose detallado de esa celda.


* Fuera de la tabla dinámica (por ejemplo, en la celda `H2` de la hoja), redacta una fórmula manual empleando `=IMPORTARDATOSDINAMICOS(...)` para extraer de forma dinámica el importe total facturado por la modalidad de *"Cuchillería"* sin apuntar a la celda fija.




5. **Actualización de Datos:**
* Añade una nueva fila al final de tu tabla original en la hoja de datos (`V-116; Madera & Tallas del Sueve; Madera; 25/06/2025; 600,00; 12`).
* Comprueba que la tabla dinámica absorbe el nuevo rango y actualiza la tabla dinámica mediante el atajo de teclado o el menú contextual para verificar el nuevo recuento.





---

## 4. Guía de Solución Paso a Paso

* **Paso 1: Creación de la Tabla Dinámica**
1. Haz clic en cualquier celda dentro de `Tbl_VentasArtesania`.
2. Ve a la pestaña **Insertar > Tabla dinámica** y selecciona *Nueva hoja de cálculo*. Nómbrala `Informe_Dinamico`.
3. En el panel lateral derecho, arrastra:
* `Modalidad` y `Fecha_Venta` a **Filas**.
* `Taller` a **Columnas**.
* `Importe_Euros` a **Valores** (asegúrate de que esté configurado como *Suma de Importe_Euros* cambiando la *Configuración de campo de valor* a formato de moneda con separador de miles).




* **Paso 2: Agrupar Fechas**
1. Haz clic derecho sobre cualquiera de las fechas agrupadas en la columna de la tabla dinámica y selecciona **Agrupar...**
2. En la ventana emergente, selecciona **Meses** y **Trimestres** y pulsa *Aceptar*. Excel organizará jerárquicamente la cronología de las piezas artesanales.




* **Paso 3: Segmentaciones y Escalas de tiempo**
1. Selecciona la tabla dinámica y ve a la pestaña superior **Analizar tabla dinámica** (o *Dinámica de tabla > Analizar*).
2. Haz clic en **Insertar segmentación de datos**, marca la casilla `Modalidad` y pulsa *Aceptar*.
3. Vuelve a la pestaña de análisis y haz clic en **Insertar escala de tiempo**, seleccionando el campo `Fecha_Venta`. Esto te permitirá filtrar visualmente por periodos de tiempo (trimestres o meses).




* **Paso 4: Extracción de valores con `IMPORTARDATOSDINAMICOS**`
1. Haz clic en una celda vacía de la hoja (por ejemplo, `H4`) e introduce el signo `=`.
2. Haz clic directamente sobre una celda de valor dentro de la tabla dinámica que contenga un importe. Excel generará automáticamente una fórmula estructurada similar a esta:
`=IMPORTARDATOSDINAMICOS("Importe_Euros"; $A$3; "Modalidad"; "Cuchillería")`


3. Pulsa *Intro*. De este modo, si la tabla dinámica cambia de tamaño o de orden, el valor extraído en `H4` no se romperá, ya que busca conceptualmente el dato de la categoría.


* **Paso 5: Actualización de datos**
1. Vuelve a tu tabla de origen, añade la nueva venta (`V-116`) al final. Como el origen es una *Tabla de Excel* oficial, el rango se expande automáticamente.


2. Regresa a tu hoja `Informe_Dinamico`, haz clic derecho en cualquier celda de la tabla dinámica y pulsa **Actualizar** (o utiliza el atajo universal **`Alt + F5`**). Comprueba cómo se recalculan los totales incorporando los nuevos datos de artesanía asturiana.


