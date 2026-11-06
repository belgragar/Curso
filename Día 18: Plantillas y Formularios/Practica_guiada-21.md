# Práctica Guiada 21: Diseño de Formulario Interactivo y Creación de Plantilla Corporativa (.xltx)

**Nivel:** Intermedio - Avanzado

**Objetivos didácticos:**

* Habilitar y dominar la pestaña **Programador**.
* Insertar y configurar **todos** los Controles de Formulario de Excel (*Etiqueta, Botón de opción, Cuadro de grupo, Cuadro de lista, Control de número, Cuadro combinado, Casilla de verificación y Barra de desplazamiento*).
* Vincular controles a celdas auxiliares de soporte y conectar los resultados con fórmulas (`INDICE`, `SI`, `AÑO`, `HOY`).
* Aplicar diseño visual, ocultar líneas de cuadrícula y proteger celdas.
* Guardar y gestionar el archivo final como **Plantilla de Excel (*.xltx)**.

---

## 1. Contexto de Negocio

El departamento de Recursos Humanos y Formación de la empresa necesita un sistema estandarizado para registrar la ficha de los empleados y sus preferencias de capacitación. Para evitar errores tipográficos y que los usuarios modifiquen accidentalmente la estructura o las fórmulas, diseñaremos una interfaz gráfica basada en **Controles de Formulario**.

Una vez finalizado el diseño y la protección del libro, guardaremos el archivo como **Plantilla de Excel (*.xltx)** para que cada vez que un usuario abra el archivo, se genere una copia limpia y virgen sin alterar el modelo maestro.

---

## 2. Conjunto de Datos (Dataset)

Para alimentar las listas desplegables del formulario (ciudades y departamentos), necesitamos un conjunto de datos base.

Abre un libro nuevo en Excel, crea una hoja auxiliar llamada **`Datos_Origen`** (o utiliza la **Hoja2** del archivo de prácticas) y copia el siguiente bloque de datos delimitado por punto y coma (`;`) a partir de la celda **`A1`**:

```csv
Ciudad;Departamento
Madrid;Dirección
Barcelona;Ventas
Valencia;Marketing
Sevilla;Recursos Humanos
Zaragoza;Finanzas
Málaga;TI y Sistemas
Murcia;Logística
Palma;Producción
Las Palmas;Atención al Cliente
Bilbao;Calidad

```

---

## 3. Tareas a Resolver

1. **Configuración inicial:** Habilitar la pestaña *Programador* (si no está activa) y preparar la hoja principal del formulario (**`Ficha_Empleado`**).
2. **Creación del área gráfica del formulario:** Aplicar un color de fondo corporativo (p. ej., Verde Mar o Azul Suave) al rango `A1:J20` y ocultar las líneas de cuadrícula.
3. **Sección Datos Personales:**
* Crear un **Cuadro de Grupo** para agrupar los **Botones de Opción** de Género (*Hombre* / *Mujer*).
* Añadir una **Etiqueta** o título en celda para el nombre completo.


4. **Sección Ubicación y Cargo:**
* Configurar un **Cuadro de Lista** para seleccionar la *Ciudad* vinculada a una celda de soporte.
* Extraer dinómicamente el nombre de la ciudad mediante la función `INDICE`.


5. **Sección Edad y Antigüedad:**
* Insertar un **Control de Número** para seleccionar el año de nacimiento (entre 1950 y 2005) y calcular la edad automáticamente mediante `AÑO(HOY()) - Celda`.
* Insertar un **Control de Número** adicional para seleccionar los años de experiencia (1 a 40).


6. **Sección Departamento y Evaluación:**
* Configurar un **Cuadro Combinado** (desplegable) para elegir el *Departamento*.
* Insertar una **Barra de Desplazamiento** para asignar una puntuación de evaluación del 1 al 10.


7. **Sección Idiomas:**
* Crear **Casillas de Verificación** independientes para los idiomas (*Inglés*, *Francés*, *Alemán*, *Otro*).


8. **Protección y Creación de Plantilla (.xltx):**
* Desbloquear únicamente las celdas de vínculo/entrada necesarias.
* Proteger la hoja de trabajo.
* Guardar la estructura en formato de **Plantilla de Excel (*.xltx)**.



---

## 4. Guía de Solución Paso a Paso

### Paso 1: Activar la Ficha Programador

1. Ve a **Archivo > Opciones > Personalizar cinta de opciones**.
2. En la columna de la derecha (*Pestañas principales*), marca la casilla **Programador** (o *Desarrollador*).
3. Haz clic en **Aceptar**.

---

### Paso 2: Diseño del Lienzo de Trabajo

1. Cambia el nombre de la **Hoja1** a **`Ficha_Empleado`**.
2. Selecciona el rango de celdas **`A1:J20`** y aplícale un color de relleno suave (p. ej., Verde Mar Claro o Gris Neutro) desde **Inicio > Color de relleno**.
3. Ve a la pestaña **Vista > grupo Mostrar** y desmarca la casilla **Líneas de cuadrícula** para obtener un acabado limpio de interfaz.

---

### Paso 3: Agrupación y Botones de Opción (Género)

