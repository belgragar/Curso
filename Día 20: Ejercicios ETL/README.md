# Ejercicios ETL

## 0. Preparación común

1. Abrir **Power BI Desktop**.
2. Crear un informe en blanco y lo guardarlo como `Ejercicios_ETL.pbix`.
3. Tener a mano una carpeta local llamada `Datos_ETL` donde se irán guardando los archivos que se descarguen (CSV, Excel, XML, etc.).

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
   - Añadir columa personalizada
     - Crear una columna personalizada llamada `Importe_Nuevo` que sea igual al producto de las unidades por el precio unitario.
     - Borrar la columna `Importe` anterior.
     - Renombrar la columna `Importe_Nuevo` a `Importe`.
   - Filtra las filas:
     - Conserva sólo las ventas con `Importe` mayor que 100.  
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

## 7. Carpeta – Consolidación de Carpeta y Desdinamización (Unpivot) en Power Query

### Enunciado y Objetivo de Negocio

El departamento de ventas de la empresa recibe mensualmente un archivo CSV enviado por cada delegación. Todos los archivos tienen la **misma estructura de columnas**, pero presentan los datos matriciales: las ventas vienen divididas en columnas según el canal comercial (`Canal_Online`, `Canal_Tienda`, `Canal_Empresa`).

Tu objetivo es configurar una conexión a la carpeta compartida en **Power Query** para unificar automáticamente todos los archivos mensuales recibidos y **desdinamizar las columnas de los canales** para obtener una estructura relacional óptima en formato de lista (Filas: *ID_Venta*, *Fecha*, *Delegacion*, *Categoria*, *Canal*, *Importe*).

---

### 🗂️ Archivos de Ejemplo (Guardar juntos en una carpeta llamada `Ventas_Mensuales`)

Los tres archivos CSV adjuntos contienen la misma estructura estandarizada (delimitador: punto y coma `;`):

* **Ventas_Enero_2026.csv** 


* **Ventas_Febrero_2026.csv** 


* **Ventas_Marzo_2026.csv** 



---

### ⚙️ Procedimiento Paso a Paso en Power BI Desktop / Excel

#### Paso 1: Conexión a la Carpeta

1. Abre **Power BI Desktop** (o Excel) y dirígete a **Obtener datos > Desde un archivo > Carpeta**.


2. Busca la carpeta donde has guardado los 3 archivos CSV (`Ventas_Mensuales`) y haz clic en **Aceptar**.
3. En la ventana emergente, selecciona **Combinar > Transformar datos** (o haz clic en *Transformar datos* y luego en el icono de combinar archivos en la columna `Content`).



#### Paso 2: Validación de la Combinación

1. Power Query generará automáticamente una consulta de archivo de muestra y combinará los 3 ficheros.


2. Comprueba que las columnas unificadas son: `ID_Venta`, `Fecha`, `Delegacion`, `Categoria`, `Canal_Online`, `Canal_Tienda`, `Canal_Empresa`.

#### Paso 3: Transformación Avanzada (Desdinamizar / Unpivot)

1. Selecciona las columnas que **NO** quieres desdinamizar: pulsa `Ctrl` y haz clic en `Source.Name`, `ID_Venta`, `Fecha`, `Delegacion` y `Categoria`.
2. Haz clic derecho sobre el encabezado de cualquiera de las columnas seleccionadas y elige **Desdinamizar otras columnas** (o *Anulación de dinamización de otras columnas*).


3. Verás que las 3 columnas de canales se convierten en dos nuevas columnas:
* **Atributo:** Renombra esta columna como `Canal_Venta`.
* **Valor:** Renombra esta columna como `Importe`.


4. Aplica **Reemplazar valores** sobre la columna `Canal_Venta` para quitar el prefijo `Canal_` si deseas dejar solo `Online`, `Tienda` y `Empresa`.

#### Paso 4: Ajuste de Tipos de Datos y Carga

1. Cambia el tipo de dato de `Fecha` a **Fecha**.


2. Cambia el tipo de dato de `Importe` a **Número decimal** (o Moneda).


3. Renombra la consulta final como `fct_Ventas_Consolidadas`.


4. Haz clic en **Cerrar y aplicar**.

### ❓ Preguntas de Comprobación

1. **¿Qué ocurre si el mes que viene se añade el archivo `Ventas_Abril_2026.csv` a la carpeta?**
* *Respuesta:* Solo hay que pulsar en el botón **Actualizar**; Power Query leerá el nuevo archivo, lo anexará al resto y le aplicará los mismos pasos de desdinamización sin tener que rehacer nada.




2. **¿Por qué es preferible almacenar los datos en formato vertical (desdinamizado) en lugar de tener una columna por cada canal de venta?**
* *Respuesta:* Porque el motor de Power BI / Power Query funciona mediante modelos relacionales tabulares. Tener los canales en filas permite filtrar, segmentar por canal y crear medidas DAX simples sin necesidad de sumar múltiples columnas a mano.


```python
import pandas as pd

# Creamos el cuarto archivo correspondiente a Abril 2026
# Mantenemos exactamente la misma estructura de columnas que los 3 anteriores:
# ID_Venta, Fecha, Delegacion, Categoria, Canal_Online, Canal_Tienda, Canal_Empresa

data_abril = {
    'ID_Venta': ['VEN-013', 'VEN-014', 'VEN-015', 'VEN-016'],
    'Fecha': ['2026-04-02', '2026-04-11', '2026-04-19', '2026-04-26'],
    'Delegacion': ['Madrid', 'Valencia', 'Barcelona', 'Sevilla'],
    'Categoria': ['Periféricos', 'Informática', 'Servicios', 'Informática'],
    'Canal_Online': [1600.00, 2100.00, 750.00, 1300.00],
    'Canal_Tienda': [920.00, 1100.00, 500.00, 850.00],
    'Canal_Empresa': [2800.00, 3900.00, 1400.00, 2600.00]
}

df_abr = pd.DataFrame(data_abril)
file_name = 'Ventas_Abril_2026.csv'
df_abr.to_csv(file_name, index=False, sep=';', encoding='utf-8')

print(f"Archivo {file_name} generado con éxito.")


```

```text
Archivo Ventas_Abril_2026.csv generado con éxito.


```

Tu archivo CSV adicional está listo:


---

### 📥 Apartado Adicional: Comprobación de la Actualización Automática al Añadir un Nuevo Archivo

#### Paso 5: Comprobación de Carga Incremental (Actualización)

1. **Guarda el nuevo archivo:** Descarga el fichero `Ventas_Abril_2026.csv` y muévelo a la misma carpeta `Ventas_Mensuales` donde están guardados los archivos de Enero, Febrero y Marzo.


2. **Ejecuta la actualización en Power BI / Excel:**
* En **Power BI Desktop:** En la pestaña **Inicio** de la cinta de opciones, haz clic en el botón **Actualizar**.


* En **Excel:** Dirígete a la pestaña **Datos** y pulsa **Actualizar todo** (o haz clic derecho sobre la tabla cargada y selecciona *Actualizar*).




3. **Verificación de resultados:**
* Observa la columna `Fecha` o `ID_Venta` en tu modelo o tabla final.


* Comprobarás que los registros `VEN-013` a `VEN-016` correspondientes al mes de Abril se han incorporado automáticamente a la consulta.


* **Power Query** habrá aplicado de forma transparente todos los pasos configurados previamente (combinación, desdinamización de las columnas `Canal_Online`, `Canal_Tienda` y `Canal_Empresa`, y asignación de tipos de datos) sin necesidad de modificar el código ni repetir el trabajo manual.

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

