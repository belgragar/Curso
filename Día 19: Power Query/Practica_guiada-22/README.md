# Práctica guiada 22: Limpieza integral de un registro semanal de ventas

## Contexto profesional

El departamento comercial ha recibido un archivo CSV denominado `Practica_Power_Query_Ventas.csv`. Este fichero presenta deficiencias graves: nombres de clientes con espacios, provincias escritas de forma inconsistente, importes guardados como texto con erratas y filas duplicadas. Se requiere construir una consulta en Power Query para dejar la tabla en perfecto estado.

```text
ESTRUCTURA DEL ARCHIVO BRUTO (CSV)
-----------------------------------------------------------------------------------------------------
ID_Venta;Fecha;Cliente;Provincia;Producto;Unidades;Importe;Comercial;Estado
1001;01/09/2026;  Ana García  ;madrid;Monitor;2;450,00;Carlos;ok
1002;02.09.2026;Lucía Martín;MADRID;Teclado;1;25,00;Laura;PENDIENTE
1003;03/09/2026;Pedro Gómez;Valencia;Ratón;5;ERROR;Carlos;ok
1003;03/09/2026;Pedro Gómez;Valencia;Ratón;5;75,00;Carlos;ok
;04/09/2026;  ;Sevilla;Impresora;1;180,00;Laura;pendiente

```

## Paso 1: Importación del archivo CSV

1. Abre un libro de Excel/Power BI en blanco.


2. Ve a **Datos/Inicio > Obtener datos > Desde un archivo > Desde texto/CSV**.


3. Selecciona `Practica_Power_Query_Ventas.csv` y pulsa **Importar**.


4. Comprueba que el delimitador sea **Punto y coma** y haz clic en **Transformar datos**.



## Paso 2: Eliminación de columnas superfluas

1. Observa la columna `Comercial`.


2. Haz clic derecho sobre la cabecera de la columna `Comercial` y selecciona **Quitar**.


3. En el panel derecho de *Pasos Aplicados*, haz clic derecho sobre el paso recién creado y cámbiale el nombre a: *`Eliminar_Columna_Comercial`*.



## Paso 3: Limpieza y normalización de textos

1. Selecciona la columna `Cliente`. Ve a **Transformar > Formato > Recortar**.


2. Selecciona la columna `Provincia`. Ve a **Transformar > Formato > Poner cada palabra en mayúscula**.


3. Selecciona la columna `Estado`. Haz clic derecho sobre la cabecera > **Reemplazar los valores**.


* Valor a buscar: `ok` | Reemplazar con: `OK`

* Repite el proceso para reemplazar `pendiente` y `PENDIENTE` por `Pendiente`.




## Paso 4: Depuración de duplicados y nulos

1. Selecciona únicamente la columna `ID_Venta`.


2. Ve a **Inicio > Quitar filas > Quitar duplicados**. (Observa cómo se elimina el registro repetido 1003).


3. Haz clic en la flecha desplegable de la cabecera `Cliente` y desmarca la casilla `(nulo)` o los espacios en blanco.



## Paso 5: Corrección de tipos de datos y gestión de errores

1. Selecciona la columna `Importe`. Cambia su tipo de dato a **Número decimal**.


2. Observa cómo la celda que contenía la palabra `"ERROR"` muestra un fallo de conversión (`Error`).


3. Ve a **Inicio > Quitar filas > Quitar errores**.



## Paso 6: Carga del resultado final en Excel/Power BI

1. Revisa el listado final de pasos aplicados.


2. En la pestaña **Inicio**, haz clic en **Cerrar y cargar**.


3. Verifica que los datos limpios aparecen volcados en una nueva hoja con formato de Tabla Estructurada.

## Reto: Unificación masiva de formatos de fecha inconsistentes

* **Escenario:** El departamento de administración recibe un archivo de proveedores denominado `Reto_CSV_Fechas.csv`. La columna `Fecha` contiene datos introducidos con formatos mezclados procedentes de diferentes delegaciones internacionales:


* `31/08/2026` (Formato español estándar)


* `01.09.2026` (Formato alemán con puntos)


* `2026-09-02` (Formato ISO)




* **Desafío:**
1. Conecta el archivo a Power Query sin modificar el fichero original en el disco.


2. Utiliza las herramientas de transformación de columna o la opción *Usar configuración regional* para lograr que toda la columna se convierta de forma estricta al tipo **Fecha** de Excel sin generar celdas de error.


3. Renombra los pasos aplicados asignando nombres explicativos.


4. Carga la tabla en Excel y comprueba que la columna permite aplicar los filtros cronológicos nativos de Excel (Años, Meses, Días).



