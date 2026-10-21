# Práctica Guiada 06: Automatizar Procesos y Datos

## 1. Contexto de Negocio

Imagina que trabajas en la empresa **Asturias Aventura y Ocio**, dedicada a la organización de experiencias turísticas y de montaña. El equipo de recepción necesita registrar diariamente las reservas de los clientes en una hoja de cálculo. Para evitar errores humanos al introducir datos incorrectos (como fechas fuera de plazo, cantidades imposibles de participantes o categorías mal escritas) y agilizar la escritura repetitiva, vamos a automatizar y proteger la hoja de registro utilizando **listas personalizadas**, **validación de datos** con sus diferentes niveles de advertencia/restricción y herramientas de **auditoría de validación**.

---

## 2. Conjunto de Datos (Dataset)

Para comenzar a trabajar, copia la siguiente estructura de tabla y pégala en la celda `A1` de una hoja nueva de Excel (o guárdala como archivo CSV delimitado por punto y coma `;`). Esta será nuestra plantilla de trabajo operativa:

```csv
ID_Reserva;Cliente;Fecha_Reserva;Estacion;Categoria_Actividad;Num_Participantes;Precio_Unitario
RES-101;María García;15/06/2026;Verano;Ruta de Senderismo;4;35,00
RES-102;Carlos López;22/07/2026;;Descenso en Canoa;2;45,00
RES-103;Ana Martínez;10/09/2025;;Puenting;25;60,00
RES-104;Jorge Ruiz;03/04/2026;;Escalada;6;35,00
RES-105;Lucía Pérez;18/11/2026;;Espeleología;3;50,00

```

> **Nota:** Observa que los registros `RES-103` y `RES-104` contienen intencionadamente datos previos fuera de norma (fecha de 2025, aforo superior a 20 y una categoría inexistente "Escalada") para poder auditar los datos preexistentes en la Tarea 5.
> 
> 

*Adicionalmente, en otra zona de tu hoja (por ejemplo, en las celdas `J1:J5`), escribe los siguientes valores que utilizaremos como origen para las listas desplegables de categorías:*

```csv
Categorias_Validas
Ruta de Senderismo
Descenso en Canoa
Puenting
Espeleología

```

---

## 3. Tareas a Resolver y Guía Paso a Paso

### Tarea 1: Creación de una lista personalizada y uso del controlador de relleno

* Registra una nueva lista personalizada en Excel con las cuatro estaciones del año ordenadas cronológicamente: `Primavera`, `Verano`, `Otoño`, `Invierno`.



> 1. Ve a la pestaña **Archivo** > **Opciones** > **Avanzadas**.
> 2. Desplázate hacia abajo hasta la sección **General** y haz clic en el botón **Modificar listas personalizadas...**
> 3. En el cuadro *Listas personalizadas*, selecciona **NUEVA LISTA** y en el cuadro *Entradas de lista* escribe uno a uno los elementos presionando *Intro*:
> ```text
> Primavera
> Verano
> Otoño
> Invierno
> 
> ```
> 
> 
> 4. Haz clic en **Agregar** y luego en **Aceptar** (dos veces para cerrar el menú de opciones).
> 
> 

* Utiliza el **controlador de relleno** en la columna `Estacion` (celdas `D3:D6`) para completar automáticamente las estaciones correspondientes a cada fecha de reserva del dataset.



> 1. Haz clic en la celda `D2` (donde ya aparece el valor *Verano* para la fecha 15/06/2026).
> 2. Sitúa el ratón en la esquina inferior derecha de la celda hasta que el cursor se transforme en una cruz negra fina (`+`), correspondiente al **controlador de relleno**.
> 
> 
> 3. Haz clic y arrastra hacia abajo hasta la celda `D6`. Excel utilizará tu lista personalizada recién creada para rellenar automáticamente las estaciones de forma correlativa.
> 
> 
> 
> 

---

### Tarea 2: Validación de datos tipo Lista con estilo de error "Detener"

* Configura una validación de datos en la columna `Categoria_Actividad` (`E2:E6`) permitiendo únicamente valores de tipo **Lista**, cuyo origen sea el rango con las categorías válidas creado previamente (`J2:J5`).


* Configura un mensaje de entrada explicativo y un **mensaje de error de estilo Detener** para impedir por completo que se escriba una actividad que no esté en la lista.



