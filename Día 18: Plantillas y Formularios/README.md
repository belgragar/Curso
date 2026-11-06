# Plantillas y Formularios en Excel Avanzado

## 1. Introducción

En el día a día de una empresa, tareas como emitir facturas, registrar partes de trabajo o controlar stock se repiten constantemente. Si cada empleado crea un documento desde cero, se producen errores, faltan datos y la imagen corporativa se resiente.

Una **plantilla** es un modelo prediseñado que sirve como base para crear nuevos documentos idénticos de forma automática. Si además le añadimos **controles de formulario** (como menús desplegables o botones), transformamos una simple hoja de cálculo en una aplicación intuitiva que cualquier compañero puede usar sin experiencia técnica previa.

---

## 2. Conceptos previos

Antes de comenzar, debes dominar los siguientes conceptos básicos:

* **Libro de Excel (.xlsx vs .xltx):** 
  * Un archivo normal  (`.xlsx`) guarda datos y se edita directamente. 
  * Una plantilla (`.xltx`) actúa como un molde virgen; al abrirla, Excel crea una copia nueva sin alterar el original.
  
* **Ficha Programador (Desarrollador):** Es la pestaña superior de Excel desde donde se insertan los controles avanzados de formulario. Si no la ves visible, tranquilos, lo veremos paso a paso.
  
* **Protección de celdas:** Herramienta para bloquear ciertas partes de la hoja (como fórmulas y títulos) y dejar libres únicamente las celdas donde el usuario debe escribir.

---

## 3. Creación y estructuración de una plantilla profesional

Para que una plantilla sea útil en una empresa, debe separar claramente las zonas de introducción de datos de los cálculos automáticos.

```
[ Datos de Cabecera (Cliente/Fecha) ] ---> Rellenado por el usuario
[ Cuerpo de Líneas (Artículos/Cantidades) ] ---> Selección mediante controles
[ Totales y Cálculos ] ---> Protegidos y bloqueados con fórmulas

```

**Procedimiento paso a paso para crear una plantilla:**

1. Abre un libro nuevo en blanco de Excel y diseña la estructura visual (añade el logotipo de la empresa, los títulos corporativos y los bordes necesarios).
2. Deja en blanco exclusivamente las celdas donde el usuario introducirá los datos operativos.
3. Introduce las fórmulas necesarias en las celdas de resultado (por ejemplo, sumas o multiplicaciones).
4. Ve a **Archivo > Guardar como**.
5. En el menú desplegable de tipo de archivo, selecciona **Plantilla de Excel (*.xltx)**. Excel cambiará automáticamente la ruta predeterminada a la carpeta de plantillas de usuario.

---

## 4. Inserción de controles de formulario

Los controles de formulario son herramientas visuales que facilitan la introducción de datos y reducen los errores tipográficos.

  >**Analogía:**
  >Imagina que vas a una imprenta a encargar talonarios de albaranes autocopiativos:
    >
    >* La **plantilla de Excel** es el diseño impreso en el papel: las líneas, el espacio para la firma y el logo ya vienen fijos para que nadie tenga que dibujarlos a mano cada vez.
    >* Los **controles de formulario** son como los menús desplegables de una pantalla táctil en una hamburguesería: en vez de dejar que el cliente escriba libremente lo que quiera (lo que provocaría faltas de ortografía o confusiones), se le ofrecen botones y opciones cerradas para elegir de forma rápida y segura.


**Procedimiento para activar la Ficha Programador:**

1. Haz clic derecho en cualquier pestaña de la cinta de opciones superior y selecciona **Personalizar la cinta de opciones**.
2. En la columna de la derecha, busca y marca la casilla **Programador** (o Desarrollador según la versión). Haz clic en Aceptar.

** Catálogo Técnico de Controles de Formulario**

Los controles de formulario son objetos gráficos interactivos situados en la pestaña **Programador > Insertar > Controles de formulario**. A continuación se detallan sus características y su comportamiento con las celdas de vínculo:

### 1. Cuadro combinado (Drop-down / Desplegable)
* **Descripción:** Despliega una lista emergente de opciones al hacer clic.
* **Resultado en celda de vínculo:** Devuelve la **posición numérica** (1, 2, 3...) del elemento seleccionado en la lista.
* **Uso ideal:** Selección de productos, clientes, provincias o listas extensas donde se requiere ahorrar espacio visual.

>**Procedimiento para añadir un Cuadro Combinado:**
>
>1. Ve a la ficha **Programador > Insertar > Controles de formulario** y selecciona **Cuadro combinado**.
>2. Dibuja el control en la celda deseada de la hoja.
>3. Haz clic derecho sobre el control y selecciona **Formato de control**.
>4. En **R intervalos de entrada**, selecciona el rango de celdas con los elementos de la lista (por ejemplo, los nombres de los productos).
>5. En **Vincular con la celda**, selecciona una celda oculta de la hoja donde Excel anotará el número de orden de la opción elegida.

