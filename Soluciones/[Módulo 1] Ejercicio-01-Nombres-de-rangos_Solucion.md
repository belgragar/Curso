# Ejercicio 01 - Nombres  de rangos

## 1. Contexto de Negocio

La startup **"Innovación y Suministros Digitales, S.L."** está organizando su modelo de control comercial para el nuevo ejercicio. Como parte del equipo administrativo, tu objetivo en este primer día de clase es estructurar un libro de trabajo en Excel:

1. Crear una hoja dedicada exclusivamente a **parámetros de consulta frecuentes y modificables** (IVA, objetivos y comisiones) a los que la dirección pueda acceder rápidamente sin alterar la estructura principal.


2. Practicar la **selección de rangos** (contiguos y no contiguos) mediante ratón, atajos de teclado y el *Cuadro de nombres*.


3. Dominar las **tres formas de crear nombres de rango**, incluyendo la creación masiva desde las etiquetas de filas y columnas.


4. Configurar y diferenciar los **ámbitos de los nombres** (global a nivel de libro vs. local a nivel de hoja).


5. Organizar visualmente las pestañas de las hojas del libro de trabajo.



---

## 2. Conjunto de Datos (Dataset)

Paso 1: Copia y pega el siguiente bloque en la celda **`A1`** de la primera hoja:

```csv
Parametro;Valor_Referencia;Ambito_Aplicacion
IVA_General;0,21;Global_Libro
Objetivo_Ventas;15000;Local_Hoja
Descuento_Especial;0,05;Global_Libro
Comision_Comercial;0,08;Local_Hoja

```

Paso 2: Copia y pega esta segunda tabla a partir de la celda **`A8`** de la misma hoja:

```csv
Comercial;Enero;Febrero;Marzo
Ana_Gomez;1200;1500;1800
Carlos_Ruiz;950;1100;1300
Elena_Blanco;2100;1900;2200

```

---

## 3. Tareas a Resolver

### Módulo A: Configuración y Organización de Hojas

1. **Pestaña principal:** Renombra la primera hoja como **`Parametros_Base`** y asígnale un color de pestaña **Verde**.
2. **Pestaña secundaria:** Crea una segunda hoja en el libro, renómbrala como **`Resumen_Ventas`** y ponle un color de pestaña **Azul**.

### Módulo B: Selección de Rangos (Contiguos y No Contiguos)

3. **Selección contigua:** Selecciona el bloque contiguo de la primera tabla (`A1:C5`) utilizando el *Cuadro de nombres*.


4. **Selección no contigua:**
* Mediante la tecla `Ctrl`, selecciona el rango no contiguo formado por los nombres de los parámetros (`A2:A5`) y las ventas de Marzo (`D9:D11`).


* Prueba a escribir en el *Cuadro de nombres* la sintaxis para rangos separados `A2:A5;D9:D11` y pulsa *Enter* para comprobar cómo Excel selecciona ambas zonas simultáneamente.





### Módulo C: Las 3 Maneras de Crear Nombres de Rangos

5. **Método 1 — Cuadro de Nombres:** Selecciona la celda **`B2`** (valor `0,21` del IVA) y asígnale el nombre **`Tipo_IVA`** directamente desde el *Cuadro de nombres*.


6. **Método 2 — Crear desde la selección (Etiquetas):** Selecciona el rango **`A1:C5`**. Ve a `Fórmulas > Nombres definidos > Crear desde la selección` y marca la opción **Columna izquierda** para asignar automáticamente el nombre de cada parámetro a su celda de valor.


7. **Método 3 — Definir nombre:** Selecciona la celda **`B5`** (valor `0,08` de la Comisión). Ve a `Fórmulas > Definir nombre` y asígnale el nombre **`Comision_Ventas`**.



### Módulo D: Nombres para Filas y Columnas de una Tabla de Datos

8. Selecciona la tabla de ventas completa con sus encabezados (**`A8:D11`**).


9. Ve a `Fórmulas > Crear desde la selección` y marca tanto **Fila superior** como **Columna izquierda**. Esto creará los nombres automáticos para cada columna (`Enero`, `Febrero`, `Marzo`) y para cada fila (`Ana_Gomez`, `Carlos_Ruiz`, `Elena_Blanco`).



