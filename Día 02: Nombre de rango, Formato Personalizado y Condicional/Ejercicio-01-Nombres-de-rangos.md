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


11. Localiza el nombre **`Objetivo_Ventas`**, haz clic en **Modificar** y cambia su ámbito de **Libro** (global) a **`Parametros_Base`** (local de la hoja).


12. Comprueba cómo en el Administrador de nombres aparecen reflejados todos los rangos creados, sus valores actuales y sus ámbitos.