### 2. Casilla de verificación (Checkbox)
* **Descripción:** Casilla cuadrada que permite activar o desactivar una opción de forma independiente.
* **Resultado en celda de vínculo:** Devuelve un valor booleano: **`VERDADERO`** (marcada) o **`FALSO`** (desmarcada).
* **Uso ideal:** Opciones binarias (Sí/No, Aplicar Descuento VIP, Incluir Seguro, Acepta Condiciones).

### 3. Botón de opción (Radio Button)
* **Descripción:** Botón circular de selección exclusiva. Al seleccionar uno dentro de un mismo grupo, los demás se desmarcan automáticamente.
* **Resultado en celda de vínculo:** Devuelve el **número de orden** (1, 2, 3...) del botón seleccionado dentro de su grupo.
* **Uso ideal:** Alternativas mutuamente excluyentes (Forma de Pago, Tipo de Factura, Prioridad).

### 4. Cuadro de grupo (Group Box / Marco)
* **Descripción:** Recuadro visual que agrupa elementos relacionados. 
* **Función técnica:** Su función principal es **aislar los Botones de opción**. Todos los botones de opción dibujados dentro de un mismo Marco forman un grupo independiente y comparten la misma celda de vínculo.

### 5. Casilla de lista (List Box)
* **Descripción:** Muestra una lista fija de elementos visible en todo momento dentro de un recuadro con desplazamiento.
* **Resultado en celda de vínculo:** Devuelve la **posición numérica** (1, 2, 3...) del elemento marcado.
* **Uso ideal:** Elección de departamentos, categorías o vistas donde conviene ver las alternativas disponibles de un vistazo sin desplegar.

### 6. Control de número (Spin Button / Contador)
* **Descripción:** Botón con flechas arriba/abajo para incrementar o decrementar un valor entero dentro de un rango predefinido.
* **Resultado en celda de vínculo:** Devuelve directamente el **número entero** resultante de la pulsación (ej. del 1 al 100).
* **Uso ideal:** Modificación rápida de cantidades de artículos, plazas, meses de garantía o días de plazo.

### 7. Barra de desplazamiento (Scroll Bar)
* **Descripción:** Barra deslizable (horizontal o vertical) que permite desplazarse a lo largo de un rango de valores numéricos de forma rápida o graduada.
* **Resultado en celda de vínculo:** Devuelve el **valor numérico entero** correspondiente a la posición de la barra.
* **Uso ideal:** Selección de magnitudes variables continuas o porcentajes (ej. % de Descuento de Volumen del 0% al 50%, Plazos de financiación en meses).

### Código y Fórmulas de Apoyo

Para vincular los resultados numéricos de los controles de formulario, combinamos la celda de vínculo con funciones lógicas como `INDICE` o `ELEGIR`.

```excel
=ELEGIR(B10; "Efectivo"; "Tarjeta de Crédito"; "Transferencia Bancaria")

```

> **Explicación de la fórmula:** La celda `B10` contiene el valor numérico devuelto por un control de formulario (por ejemplo, 1, 2 o 3). La función `ELEGIR` devuelve el texto correspondiente asociado a ese número de forma automática.
> 
---


## 5. Resumen

* Las plantillas (`.xltx`) actúan como moldes seguros y estandarizados para generar documentos idénticos en la empresa.
* La ficha **Programador** permite añadir herramientas interactivas como desplegables y casillas.
* Los controles de formulario agilizan la entrada de datos y eliminan los errores humanos por escritura manual.
* Es fundamental proteger la estructura y las fórmulas para garantizar la integridad de los datos introducidos.

** ✔️ Buenas prácticas:**

  * **Protege las hojas:** Bloquea las celdas con fórmulas antes de guardar la plantilla para que nadie pueda alterarlas por accidente.
  * **Separa los datos de origen:** Coloca las listas que alimentan a los menús desplegables en una pestaña auxiliar y oculta o protege dicha pestaña.
  * **Usa extensiones correctas:** Guarda siempre el archivo maestro como `.xltx` para evitar sobrescribir la plantilla original con datos de clientes reales.

---

**❌ Errores habituales:**

  * **Guardar como `.xlsx` en lugar de `.xltx`:** Esto provoca que al abrir el archivo se modifique la plantilla original sin querer. *Solución:* Comprueba siempre la extensión al guardar por primera vez.
  * **Vincular mal el control:** Seleccionar celdas dinámicas que cambian de posición. *Solución:* Apunta el vínculo siempre a celdas fijas de soporte, preferiblemente en zonas apartadas u ocultas.

---

## 6. Glosario

* **Plantilla (`.xltx`):** Archivo de Excel prediseñado que sirve como patrón para crear nuevos libros sin alterar el modelo original.
* **Control de formulario:** Elemento gráfico de interfaz (como botones o listas desplegables) que facilita la interacción del usuario con la hoja.
* **Celda de vínculo:** Celda auxiliar conectada a un control que almacena el valor numérico de la opción seleccionada.

---

## Recursos adicionales

* **Documentación oficial:** [Microsoft Learn - Crear una plantilla de Excel](https://support.microsoft.com/Excel)
* **Herramientas recomendadas:** Microsoft Excel 365 / Excel 2021.
* **Recursos para ampliar:** Guías oficiales de automatización y diseño de interfaces de usuario en hojas de cálculo corporativas.
