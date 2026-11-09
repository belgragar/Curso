
## 0. Preparación común

1. Abrir **Power BI Desktop**.
2. Crear un informe en blanco y lo guardarlo como `Clase01_PowerQuery_Practicas.pbix`.
3. Tener a mano una carpeta local llamada `Datos_Clase01` donde se irán guardando los archivos que se descarguen (CSV, Excel, XML, etc.).

**Todas** las consultas deben crearse pulsando **“Transformar datos”** (no “Cargar”), para trabajar en el Editor de Power Query.


## 1. CSV – Ventas de una tienda

**Objetivo:** Importar un CSV, revisar tipos de datos, limpiar textos y filtrar registros.

1. En Power BI Desktop, ve a **Inicio → Obtener datos → Texto/CSV**.  
2. Selecciona `Ventas.csv` y pulsa **Transformar datos**.  
3. En el Editor de Power Query:
   - Comprueba que la primera fila se usa como encabezado.  
   - Cambia los tipos de datos:
     - `ID_Interno` → Texto.
     - `Fecha` → Fecha.  
     - `Unidades` → Número entero.  
     - `Precio` e `Importe` → Número decimal.  
   - Limpia la columna `Producto`:
     - Quitar espacios al inicio y final.  
     - Convertir todo a mayúsculas o minúsculas.  
   - Filtra las filas:
     - Elimina las filas con `Importe` vacío o nulo.  
     - Conserva solo las ventas con `Importe` mayor que 100.  
   - Elimina columnas que no vayas a usar (por ejemplo, un ID interno).  
4. Renombra la consulta como `stg_Ventas_CSV`.  
5. Renombra los pasos aplicados con nombres descriptivos (por ejemplo, “Filtrar importe mayor que 100”).  
6. Pulsa **Cerrar y aplicar**.

**Comprobación:** En la vista de Datos, verifica que:
- No hay valores de texto en columnas numéricas.
- No hay filas con importe vacío.
- La columna `Producto` está normalizada.

***

## 2. Excel – Clientes y segmentos

**Objetivo:** Importar un Excel, revisar tablas/hojas, corregir tipos de datos y crear una dimensión limpia.

1. En Power BI Desktop, ve a **Inicio → Obtener datos → Libro de Excel**.  
2. Selecciona `Clientes.xlsx` y pulsa **Transformar datos**.  
3. En el Navegador, marca la tabla/hoja `Clientes` y pulsa **Transformar datos**.  
4. En el Editor de Power Query:
   - Promueve encabezados si es necesario.  
   - Cambia los tipos de datos:
     - `IdCliente` → Texto.  
     - `Nombre`, `Ciudad`, `Segmento` → Texto.  
     - `FechaAlta` → Fecha.  
   - Limpia las columnas de texto:
     - Recorta espacios en `Nombre`, `Ciudad` y `Segmento`.  
     - Estandariza `Segmento` (todo en mayúsculas o todo en minúsculas).  
   - Elimina filas completamente vacías.  
   - Filtra para quitar posibles clientes sin `IdCliente`.  
5. Renombra la consulta como `dim_Clientes`.  
6. Renombra los pasos aplicados de forma clara.  
7. Pulsa **Cerrar y aplicar**.

**Comprobación:** En la vista de Datos:
- No hay segmentos duplicados por diferencias de mayúsculas/minúsculas.
- No hay espacios sobrantes en los nombres.
- `FechaAlta` es de tipo fecha.

***

## 3. XML – Catálogo de productos

**Objetivo:** Leer un archivo XML, navegar por nodos y convertir la estructura en una tabla.

1. En Power BI Desktop, ve a **Inicio → Obtener datos → Más… → XML**.  
2. Selecciona `Productos.xml` y pulsa **Transformar datos**.  
3. En el Editor de Power Query:
   - Navega por la estructura hasta localizar la tabla con los productos (normalmente un nodo `Producto`).  
   - Expande los campos:
     - `IdProducto`, `Nombre`, `Categoria`, `Precio`. (Puede haberlo hecho de forma automática) 
   - Cambia los tipos de datos:
     - `IdProducto`, `Nombre`, `Categoria` → Texto.  
     - `Precio` → Número decimal.  
   - Renombra la consulta como `dim_Productos_XML`.  
   - Renombra los pasos aplicados (por ejemplo, “Expandir nodo Producto”).  
4. Pulsa **Cerrar y aplicar**.

