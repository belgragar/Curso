# DÍA 4 - Práctica guiada paso a paso: Análisis de ventas y control de errores

Durante esta práctica vas a construir un pequeño informe de ventas.

La práctica está diseñada para realizarse **a la vez que se explican los conceptos de la unidad**, siguiendo el mismo orden que aparece en el desarrollo teórico:

1. Preparación del origen de datos.
2. Creación de una Tabla Dinámica.
3. Organización de los campos en FILAS, COLUMNAS, VALORES y FILTROS.
4. Configuración de los cálculos de los campos de valores.
5. Aplicación del formato numérico desde la configuración del campo.
6. Reorganización del informe.
7. Actualización de la Tabla Dinámica.
8. Auditoría de fórmulas.
9. Control de errores mediante `SI.ERROR()`.
10. Depuración asistida mediante IA.

### Datos de partida

Crea una hoja nueva denominada `Practica_Dia4`.

Copia el siguiente bloque y pégalo directamente en la celda `A1`.

```tsv
ID_Venta	Fecha	Vendedor	Región	Canal	Producto	Importe	Unidades
V-001	05/01/2026	Ana	Norte	Tienda	Ordenador	1250,00	2
V-002	08/01/2026	Carlos	Sur	Online	Monitor	480,00	4
V-003	12/01/2026	Marta	Norte	Tienda	Teclado	180,00	6
V-004	15/01/2026	Javier	Este	Online	Ordenador	1680,00	3
V-005	20/01/2026	Ana	Sur	Tienda	Monitor	720,00	5
V-006	24/01/2026	Carlos	Norte	Online	Teclado	210,00	7
V-007	03/02/2026	Marta	Este	Tienda	Ordenador	1320,00	2
V-008	07/02/2026	Javier	Sur	Online	Monitor	960,00	6
V-009	11/02/2026	Ana	Norte	Tienda	Teclado	150,00	5
V-010	16/02/2026	Carlos	Este	Online	Ordenador	1920,00	4
V-011	21/02/2026	Marta	Norte	Tienda	Monitor	760,00	5
V-012	26/02/2026	Javier	Sur	Online	Teclado	310,00	8
V-013	04/03/2026	Ana	Este	Tienda	Ordenador	1475,00	3
V-014	09/03/2026	Carlos	Norte	Online	Monitor	980,00	7
V-015	14/03/2026	Marta	Sur	Tienda	Teclado	240,00	6
V-016	19/03/2026	Javier	Norte	Online	Ordenador	2250,00	4
V-017	24/03/2026	Ana	Sur	Tienda	Monitor	1890,00	9
V-018	29/03/2026	Carlos	Este	Online	Teclado	455,00	10
V-019	03/04/2026	Marta	Norte	Tienda	Ordenador	1180,00	2
V-020	08/04/2026	Javier	Sur	Online	Monitor	2760,00	12
```

### Preparación del origen de datos

Antes de crear la Tabla Dinámica, comprueba que:

* La primera fila contiene encabezados.
* Todos los encabezados son diferentes.
* No existen filas completamente vacías.
* No existen columnas completamente vacías dentro del rango.
* No existen celdas combinadas.
* Las fechas son fechas.
* `Importe` y `Unidades` son valores numéricos.

Selecciona cualquier celda del rango y conviértelo en una **Tabla Estructurada** y asígnale el nombre `Tbl_Ventas_Guiada`

### Paso 1 — Crear la primera Tabla Dinámica

La primera pregunta que plantea la dirección es:

> **¿Cuánto ha vendido cada vendedor?**

1. Haz clic en cualquier celda de `Tbl_Ventas_Guiada`.
2. Ve a **Insertar > Tabla dinámica > De una tabla o rango**.
3. Selecciona **Nueva hoja de cálculo**.
4. Pulsa **Aceptar**.
5. Cambia el nombre de la hoja a `TD_Vendedores`

### Paso 2 — Trabajar con las áreas FILAS y VALORES

En el panel **Campos de tabla dinámica**:

1. Arrastra `Vendedor` a **FILAS**.
2. Arrastra `Importe` a **VALORES**.

Observa el resultado. La Tabla Dinámica debe mostrar una fila para cada vendedor y el importe total vendido. Comprueba que Excel ha utilizado `Suma de Importe`

### Paso 3 — Configurar el campo de valor

Ahora vamos a trabajar con la configuración del campo de valores.

1. En el área **VALORES**, abre el menú de `Suma de Importe`.
2. Selecciona **Configuración de campo de valor**.
3. Comprueba que está seleccionada `Suma`
4. Pulsa **Formato de número**.
5. Selecciona **Moneda**.
6. Utiliza el símbolo `€`
7. Utiliza dos decimales.
8. Acepta los cambios.

