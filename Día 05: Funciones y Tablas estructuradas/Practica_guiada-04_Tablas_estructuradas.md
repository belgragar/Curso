# Práctica guiada — Construcción de un sistema dinámico de ventas

## 🎯 Objetivo de la práctica

Durante esta práctica construiremos, paso a paso y sobre una única hoja de Excel, un pequeño sistema de control de ventas para una empresa comercial.

La práctica se desarrollará **simultáneamente con la explicación de la teoría**. El docente realizará cada paso y los alumnos lo reproducirán en sus propios equipos.

Partiremos de un rango convencional y terminaremos con una **Tabla Estructurada conectada a un gráfico**, capaz de incorporar nuevos registros sin modificar manualmente las fórmulas ni el origen del gráfico.

A lo largo de la práctica trabajaremos:

* Conversión de un rango convencional en Tabla Estructurada.
* Nombre profesional de una tabla.
* Estilos y opciones de diseño.
* Columnas calculadas.
* Referencias estructuradas.
* Referencias de fila mediante `@`.
* Fila de totales.
* Fórmulas de resumen mediante referencias estructuradas.
* Creación de un gráfico vinculado a la tabla.
* Ampliación automática de la tabla.
* Actualización automática de fórmulas y gráficos al añadir nuevos registros.

---

## Parte 1. Preparar los datos

- **Crear la hoja de trabajo**: Crea una hoja nueva y asígnale el nombre `Ventas`. La hoja representará el registro de ventas de una empresa comercial.
- **Introducir los datos**: Copia el siguiente bloque y pégalo directamente en la celda **A1**.

> **Instrucción:** Pulsa **Copy** en el bloque y pégalo en Excel comenzando en `A1`.

```tsv
ID	Fecha	Vendedor	Categoría	Producto	Canal	Unidades	Precio Unitario (€)	Estado
V001	02/09/2026	Ana	Hardware	Teclado	Tienda Física	5	35,00	Completada
V002	02/09/2026	Carlos	Software	Microsoft 365	Online	8	72,00	Completada
V003	03/09/2026	Laura	Hardware	Ratón	Tienda Física	12	18,50	Completada
V004	03/09/2026	Miguel	Accesorios	Alfombrilla	Online	20	12,00	Pendiente
V005	04/09/2026	Ana	Hardware	Monitor 24"	Tienda Física	4	189,00	Completada
V006	04/09/2026	Carlos	Software	Windows 11	Online	6	145,00	Completada
V007	05/09/2026	Laura	Accesorios	Webcam	Online	10	45,00	Pendiente
V008	05/09/2026	Miguel	Hardware	Disco SSD	Tienda Física	7	89,90	Completada
V009	06/09/2026	Ana	Hardware	Teclado	Tienda Física	15	35,00	Completada
V010	06/09/2026	Carlos	Accesorios	Hub USB	Online	18	24,50	Pendiente
V011	07/09/2026	Laura	Software	Microsoft 365	Online	12	72,00	Completada
V012	07/09/2026	Miguel	Hardware	Monitor 24"	Tienda Física	6	189,00	Completada
V013	08/09/2026	Ana	Accesorios	Webcam	Online	9	45,00	Completada
V014	08/09/2026	Carlos	Hardware	Disco SSD	Tienda Física	11	89,90	Pendiente
V015	09/09/2026	Laura	Hardware	Ratón	Online	25	18,50	Completada
V016	09/09/2026	Miguel	Software	Windows 11	Online	4	145,00	Completada
V017	10/09/2026	Ana	Accesorios	Hub USB	Tienda Física	16	24,50	Completada
V018	10/09/2026	Carlos	Hardware	Monitor 24"	Online	8	189,00	Pendiente
V019	11/09/2026	Laura	Software	Microsoft 365	Tienda Física	15	72,00	Completada
V020	11/09/2026	Miguel	Hardware	Teclado	Online	10	35,00	Completada
```

---

## Parte 2. Convertir el rango en Tabla Estructurada

