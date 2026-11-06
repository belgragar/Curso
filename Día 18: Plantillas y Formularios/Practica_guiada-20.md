# Práctica Guiada 20: Gestión y Creación de Tablas Mediante Formularios en Excel

## 1. Contexto de Negocio

La Dirección General de Universidades precisa unificar el registro de matriculaciones por tipo de titulación (Arquitectura e Ingenierías Técnicas, Diplomaturas, Licenciaturas, Arquitectura e Ingenierías, y Títulos Dobles) en sus distintas sedes académicas.

Para minimizar los errores de transcripción del personal administrativo y agilizar la navegación entre los registros existentes, se ha establecido el uso de la **herramienta de Formulario nativa de Excel**. A través de esta práctica, aprenderás a consultar, filtrar y administrar datos mediante formularios, así como a utilizar esta misma herramienta para **crear una tabla estructurada desde cero** comenzando únicamente con las cabeceras.

---

## 2. Conjunto de Datos (Dataset)

Para trabajar en esta práctica dispones de dos opciones:

### Opción A: Base de Datos Existente (Hoja1 - Formularios.xlsx)

Copia la siguiente tabla de ejemplo (extraída de la hoja de matriculaciones universitarias) y pégala a partir de la celda `A1` en una hoja nueva llamada `Hoja1`:

```csv
Universidades;Arquitectura e Ingenierías Técnicas;Diplomaturas;Licenciaturas;Arquitectura e Ingenierías;Títulos Dobles;Total
Alcalá de Henares;3704;3382;9218;2107;;18411
Málaga;2510;4120;12400;3150;110;22290
Pública de Navarra;1950;2240;1519;1633;233;7575
Rey Juan Carlos;1264;5893;7406;1090;218;15871
Rovira i Virgili;2105;4110;5039;591;;11845
Salamanca;4327;6729;16141;1081;279;28557
Santiago de Compostela;2800;6024;21371;1265;;31460
Sevilla;7844;13312;29184;10346;15;60701
U.N.E.D.;14421;17029;99035;3640;;134125
Valencia (Est. General);706;13275;30295;1174;234;45684
Valladolid;6337;7833;9503;4964;112;28749
Vigo;4089;6803;9587;4192;;24671
Zaragoza;7093;9681;13157;3706;273;33910

```

### Opción B: Nueva Hoja para Creación desde Cero

En una hoja limpia denominada `Nueva_Tabla`, introduce en la fila 1 únicamente las cabeceras separadas por columnas:

| A1 | B1 | C1 | D1 | E1 | F1 | G1 |
| --- | --- | --- | --- | --- | --- | --- |
| **Universidad** | **Arquitectura e Ingenierías Técnicas** | **Diplomaturas** | **Licenciaturas** | **Arquitectura e Ingenierías** | **Títulos Dobles** | **Total** |

---

## 3. Tareas a Resolver

1. **Activación de la herramienta Formulario:** Habilitar el comando en la cinta de opciones o en la barra de herramientas de acceso rápido si no se encuentra visible.
2. **Navegación y Consulta:** Explorar los registros existentes utilizando los botones `Buscar siguiente` y `Buscar anterior`.
3. **Búsqueda por Criterios:**
* Localizar el registro correspondiente a la Universidad de **Málaga**.
* Filtrar y mostrar las universidades cuyo número de Licenciaturas sea superior a `40000` (`>40000`).


4. **Inserción y Eliminación de Registros:**
* Añadir un nuevo registro para la universidad de **Navarra** con sus datos correspondientes.
* Localizar el registro recién insertado y proceder a su eliminación definitiva mediante el formulario.


5. **Creación de Tabla desde Cero mediante Formularios:**
* Intentar abrir el formulario desde una celda vacía fuera del rango de encabezados para **analizar el mensaje de error de Excel**.
* Abrir el formulario situándote sobre los encabezados escritos en la fila 1 e introducir el primer registro para comprobar cómo Excel genera automáticamente la tabla de datos.



---

## 4. Guía de Solución Paso a Paso

### Paso 1: Activar el comando Formulario en Excel

Si el botón **Formulario** no está disponible en la pestaña *Programador* (o *Desarrollador*):