**Comprobación:** En la vista de Datos:
- Hay una fila por producto.
- `Precio` es numérico.
- No hay columnas con estructuras anidadas sin expandir.

***

## 4. JSON – API pública (usuarios ficticios)

**Objetivo:** Conectar a una API REST que devuelve JSON, expandir registros y obtener una tabla.

1. En Power BI Desktop, ve a **Inicio → Obtener datos → Web**.  
2. En la ventana, elige **URL** e introduce:  
   `https://jsonplaceholder.typicode.com/users`  
3. Pulsa **Aceptar** y luego **Transformar datos**.  
4. En el Editor de Power Query:
   - Verás una lista de registros.  
   - Convierte la lista en tabla (si Power Query no lo hace automáticamente).  
   - Expande los campos:
     - `id`, `name`, `username`, `email`, `city` (dentro de `address`), `company name` (dentro de `company`), etc.  
   - Cambia los tipos de datos:
     - `id` → Número entero.  
     - `name`, `username`, `email`, `city`, `company name` → Texto.  
   - Renombra la consulta como `dim_Usuarios_JSON`.  
   - Renombra los pasos aplicados.  
5. Pulsa **Cerrar y aplicar**.

**Comprobación:** En la vista de Datos:
- Hay una fila por usuario.
- Las columnas están planas (sin estructuras anidadas).
- Los tipos de datos son correctos.

***

## 5. Web – Tabla HTML de Wikipedia

**Objetivo:** Importar una tabla HTML con datos de audiencias, realizar la limpieza de caracteres en valores porcentuales y numéricos, y estructurar una tabla de hechos para su análisis en Power BI.

1. En Power BI Desktop, ve a **Inicio → Obtener datos → Web**.
2. Introduce la URL: https://es.wikipedia.org/wiki/Premios_Princesa_de_Asturias y pulsa **Aceptar**.
3. En el **Navegador**, busca y selecciona la tabla correspondiente a **Audiencias de televisión** (o la tabla que contenga las columnas *Año*, *Cadena*, *Espectadores* y *Cuota* / *Share*).
4. Pulsa **Transformar datos**.
5. En el Editor de Power Query:
   * **Promover encabezados:** Verifica que la primera fila se haya establecido correctamente como encabezado de la columna.
   * **Limpieza de columnas:** Conserva las columnas esenciales (`Año`, `Cadena`, `Espectadores` y `Cuota` / `Share`). Elimina columnas innecesarias.
   * **Tratamiento de la columna Espectadores:**
     * Elimina los puntos o espacios de separador de millares en caso de que existan.
     * Cambia el tipo de dato de `Espectadores` a **Número entero**.


   * **Tratamiento de la columna Cuota / Share (%):**
     * Asegúrate de que las comas o puntos se ajusten a tu separador decimal local.
     * Cambia el tipo de dato a **Número decimal** (o **Porcentaje**).


   * **Cambiar tipo de las demás columnas:**
     * `Año` → **Número entero** (o **Texto** si se usará únicamente como categoría).
     * `Cadena` → **Texto**.


   * **Filtrado de filas:**  Aplica un filtro para eliminar filas correspondientes a promedios, totales o valores nulos.


   * **Normalización de texto:** Aplica **Transformar → Formato → Recortar** en la columna `Cadena` para eliminar espacios accidentales.


6. Renombra la consulta como **`fact_Audiencias_Premios`**.
7. Renombra los pasos aplicados en el panel lateral con nombres descriptivos (ej. *"Quitar símbolo %"*, *"Cambiar tipo espectadores a entero"*).
8. Pulsa **Cerrar y aplicar**.

**Comprobación final:**
En la vista de **Datos**:

* Cada fila representa la audiencia registrada en una edición/año concreto.
* Las columnas `Espectadores` y `Cuota` son numéricas y permiten realizar promedios, máximos y agregaciones.
* No quedan caracteres de texto (como `%`) dentro de las columnas cuantitativas.

***

Aquí tienes el texto del ejercicio completamente redactado y adaptado para el nuevo fichero de Access que has adjuntado:

---

## 6. Access – Base de datos de Agencia de Viajes (Tours y Turistas)

**Objetivo:** Conectar a una base de datos Access, seleccionar tablas y aplicar transformaciones básicas en Power Query.