>Relación con la teoría: ¿qué diferencia existe entre un rango y una Tabla?
>
>Antes de convertir los datos, explica al alumnado que actualmente tenemos simplemente un **rango de celdas**.
>
>Si mañana añadimos una nueva venta debajo de la fila 21, un rango convencional no necesariamente incorporará ese registro a las fórmulas o gráficos que creemos posteriormente.

Ahora vamos a convertirlo en una **Tabla Estructurada**. Para crear la Tabla

1. Selecciona cualquier celda del rango.
2. Pulsa: `Ctrl + T`
3. Comprueba que Excel ha seleccionado todo el rango.
4. Activa: `La tabla tiene encabezados`
5. Pulsa **Aceptar**.

Obserba el cambio visual.

>Explica que no acabamos de aplicar simplemente un formato: hemos convertido el rango en un **objeto Tabla de Excel**.

---

## Parte 3. Asignar un nombre profesional

>Relación con la teoría: nombre de la Tabla

Para **cambiar el nombre**, selecciona cualquier celda de la tabla y:

1. Accede a **Diseño de tabla**.
2. Localiza el cuadro **Nombre de la tabla**.
3. Sustituye el nombre que Excel haya asignado por: `Tbl_Ventas`
4. Pulsa **Intro**.

>Explica que `Tbl_Ventas` será el nombre que utilizaremos posteriormente en las fórmulas.

> **Buena práctica:** evitar nombres como `Tabla1`, `Tabla2` o `Tabla3`. Un nombre profesional debe indicar claramente qué contiene la tabla.

---

## Parte 4. Personalizar el diseño: Cambiar el estilo

>Relación con la teoría: estilos y opciones de diseño

Desde **Diseño de tabla**, selecciona un estilo que permita distinguir claramente:

* encabezados;
* filas;
* columnas;
* datos.

A continuación, prueba las opciones:

* **Filas con bandas**
* **Primera columna**
* **Última columna**

Observa cómo cambia la presentación.

>Explica:
>- Que la **previsualización activa** es una función que muestra en tiempo real cómo quedará una cambio de formato con sólo pasar el ratón por encima.
>- Que estas opciones modifican la **presentación de la Tabla**, pero no los datos almacenados.

---

## Parte 5. Crear una columna calculada

1. **Añadir la columna `Importe`**. Vamos a calcular automáticamente el importe de cada venta. En la primera columna libre situada a la derecha de **Estado**, escribe como encabezado: `Importe`. La tabla debería incorporar automáticamente la nueva columna.
2. **Crear la fórmula utilizando referencias estructuradas**: En la primera celda de la columna **Importe**, escribe:
```excel
=[@Unidades]*[@[Precio Unitario (€)]]
```
Pulsa **Enter**.

Obserba qué ocurre. Excel debería completar automáticamente toda la columna.

>Detenerse aquí para explicar
>
>Esta es una de las características fundamentales de las Tablas Estructuradas: **una fórmula introducida en una columna puede convertirse automáticamente en una columna calculada.**
>
>Compara:
> - **Rango convencional**: `=G2*H2`
> - **Tabla Estructurada**: `=[@Unidades]*[@[Precio Unitario (€)]]`
>
>Explica que:
>* `[@Unidades]` significa **Unidades de esta misma fila**.
>* `[@[Precio Unitario (€)]]` significa **Precio Unitario de esta misma fila**.
>* `@` representa la **fila actual**.

---

## Parte 6. Añadir una segunda columna calculada 

1. **Crear la columna IVA**: Añade una nueva columna denominada `IVA`. Utilizaremos un IVA del 21 %. 
2. **Crear la fórmula**: En la primera fila escribe:

```excel
=[@Importe]*0,21
```

Pulsa **Enter**. Comprueba nuevamente que Excel completa automáticamente toda la columna.

---

## Parte 7. Crear el Total Factura

1. **Crear la columna Total**: Añade una columna denominada `Total Factura`. 
2. Introduce:

```excel
=[@Importe]+[@IVA]
```

Excel volverá a crear automáticamente una columna calculada.

La tabla ya contiene ahora:

* datos originales;
* Importe;
* IVA;
* Total Factura.

---

## Parte 8. Utilizar referencias estructuradas para obtener información global

Hasta ahora hemos utilizado referencias estructuradas para realizar cálculos **fila por fila**. Ahora utilizaremos referencias estructuradas para realizar cálculos sobre **toda una columna**.

1. **Calcular la facturación total**. En una celda situada fuera de la tabla escribe:

```excel
=SUMA(Tbl_Ventas[Total Factura])
```

>Explica la estructura:
>
>```text
>Tbl_Ventas
>     ↓
>Nombre de la tabla
>
>[Total Factura]
>     ↓
>Nombre de la columna
>```

La fórmula significa:

> "Suma todos los valores de la columna Total Factura de la tabla Tbl_Ventas".

2. **Calcular el número de operaciones**. En otra celda escribe:

```excel
=CONTARA(Tbl_Ventas[ID])
```

>Explica que podemos utilizar una referencia estructurada para contar los registros de la tabla.

3. **Calcular la venta media**. En otra celda escribe:

```excel
=PROMEDIO(Tbl_Ventas[Total Factura])
```

Ahora disponemos de tres indicadores:

| Indicador             | Fórmula                                |
| --------------------- | -------------------------------------- |
| Facturación total     | `=SUMA(Tbl_Ventas[Total Factura])`     |
| Número de operaciones | `=CONTARA(Tbl_Ventas[ID])`             |
| Venta media           | `=PROMEDIO(Tbl_Ventas[Total Factura])` |

---

## Parte 9. Activar la Fila de Totales

>Relación con la teoría: Fila de Totales

### Paso 13. Activar la Fila de Totales

Selecciona la tabla.

En **Diseño de tabla**, activa `Fila de totales`

Aparecerá una nueva fila al final de la tabla.

### Paso 14. Configurar los cálculos

- En la columna **Total Factura**, utiliza el desplegable de la fila de totales y selecciona `Suma`
- En **Importe**, selecciona `Suma`
- En **Unidades**, selecciona `Suma`
- En **ID**, selecciona `Recuento`

Compara estos resultados con las fórmulas que hemos creado anteriormente.

>**Pregunta para los alumnos:** ¿Qué ventaja tiene la Fila de Totales frente a escribir manualmente una fórmula `SUMA` debajo de los datos?
>
>La respuesta esperada es que la Tabla proporciona una fila de resumen integrada y que sus cálculos se adaptan al crecimiento de la tabla.

---

## Parte 10. Crear un gráfico vinculado a la Tabla

Ahora vamos a utilizar la Tabla como origen de un gráfico.

### Paso 15. Crear el gráfico

Selecciona cualquier celda de `Tbl_Ventas`.

Vete a: **Insertar → Gráficos → Columnas**

Selecciona un gráfico de columnas, puede hacerse desde la opción de **Gráficos recomendados**.

Excel utilizará la Tabla como origen de datos.

---

### Paso 16. Configurar y personalizar el gráfico

Ahora vamos a modificar el gráfico para que represente información útil y no sea simplemente un gráfico generado automáticamente por Excel.

#### 16.1 Seleccionar los datos que queremos representar

El objetivo será representar **la facturación de cada venta**.

En el gráfico queremos:

* **Eje horizontal (categorías):** `ID`
* **Eje vertical (valores):** `Suma de Total Factura`

Excel mostrará el campo numérico como **Suma de Total Factura** porque los gráficos agrupan y agregan los valores numéricos.

En este caso, cada `ID` corresponde a una única venta, por lo que:

**Suma de Total Factura = Total Factura de esa operación**

Si Excel ha seleccionado campos adicionales que no necesitamos:

1. Selecciona el gráfico.
2. Accede a **Diseño de gráfico → Seleccionar datos**.
3. En **Entradas de leyenda (series)**, elimina las series que no correspondan a `Suma de Total Factura`.
4. Comprueba que la única serie representada sea `Suma de Total Factura`
5. En **Etiquetas del eje horizontal**, compruebe que se utilice `ID`