1. Ve a **Archivo** > **Opciones** > **Barra de herramientas de acceso rápido**.
2. En el desplegable *Comandos disponibles en:*, selecciona **Comandos que no están en la cinta de opciones**.
3. Busca **Formulario...**, haz clic en **Agregar >>** y pulsa **Aceptar**.

---

### Paso 2: Navegación y Búsqueda por Criterios

1. Sitúrate en cualquier celda con datos del rango `A1:G14` de la `Hoja1`.
2. Pulsa en el icono **Formulario**. Se abrirá la ventana flotante mostrando el primer registro (*Alcalá de Henares*).
3. **Navegar:** Pulsa el botón **Buscar siguiente** para desplazarte hacia adelante (registro 2: *Málaga*) y **Buscar anterior** para volver atrás.
4. **Búsqueda por Nombre:**
* Haz clic en el botón **Criterios** (el formulario se limpiará).
* En el campo *Universidades*, escribe `Málaga` y presiona la tecla `Enter`. Aparecerán los datos de dicha universidad.


5. **Búsqueda por Condición Numérica:**
* Pulsa nuevamente en **Criterios** y haz clic en **Borrar** para limpiar los filtros anteriores.
* En la casilla correspondiente a *Licenciaturas*, introduce el criterio `>40000` y pulsa `Enter`. El formulario mostrará los datos de la **U.N.E.D.** (que cuenta con más de 40.000 alumnos en esa titulación).



---

### Paso 3: Introducción y Eliminación de Registros

1. **Insertar Registro:**
* Dentro de la ventana del formulario, haz clic en el botón **Nuevo**.
* Rellena los campos consecutivamente con los siguientes valores:
* **Universidades:** `Navarra`
* **Arquitectura e Ingenierías Técnicas:** `484`
* **Diplomaturas:** `1007`
* **Licenciaturas:** `5794`
* **Arquitectura e Ingenierías:** `2208`
* **Títulos Dobles:** `355`


* Pulsa `Enter` y cierra la ventana con el botón **Cerrar**.
* Comprueba que el nuevo registro se ha insertado al final del listado en la fila 15.


2. **Eliminar Registro:**
* Abre de nuevo el formulario.
* Pulsa **Criterios**, escribe `Navarra` en el campo *Universidades* y pulsa `Enter`.
* Con el registro de *Navarra* en pantalla, pulsa sobre el botón **Eliminar**.
* Acepta el mensaje de confirmación (*"El registro se eliminará permanentemente"*) y cierra el formulario.



---

### Paso 4: Creación de una Tabla desde Cero mediante Formulario y Control de Errores

#### A. Provocar y comprender el mensaje de error

1. Ve a la hoja `Nueva_Tabla` donde escribiste los encabezados en la fila 1 (`A1:G1`).
2. Haz clic en una celda completamente vacía fuera de las cabeceras (por ejemplo, en la celda `C10`).
3. Intenta pulsar el botón **Formulario**.
4. **Resultado esperado:** Excel mostrará un mensaje de advertencia indicando que *no se puede determinar qué fila contiene los encabezados de la lista* o que *no se puede aplicar la orden a un rango vacío*. Esto ocurre porque la herramienta requiere un contexto de datos o títulos para construir los campos de entrada.

#### B. Construir la tabla usando el Formulario

1. Haz clic en cualquiera de las celdas con encabezado (por ejemplo, en `A1`).
2. Haz clic de nuevo en el botón **Formulario**.
3. Observa cómo Excel reconoce los títulos de la fila 1 como campos del formulario.
4. Pulsa sobre **Nuevo** e introduce los datos del primer registro:
* **Universidades:** `Universidad Complutense`
* **Arquitectura e Ingenierías Técnicas:** `1200`
* **Diplomaturas:** `3400`
* **Licenciaturas:** `15000`
* **Arquitectura e Ingenierías:** `2100`
* **Títulos Dobles:** `450`


5. Presiona `Enter` y cierra el formulario.
6. **Comprobación:** Verás que Excel ha colocado automáticamente los datos en la fila 2, justo debajo de sus correspondientes cabeceras, iniciando la construcción estructurada de la tabla sin haber tenido que escribir manualmente en la cuadrícula.