1. En **Power BI Desktop**, ve a **Inicio** → **Obtener datos** → **Más…** → **Base de datos de Access**. Selecciona el archivo de la agencia de viajes (`.accdb`) y pulsa **Aceptar**.


2. En la ventana del **Navegador**, marca la tabla `TURISTA` del modelo y pulsa **Transformar datos**.


3. En el **Editor de Power Query**:
   * **Revisa los tipos de datos** de cada columna (`ID_TURISTA`, `NOMBRE`, `DNI`, `EDAD`, `EXTRANJERO`, `CODIGO_TUR`, etc.).


   * **Cambia los que sean incorrectos** (p. ej., asegurar que `EDAD` sea número entero, `EXTRANJERO` sea un tipo Lógico/Booleano Verdadero/Falso, o `NOMBRE`/`DNI` y los identificadores sean de tipo texto).


   * **Renombra columnas** para mejorar su formato y legibilidad si lo consideras conveniente (por ejemplo, `NOMBRE` → `Nombre del Turista`, `CODIGO_TUR` → `Código de Tour`).


   * **Elimina columnas** que no vayas a utilizar para el análisis.


   * **Filtra registros** si es necesario (por ejemplo, filtrar solo los turistas donde `EXTRANJERO` sea igual a *Verdadero/True*, o por un rango de edad específico).

4. Tratamiento de la columna `Tours` (**tabla relacionada**):
   - **Expandir**, mediante en botón de las flechas opuestas, y seleccionar  únicamente los campos de la tabla de Tours que interesen (por ejemplo, el nombre/descripción del tour, destino o precio).
   - **Desmarcar la casilla** "Usar el nombre de la columna original como prefijo" para mantener los nombres de campos limpios. Pulsar **Aceptar**.
   - **Limpieza final**: Eliminar columnas irrelevantes o duplicadas que hayan surgido tras la expansión.

5. **Renombra la consulta** como `dim_Turistas_Access`.

6. Pulsa **Cerrar y aplicar**.

#### **Comprobación**

En la **Vista de Datos** de Power BI, verifica que:

* Los nombres de las columnas sean claros y profesionales.


* Los tipos de datos de cada campo sean los adecuados.


* No se hayan cargado columnas irrelevantes o vacías.

> **Nota:** Si en algún equipo no está instalado el motor de base de datos de Microsoft Access (Microsoft Access Database Engine), esta práctica puede realizarse mediante una demostración del docente o sustituirse por una fuente alternativa en Excel/CSV.

***

## 7. Carpeta – Consolidar varios CSV de ventas mensuales

**Objetivo:** Conectar a una carpeta, combinar archivos con la misma estructura y aplicar transformaciones comunes.

**1. Importar la carpeta de datos**
* En **Power BI Desktop**, ve a **Inicio** → **Obtener datos** → **Más…** → **Carpeta**.
* Selecciona la carpeta **`Ventas_Mensuales`** y pulsa **Combinar y transformar datos**.
* En la ventana emergente de vista previa, cambia el **Archivo de ejemplo** a **`Ventas_2024_04.csv`** para interpretar correctamente todas las columnas.
* Pulsa el botón **Aceptar**.
 
**2. Revelar columnas de meses posteriores (`Descuento` y `Precio unitario`)**
* Una vez dentro del **Editor de Power Query**, selecciona la consulta principal **`Ventas_Mensuales`**.
* En el panel derecho (**Pasos aplicados**), busca el paso llamado **"Se expandió Transformar archivo"** (o similar) y haz clic en el icono de la **tuerca/engranaje** ⚙️ situado a su derecha.
* En la ventana emergente, haz clic en **Cargar más** para que Power Query lea la estructura de todos los archivos de la carpeta.
* Asegúrate de marcar todas las columnas (incluidas **`Descuento`** y **`Precio unitario`**) y pulsa **Aceptar**.
 
**3. Unificar las columnas de precio (`Precio` vs. `Precio unitario`)**
* Ve a la pestaña **Agregar columna** en la barra superior y selecciona **Columna condicional**.
* Configura la nueva columna con estos parámetros:
* **Nombre de la columna:** `Precio_Final`
* **Si** `Precio` **es igual a** *(déjalo en blanco / null)* ➔ **Devolver valor de una columna:** `Precio unitario`
* **De lo contrario** ➔ **Devolver valor de una columna:** `Precio`
 
* Haz clic en **Aceptar**.
* Selecciona y elimina las dos columnas originales (`Precio` y `Precio unitario`), y renombra `Precio_Final` simplemente como **`Precio`**.