El gráfico debe representar, por tanto:

```text
ID → Suma de Total Factura
```

#### 16.2 Cambiar el título

Selecciona el título del gráfico y sustitúyelo por `Facturación por operación`

El título debe indicar claramente **qué información está mostrando el gráfico**. Evita títulos genéricos como `Gráfico 1` o `Ventas`.

#### 16.3 Comprobar los ejes

Comprueba que:
* El eje horizontal representa las **operaciones (ID)**.
* El eje vertical representa el **importe de facturación**.

Añade títulos a los ejes si la versión de Excel utilizada dispone de esta opción:

**Diseño de gráfico → Agregar elemento de gráfico → Títulos de los ejes**

Utiliza:
- **Eje horizontal:** `Operación`
- **Eje vertical:** `Total Factura (€)`

#### 16.4 Añadir etiquetas de datos

Añade las etiquetas de datos:

**Diseño de gráfico → Agregar elemento de gráfico → Etiquetas de datos → Extremo externo**

De esta forma podremos conocer directamente el importe de cada operación sin tener que aproximarlo visualmente sobre el eje.

#### 16.5 Dar formato a los valores

Los valores del eje vertical y las etiquetas de datos representan importes monetarios. Configura el formato para que los valores se muestren como euros y con dos decimales. Por ejemplo, `1.250,00 €` y no `1250`,

#### 16.6 Modificar el tamaño del gráfico

Aumenta el tamaño del gráfico para que:
* se puedan leer todos los ID;
* las etiquetas de datos sean visibles;
* el título quede claramente separado;
* no se solapen los elementos.

Coloca el gráfico debajo de la tabla.

#### 16.7 Comprobación final

Antes de continuar, el gráfico debería cumplir estas condiciones:

| Elemento       | Configuración             |
| -------------- | ------------------------- |
| Tipo           | Columnas                  |
| Título         | Facturación por operación |
| Eje horizontal | ID                        |
| Eje vertical   | Total Factura (€)         |
| Serie          | Total Factura             |
| Etiquetas      | Valores de Total Factura  |
| Ubicación      | Debajo de la tabla        |

> **Pregunta para los alumnos:** ¿Qué ocurriría con el gráfico si mañana incorporamos nuevas ventas a `Tbl_Ventas`?
>
>Todavía no respondáis. Lo comprobaremos en la siguiente parte de la práctica.

---

## Parte 11. La prueba fundamental: añadir nuevos registros

Esta es la parte más importante de la práctica. Hasta ahora hemos creado la Tabla y todos los elementos vinculados a ella. Ahora comprobaremos si realmente es dinámica.

### Paso 17. Añadir una nueva venta

Escribe inmediatamente debajo de la última fila de datos:

```tsv
V021	12/09/2026	Ana	Hardware	Monitor 24"	Tienda Física	10	189,00	Completada
```

> **Pregunta al alumnado**: ¿Qué debería ocurrir si estamos trabajando realmente con una Tabla Estructurada?

Comprueba que:
* la nueva fila queda incorporada a la tabla;
* mantiene el formato;
* las columnas calculadas se completan;
* la fila de totales incorpora el nuevo registro;
* los indicadores se actualizan;
* el gráfico incorpora el nuevo registro (hay que actualizarlo en **Anáslisis de Gráfico Dinámico -> Actualizar**).

---

## Parte 12. Segunda prueba de crecimiento

### Paso 18. Añadir tres ventas más

Añade debajo:

```tsv
V022	12/09/2026	Carlos	Software	Windows 11	Online	7	145,00	Completada
V023	13/09/2026	Laura	Accesorios	Webcam	Online	14	45,00	Pendiente
V024	13/09/2026	Miguel	Hardware	Disco SSD	Tienda Física	9	89,90	Completada
```

Obserba nuevamente el comportamiento de la Tabla.

---

## Parte 13. Comprobar la ventaja frente a un rango convencional