> 1. Selecciona el rango de celdas `E2:E6`.
> 2. Ve a la pestaña **Datos** en la cinta de opciones y haz clic en el botón **Validación de datos** (dentro del grupo *Herramientas de datos*).
> 
> 
> 3. En la ficha **Configuración**:
> * En *Permitir*, selecciona **Lista**.
> 
> 
> * En *Origen*, haz clic en el selector de rango y selecciona las celdas `=$J$2:$J$5`.
> 
> 
> 
> 
> 4. En la ficha **Mensaje de entrada**:
> * Marca la casilla *Mostrar mensaje de entrada al seleccionar la celda*.
> 
> 
> * **Título:** `Selección requerida`
> * **Mensaje de entrada:** `Por favor, seleccione una categoría válida de la lista desplegable.`
> 
> 
> 5. En la ficha **Mensaje de error**:
> * Marca la casilla *Mostrar mensaje de error si se introducen datos no válidos*.
> 
> 
> * **Estilo:** **Detener** (o **Alto**) (icono de círculo rojo con una cruz).
> 
> 
> * **Título:** `Actividad no permitida`
> * **Mensaje de error:** `La actividad introducida no existe en el catálogo oficial. Debe elegir una opción de la lista.`
> 
> 
> 6. Haz clic en **Aceptar**.
> 
> 

---

### Tarea 3: Validación de datos tipo Número entero con estilo de error "Advertencia"

* Configura una validación de datos en la columna `Num_Participantes` (`F2:F6`) para aceptar únicamente **Números enteros** comprendidos entre `1` y `20` (inclusive).


* Configura un **mensaje de error de estilo Advertencia** que avise al usuario si introduce un número superior a 20, permitiéndole continuar si confirma la acción de forma excepcional.



> 1. Selecciona el rango de celdas `F2:F6`.
> 2. Ve a la pestaña **Datos** > **Validación de datos**.
> 
> 
> 3. En la ficha **Configuración**:
> * **Permitir:** **Número entero**.
> 
> 
> * **Datos:** **entre**.
> 
> 
> * **Mínimo:** `1`
> * **Máximo:** `20`
> 
> 
> 4. En la ficha **Mensaje de error**:
> * **Estilo:** **Advertencia** (icono de triángulo amarillo con exclamación).
> 
> 
> * **Título:** `Aforo elevado`
> * **Mensaje de error:** `El número de participantes supera el límite estándar de 20 personas por grupo. ¿Desea continuar de todos modos?`
> 
> 
> 5. Haz clic en **Aceptar**.
> 
> 

---

### Tarea 4: Validación de datos tipo Fecha con estilo de error "Información"

* Configura una validación de datos en la columna `Fecha_Reserva` (`C2:C6`) para permitir únicamente **Fechas** dentro del año en curso, es decir, entre el `01/01/2026` y el `31/12/2026`.


* Configura un **mensaje de error de estilo Información** que alerte al usuario si introduce una fecha fuera de ese rango, informándole amablemente pero permitiéndole registrar el dato de todas formas.



> 1. Selecciona el rango de celdas `C2:C6`.
> 2. Ve a la pestaña **Datos** > **Validación de datos**.
> 
> 
> 3. En la ficha **Configuración**:
> * **Permitir:** **Fecha**.
> 
> 
> * **Datos:** **entre**.
> 
> 
> * **Fecha inicial:** `01/01/2026`
> * **Fecha final:** `31/12/2026`
> 
> 
> 4. En la ficha **Mensaje de error**:
> * **Estilo:** **Información** (icono de círculo azul con la letra i).
> 
> 
> * **Título:** `Aviso de temporada`
> * **Mensaje de error:** `La fecha introducida no corresponde al ejercicio fiscal actual (2026). Se registrará a título informativo.`
> 
> 
> 5. Haz clic en **Aceptar**.
> 
> 

---

### Tarea 5: Auditoría de datos previos (Rodear con un círculo datos no válidos y borrar círculos)

* Utiliza la herramienta de auditoría para identificar visualmente aquellos datos del dataset original que incumplen las reglas de validación recién aplicadas.


* Corrige los datos señalados o elimina los círculos rojos una vez realizada la revisión.



> 1. **Rodear los datos no válidos con un círculo:**
> * Ve a la pestaña **Datos** en la cinta de opciones.
> * Haz clic en la pequeña flecha desplegable situada junto al botón **Validación de datos** (en el grupo *Herramientas de datos*).
> * Selecciona la opción **Rodear con un círculo datos no válidos**.
> 
> 
> * **Resultado esperado:** Excel dibujará un círculo rojo alrededor de las celdas que contienen errores preexistentes:
> 
> 
> * `C4` (Fecha de 2025 fuera del rango establecido para 2026).
> * `E5` (Categoría "Escalada" que no existe en el origen de datos).
> * `F4` (Aforo de 25 participantes, superior al límite máximo de 20).
> 
> 
> 
> 
> 2. **Borrar los círculos de validación:**
> * Una vez revisados los errores, vuelve a desplegar el menú de **Validación de datos** en la pestaña **Datos**.
> * Haz clic en **Borrar círculos de validación** para retirar las marcas visuales de la hoja de trabajo.
> 