1. Ve a **Programador > Insertar > Cuadro de grupo (Control de formulario)**. Dibuja un rectángulo en `C2:E5` y cámbiale el texto por `Sexo`.
2. Ve a **Programador > Insertar > Botón de opción**.
3. Dibuja un botón dentro del marco en `C3`, haz clic derecho sobre el texto, selecciona *Editar texto* y escribe `Hombre`.
4. Dibuja otro **Botón de opción** en `D3` y edita su texto a `Mujer`.
5. Haz clic derecho sobre el primer botón de opción > **Formato de control**:
* **Vincular con la celda:** `$A$79` (o `$Z$1` para ocultarla).
* Activa el **Sombreado 3D**. Haz clic en **Aceptar**. *(Al marcar "Hombre" devolverá 1, y "Mujer" devolverá 2).*



---

### Paso 4: Cuadro de Lista (Selección de Ciudad)

1. Ve a **Programador > Insertar > Cuadro de lista**.
2. Dibuja el cuadro abarcando el rango `H3:I9`.
3. Haz clic derecho sobre el cuadro de lista > **Formato de control**:
* **Rango de entrada:** `Datos_Origen!A2:A11`
* **Vincular con la celda:** `Datos_Origen!A15`
* **Tipo de selección:** Simple.
* Activa el **Sombreado 3D** y pulsa **Aceptar**.


4. En la celda **`E6`** de la hoja `Ficha_Empleado`, introduce la siguiente fórmula exacta para mostrar el nombre de la ciudad seleccionada:
```excel
=INDICE(Datos_Origen!A2:A11; Datos_Origen!A15; 1)

```



---

### Paso 5: Control de Número (Año de Nacimiento y Edad)

1. Ve a **Programador > Insertar > Control de número**.
2. Dibuja el control sobre la celda **`D10`**.
3. Haz clic derecho > **Formato de control**:
* **Valor mínimo:** `1950`
* **Valor máximo:** `2005`
* **Incremento:** `1`
* **Vincular con la celda:** `E10`
* Activa **Sombreado 3D** y pulsa **Aceptar**.


4. En la celda **`C12`**, escribe la fórmula para calcular la edad actual:
```excel
=AÑO(HOY())-E10

```


*(Nota: Si Excel asigna un formato de fecha a `C12`, cambia el formato de celda a **General** desde la pestaña Inicio).*
5. En la celda **`D12`**, escribe el texto: `Años`.

---

### Paso 6: Cuadro Combinado (Departamento)

1. Ve a **Programador > Insertar > Cuadro combinado**.
2. Dibuja un rectángulo en el rango **`F14:G14`**.
3. Haz clic derecho > **Formato de control**:
* **Rango de entrada:** `Datos_Origen!B2:B11`
* **Vincular con la celda:** `Datos_Origen!B15`
* Activa **Sombreado 3D** y pulsa **Aceptar**.


4. Para mostrar el departamento seleccionado en una celda de resumen (`H14`), escribe:
```excel
=INDICE(Datos_Origen!B2:B11; Datos_Origen!B15)

```



---

### Paso 7: Barra de Desplazamiento (Puntuación de Evaluación)

*(Añadido para explorar todos los controles de formulario disponibles)*

1. Ve a **Programador > Insertar > Barra de desplazamiento (Control de formulario)**.
2. Dibuja la barra horizontalmente en el rango **`C18:F18`**.
3. Haz clic derecho > **Formato de control**:
* **Valor mínimo:** `1`
* **Valor máximo:** `10`
* **Incremento:** `1`
* **Cambio de página:** `2`
* **Vincular con la celda:** `G18`
* Activa **Sombreado 3D** y pulsa **Aceptar**.



---

### Paso 8: Casillas de Verificación (Idiomas)

1. Ve a **Programador > Insertar > Casilla de verificación**.
2. Dibuja las casillas en las celdas indicadas y ajusta el texto descriptivo:
* Celda **`E16`**: Texto `Inglés` | Vincular con celda: `E17`
* Celda **`F16`**: Texto `Francés` | Vincular con celda: `F17`
* Celda **`G16`**: Texto `Alemán` | Vincular con celda: `G17`
* Celda **`H16`**: Texto `Otro` | Vincular con celda: `H17`


3. *(Opcional)* Si la casilla está marcada, la celda de vínculo mostrará `VERDADERO`; de lo contrario, mostrará `FALSO`.

---

### Paso 9: Protección del Formulario

Para asegurar que los usuarios solo interactúen con los controles y no borren las fórmulas:

1. Selecciona las celdas vinculadas que requieren entrada manual si las hubiera, o asegúrate de que los controles estén vinculados a celdas desprotegidas.
2. Oculta la pestaña auxiliar `Datos_Origen` (haz clic derecho sobre la pestaña > **Ocultar**).
3. Ve a la pestaña **Revisar > Proteger hoja**.
4. Introduce una contraseña (opcional) y asegúrate de dejar marcadas solo las opciones que permitan al usuario seleccionar celdas desbloqueadas e interactuar con controles de formulario.

---

### Paso 10: Guardar el Archivo como Plantilla de Excel (.xltx)

1. Ve a **Archivo > Guardar como**.
2. Selecciona **Examinar**.
3. En el desplegable **Tipo**, cambia *Libro de Excel (*.xlsx)* por **Plantilla de Excel (*.xltx)**.
4. Observa cómo Excel redirige automáticamente la ruta a la carpeta de plantillas personalizadas.
5. Asigna el nombre **`Plantilla_Ficha_Empleado.xltx`** y haz clic en **Guardar**.

> **¿Cómo probar la plantilla?** Cierra Excel y haz doble clic sobre el archivo `Plantilla_Ficha_Empleado.xltx`. Verás que Excel abre un documento nuevo llamado **`Plantilla_Ficha_Empleado1.xlsx`**, manteniendo el archivo origen intacto y listo para rellenar de forma segura.