>Ahora formula al alumnado la siguiente pregunta: Si estos datos fueran un rango convencional y el gráfico estuviera basado en `A1:L21`, ¿qué tendríamos que hacer para incorporar manualmente las nuevas ventas?
>
>Deja que los alumnos respondan antes de explicar.
>
>La respuesta es que habría que **modificar manualmente los rangos** correspondientes y **comprobar que las fórmulas y el gráfico incluyen los nuevos registros**. Con una Tabla Estructurada, esta ampliación se produce automáticamente.

---

## Parte 14. Comprender las dos referencias estructuradas principales

>Llegados a este punto, deténte para comparar las dos sintaxis utilizadas.

- **Referencia a toda una columna**: `Tbl_Ventas[Total Factura]`
       - Significa: Todos los valores de la columna `Total Factura`.
       - Ejemplo: `>=SUMA(Tbl_Ventas[Total Factura])`
- **Referencia a la fila actual**: `[@[Total Factura]]`
       - Significa: El valor de `Total Factura` de esta misma fila.
       - Ejemplo: Podríamos crear una columna denominada **Comisión** y utilizar: `=SI([@Estado]="Completada";[@[Total Factura]]*0,05;0)`. La fórmula calcula una comisión del 5 % únicamente para las ventas completadas.

---

## Parte 15. Añadir una última columna calculada

### Paso 19. Crear la columna Comisión

Añade al final de la tabla una columna `Comisión` e introduce:

```excel
=SI([@Estado]="Completada";[@[Total Factura]]*0,05;0)
```

Comprueba que:

* Excel crea automáticamente la columna calculada.
* Las ventas `Completada` tienen comisión.
* Las ventas `Pendiente` tienen comisión `0`.

---

## Parte 16. Reflexión final

>Al terminar la práctica, pide a los alumnos que observen la hoja completa.

Ahora disponemos de:

* una **Tabla Estructurada** llamada `Tbl_Ventas`;
* columnas calculadas mediante referencias estructuradas;
* fórmulas que utilizan `[@Columna]`;
* fórmulas globales que utilizan `Tbl_Ventas[Columna]`;
* una Fila de Totales;
* indicadores resumen;
* un gráfico vinculado a la tabla;
* actualización automática al añadir registros.

## Preguntas de comprobación

1. ¿Qué diferencia hay entre `Tbl_Ventas[Total Factura]` y `[@[Total Factura]]`?
2. ¿Qué significa el símbolo `@`?
3. ¿Por qué la fórmula de `Comisión` no necesita copiarse manualmente a todas las filas?
4. ¿Qué ocurre con el gráfico cuando añadimos una nueva venta?
5. ¿Qué ventaja aporta utilizar `Tbl_Ventas[Total Factura]` frente a `P2:P21`?
6. ¿Qué sucedería si mañana la empresa registra 500 ventas más?

---

### 🎯 Resultado final de la práctica

El alumno habrá construido desde cero un sistema de ventas que permite comprobar de forma práctica las principales ventajas de las Tablas Estructuradas:

| Funcionalidad             | Aplicación en la práctica              |
| ------------------------- | -------------------------------------- |
| Tabla Estructurada        | `Tbl_Ventas`                           |
| Nombre profesional        | `Tbl_Ventas`                           |
| Estilo de tabla           | Diseño de tabla                        |
| Filas con bandas          | Presentación de datos                  |
| Columna calculada         | Importe, IVA, Total Factura y Comisión |
| Referencia de fila        | `[@Columna]`                           |
| Referencia de columna     | `Tbl_Ventas[Columna]`                  |
| Fila de Totales           | Sumas y recuentos                      |
| Indicadores               | Facturación, operaciones y media       |
| Gráfico                   | Facturación por venta                  |
| Crecimiento automático    | Nuevos registros                       |
| Actualización de fórmulas | Automática                             |
| Actualización del gráfico | Automática                             |

> **Idea clave:** una Tabla Estructurada no es simplemente un rango con formato. Es un objeto de Excel que entiende su propia estructura y permite construir informes, fórmulas y gráficos que se adaptan automáticamente al crecimiento de los datos.