### Módulo E: Configuración del Ámbito y Auditoría de Nombres

10. Abre el **Administrador de nombres** (`Fórmulas > Administrador de nombres`).
11. Localiza el nombre **`Objetivo_Ventas`** (creado previamente de forma global por defecto) y elimínalo de la lista, ya que Excel no permite modificar el ámbito de un nombre una vez creado.
12. Vuelve a definir el rango de la celda `B3` pero asignándole explícitamente el ámbito **`Parametros_Base`** (local de la hoja) desde el cuadro de diálogo *Definir nombre*.
13. Comprueba en el Administrador de nombres que el nuevo rango aparece correctamente vinculado al ámbito local de la hoja.

---

## 4. Guía de Solución Paso a Paso

### Paso 1: Renombrar hojas y cambiar color de pestaña

1. Haz clic derecho sobre la etiqueta de la hoja (*Hoja1*), selecciona **Cambiar nombre** y escribe `Parametros_Base`.
2. Vuelve a hacer clic derecho sobre la pestaña, entra en **Color de pestaña** y selecciona el tono **Verde**.
3. Haz clic en el botón **`+`** para añadir una nueva hoja, cámbiale el nombre a `Resumen_Ventas` y aplica el color de pestaña **Azul**.

### Paso 2: Practicar la selección de rangos contiguos y no contiguos

1. **Rango contiguo:** Haz clic en el *Cuadro de nombres* (arriba a la izquierda, junto a la barra de fórmulas), escribe `A1:C5` y pulsa *Enter*.


2. **Rango no contiguo (Teclado/Ratón):** Haz clic en `A2` y arrastra hasta `A5`. Mantén pulsada la tecla **`Ctrl`** en tu teclado y selecciona con el ratón el rango `D9:D11`.


3. **Rango no contiguo (Cuadro de nombres):** Escribe directamente en el *Cuadro de nombres* `A2:A5,D9:D11` y pulsa *Enter*.



### Paso 3: Aplicar los 3 métodos para crear nombres

1. **Método 1 (Cuadro de Nombres):** Selecciona la celda `B2`. En el *Cuadro de nombres*, borra la dirección `B2`, escribe `Tipo_IVA` (sin espacios) y pulsa *Enter*.


2. **Método 2 (Crear desde la selección):** Selecciona el rango `A1:C5`. Dirígete a la pestaña **Fórmulas**, grupo *Nombres definidos*, y pulsa **Crear desde la selección**. Desmarca la opción *Fila superior*, deja marcada **Columna izquierda** y pulsa **Aceptar**.


3. **Método 3 (Definir nombre):** Selecciona la celda `B5`. Ve a la pestaña **Fórmulas** y haz clic en **Definir nombre**. Comprueba que el campo *Se refiere a* indique `=$B$5`, asígnale el nombre **`Comision_Ventas`** y pulsa **Aceptar**.


### Paso 4: Crear nombres automáticos para filas y columnas

1. Selecciona la tabla de comisiones y ventas situada en **`A8:D11`**.


2. Ve a `Fórmulas > Crear desde la selección`.


3. En la ventana emergente, marca **Fila superior** y **Columna izquierda** al mismo tiempo, y pulsa **Aceptar**.


4. *(Opcional)* Si en cualquier celda fuera de la tabla escribes la fórmula `=SUMA(Enero)`, comprobarás cómo Excel suma directamente los valores de esa columna utilizando su nombre definido.



### Paso 5: Gestionar y cambiar el Ámbito de un nombre (Ámbito Local)

1. Ve a la pestaña **Fórmulas** y haz clic en **Administrador de nombres**.
2. Selecciona el nombre **`Objetivo_Ventas`** y haz clic en el botón **Eliminar** (recuerda que Excel no permite cambiar el ámbito de un nombre ya existente una vez guardado).
3. Selecciona la celda **`B3`**, ve a la pestaña **Fórmulas** y haz clic en **Definir nombre**.
4. En el cuadro de diálogo, escribe el nombre `Objetivo_Ventas` y en el desplegable **Ámbito**, selecciona explícitamente **`Parametros_Base`** en lugar de *Libro*. Haz clic en **Aceptar**. De este modo, el nombre queda configurado con ámbito estrictamente local para esa hoja.