**4. Limpieza de datos, tipos y filtros**
* **Origen del archivo:** Renombra la columna `Source.Name` a **`Archivo`**.
* **Separadores decimales:** Selecciona las columnas `Precio`, `Importe` y `Descuento`. Haz clic derecho en el encabezado de cualquiera de ellas → **Cambiar tipo** → **Usar configuración regional...** Escoge la alternativa **Número decimal** con configuración regional **Inglés (Estados Unidos)** para que interprete el punto (`.`) correctamente como separador decimal.
* **Filtrar filas de totales e incompletas:**
* En la columna `Fecha`, despliega el filtro y desmarca la opción **Total**.
* En la columna `Importe`, despliega el filtro y desmarca la opción **(Nulo/Vacio)**.
 
* **Tipos de datos finales:** Confirma los tipos de datos en la barra superior:
* `Fecha` → **Fecha**
* `Unidades` → **Número entero**
* `Precio`, `Importe`, `Descuento` → **Número decimal**

 
* **Nombre de la consulta:** Haz clic derecho sobre la consulta en el panel izquierdo y renómbrala como **`fact_Ventas_Carpeta`**.

**5. Cargar datos**
* Ve a la pestaña **Inicio** y pulsa **Cerrar y aplicar**.
 

***

## 8. PDF – Registro de Ventas Industriales

**Objetivo:** Conectar a un archivo PDF con datos de ventas industriales, seleccionar la tabla detectada por Power BI, limpiar la columna de precios/importes con formato de moneda (`€`), ajustar separadores de millares y establecer los tipos de datos correctos.

1. En **Power BI Desktop**, ve a **Inicio → Obtener datos → Más… → PDF**.

2. Selecciona el archivo **`VentasIndustriales.pdf`** ubicado en tu carpeta `Datos_Clase01` y pulsa **Aceptar**.

3. En la ventana del **Navegador**:
* Selecciona la tabla detectada (por ejemplo, **`Table 001`** o **`Page 1`**) que contiene el detalle de las transacciones.
* Pulsa **Transformar datos**.

4. En el **Editor de Power Query**:
   * **Promover encabezados:** Verifica que la primera fila se haya promovido correctamente con los nombres de columna: `ID Transaccion`, `Fecha Venta`, `ID Cliente`, `Categoria`, `Producto`, `Precio Unitario`, `Unidades`, `Importe Total` y `Canal`.

   * **Tratamiento de precios e importes (`Precio Unitario` e `Importe Total`):**
     * En las columnas `Precio Unitario` e `Importe Total`, elimina los puntos de separador de millares (p. ej., `1.050,00 €` → `1050,00 €`).

     * Elimina el símbolo de moneda (`€`) y los espacios de ambas columnas utilizando **Transformar → Reemplazar los valores** o la opción de extracción de texto.

     * Cambia el tipo de dato de ambas columnas a **Número decimal** (asegurándote de que la coma `,` se reconozca como separador decimal).

   * **Tratamiento de códigos e identificadores:**
     * Configura `ID Transaccion`, `ID Cliente`, `Producto`, `Categoria` y `Canal` como tipo **Texto**.

     * **Fechas y cantidades:**
     * Cambia la columna `Fecha Venta` a tipo **Fecha**.

     * Cambia la columna `Unidades` a **Número entero**.

   * **Limpieza de texto:**
     * Aplica **Transformar → Formato → Recortar** en la columna `Producto` para eliminar espacios innecesarios al inicio o final del texto.
     * **Filtrado de filas:**
     * Aplica un filtro para eliminar posibles filas nulas o con valores incompletos.

   * Renombra la consulta como **`fact_Ventas_PDF`**.
   * Renombra los pasos aplicados en el panel derecho con nombres claros (ej. *"Quitar simbolo euro"*, *"Cambiar tipo precio a decimal"*).

   * Pulsa **Cerrar y aplicar**.


### Comprobación

En la vista de **Datos** de Power BI, verifica que:

* La columna `Precio Unitario` e `Importe Total` son de tipo numérico decimal y permiten realizar cálculos o sumas dinámicas (sin incluir el texto `€`).


* La columna `Fecha Venta` está correctamente reconocida con formato de fecha (`DD/MM/AAAA`).


* Cada fila corresponde a una transacción individual limpia y lista para su análisis.


---