> **Importante:** no selecciones manualmente las celdas de la Tabla Dinámica para aplicar el formato desde **Inicio > Número**. El formato debe configurarse desde **Formato de número**, dentro de la configuración del campo de valor.

### Paso 4 — Añadir una segunda dimensión mediante COLUMNAS

Ahora queremos responder a una pregunta más completa:

> **¿Cuánto vende cada vendedor según el canal utilizado?**

En la misma Tabla Dinámica:

1. Arrastra `Canal` al área **COLUMNAS**.
2. Mantén `Vendedor` en **FILAS**.
3. Mantén `Importe` en **VALORES**.

Observa cómo cambia automáticamente el informe. Ahora tenemos:

* Vendedores verticalmente.
* Canales horizontalmente.
* Importes en el interior de la tabla.

### Paso 5 — Incorporar el área FILTROS

La dirección quiere analizar exclusivamente una región. La pregunta pasa a ser:

> **¿Cuánto ha vendido cada vendedor por canal en una región concreta?**

1. Arrastra `Región` al área **FILTROS**.
2. Abre el filtro de `Región`.
3. Selecciona únicamente: `Norte`

Observa cómo cambia todo el informe.

Después prueba con `Sur` y posteriormente con `Este`.

> **Observación:** el área **FILTROS** permite aplicar un criterio al conjunto del informe sin tener que modificar la organización de FILAS y COLUMNAS.

### Paso 6 - Cambiar el cálculo del campo de valores

Hasta ahora hemos utilizado `Suma de Importe`. Ahora queremos estudiar diferentes aspectos de las ventas.

En **VALORES**, abre `Suma de Importe` y selecciona **Configuración de campo de valor**.

Prueba sucesivamente los siguientes cálculos:

- `Suma` responde a: *¿Cuál es el volumen total de ventas?*
- `Promedio` responde a: *¿Cuál es el importe medio de una venta?*
- `Máx` responde a: *¿Cuál ha sido la operación de mayor importe?*
- `Recuento` responde a: *¿Cuántas operaciones existen?*

Después, vuelve a dejar el campo configurado como `Suma` y conserva el formato monetario.

### Paso 7 — Utilizar dos campos en VALORES

Ahora queremos comparar dos indicadores simultáneamente:

> **¿Cuánto ha vendido cada vendedor y cuántas operaciones ha realizado?**

En **VALORES**, mantén `Importe` y añade `ID_Venta`.

Observa que Excel puede mostrar `Suma de Importe` y `Recuento de ID_Venta`. De esta forma obtenemos dos indicadores diferentes en una misma Tabla Dinámica:

* Volumen económico.
* Número de operaciones.

### Paso 8 — Reorganizar la Tabla Dinámica

Ahora vamos a comprobar una de las principales ventajas de las Tablas Dinámicas: podemos cambiar la perspectiva del análisis sin modificar las fórmulas de los datos originales.

Elimina `Vendedor` del área **FILAS**.

Arrastra `Producto` a **FILAS**.

Mantén `Canal` en **COLUMNAS** e `Importe` en **VALORES**

La pregunta que responde ahora el informe es: *¿Qué productos generan mayor facturación según el canal?*

Después realiza una segunda reorganización:

```text
FILAS → Región
COLUMNAS → Producto
VALORES → Suma de Importe
```

La pregunta será: *¿Qué productos generan mayor facturación en cada región?*

> **Conclusión:** los mismos datos de origen pueden utilizarse para crear diferentes perspectivas de análisis simplemente reorganizando los campos.

### Paso 9 — Actualizar la Tabla Dinámica

Ahora vamos a comprobar que una Tabla Dinámica **no se actualiza automáticamente** simplemente porque cambien los datos de origen.

Añade al final de `Tbl_Ventas_Guiada` los siguientes registros:

```tsv
V-021	15/04/2026	Ana	Norte	Tienda	Ordenador	2100,00	3
V-022	20/04/2026	Carlos	Sur	Online	Monitor	850,00	5
V-023	25/04/2026	Marta	Este	Tienda	Teclado	320,00	9
```

Vuelve a la Tabla Dinámica y comprueba si los nuevos registros aparecen inmediatamente.

A continuación, actualiza la Tabla Dinámica mediante una de estas opciones:

* Clic derecho sobre la Tabla Dinámica > **Actualizar**.
* Pestaña **Analizar tabla dinámica > Actualizar**.
* Atajo: `Alt+F5`

Comprueba que las nuevas operaciones aparecen ahora en el informe.

> **Conclusión:** una Tabla Dinámica necesita actualizarse para incorporar cambios realizados en su origen cuando estos cambios no se reflejan automáticamente.

