# Ejercicio Práctico: Análisis Comercial y de Alojamiento Turístico en Asturias

## 1. Contexto de Negocio

La **Dirección General de Turismo del Principado de Asturias** desea analizar el comportamiento de la ocupación hotelera y la contratación de experiencias turísticas durante el último periodo vacacional. Para apoyar la toma de decisiones en el sector de la hostelería y el turismo rural, el departamento de análisis de datos ha recopilado una muestra de reservas y operaciones comerciales en distintos concejos de la región.

Tu objetivo como analista de datos es procesar esta información utilizando las herramientas avanzadas de Excel (tablas estructuradas, funciones lógicas y de texto avanzadas, y segmentación de datos) para evaluar el rendimiento comercial de las agencias colaboradoras y las pernoctaciones registradas.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de datos y pégalo directamente en la celda **A1** de una hoja nueva de Excel. Asegúrate de convertirlo en **Tabla Estructurada** (`Ctrl + T`) y asígnale el nombre **`Tbl_TurismoAsturias`**.

*(Nota: Los datos utilizan el punto y coma `;` como separador de columnas y la coma `,` como separador decimal para ajustarse estrictamente a la configuración regional de España).*

```csv
ID_Reserva;Concejo;Zona_Turistica;Agencia;Tipo_Alojamiento;Noches;Importe_Total;Valoracion_Cliente
RES-501;Oviedo;Comicuenca;AsturiasNatural;Hotel;3;450,00;4,8
RES-502;Gijón;Costa Verde;NorteViajes;Apartamento;5;620,50;4,2
RES-503;Llanes;Costa Verde;PicosBooking;Casa Aldea;7;980,00;4,9
RES-504;Cangas de Onís;Picos de Europa;AsturiasNatural;Hotel;2;310,00;3,9
RES-505;Avilés;Comicuenca;NorteViajes;Hotel;3;390,00;4,0
RES-506;Ribadesella;Costa Verde;PicosBooking;Casa Aldea;4;560,00;4,7
RES-507;Cabrales;Picos de Europa;AsturiasNatural;Casa Aldea;6;840,00;4,5
RES-508;Oviedo;Comicuenca;NorteViajes;Apartamento;2;240,00;3,8
RES-509;Gijón;Costa Verde;AsturiasNatural;Hotel;4;680,00;4,6
RES-510;Llanes;Costa Verde;NorteViajes;Casa Aldea;5;750,00;4,3
RES-511;Cangas de Onís;Picos de Europa;PicosBooking;Hotel;3;420,00;4,4
RES-512;Ribadesella;Costa Verde;AsturiasNatural;Apartamento;3;360,00;4,1

```

---

## 3. Tareas a Resolver

1. **Preparación del Entorno:** Inserta los datos en Excel, dales formato de Tabla Estructurada bajo el nombre `Tbl_TurismoAsturias`, y comprueba que las columnas numéricas (`Noches`, `Importe_Total`, `Valoracion_Cliente`) mantengan su formato correcto (moneda y decimales con coma).
2. **Clasificación de Estancias (Función `SI` y `SI.CONJUNTO`):**
* Añade una nueva columna a la derecha de la tabla llamada `Tipo_Estancia`.
* Utiliza una fórmula basada en la función `SI` (o `SI.CONJUNTO`) para clasificar las reservas según las noches contratadas:
* Si el número de noches es menor o igual a 3, etiquétalo como `"Escapada breve"`.
* Si es superior a 3 y menor o igual a 5, etiquétalo como `"Estancia media"`.
* Si es mayor a 5, etiquétalo como `"Vacaciones largas"`.




3. **Informe Resumen con Tabla Dinámica:**
* Inserta una nueva Tabla Dinámica en otra hoja llamada `TD_Turismo`.
* Coloca el campo `Zona_Turistica` en **FILAS** y `Tipo_Alojamiento` en **COLUMNAS**.
* Arrastra el campo `Importe_Total` al área de **VALORES**, configúralo como **Suma**, renómbralo como `"Facturación Total"` y asígnale el formato de número de Moneda (`€`).


4. **Filtros Interactivos:**
* Añade un **Segmentador de datos (Slicer)** para el campo `Agencia` que permita filtrar dinámicamente el informe de la tabla dinámica con un solo clic.



---

## 4. Guía de Solución Paso a Paso

### Paso 1: Preparación y Creación de la Tabla Estructurada

1. Selecciona el bloque de datos proporcionado arriba, cópialo (`Ctrl + C`) y pégalo en la celda **A1** de una hoja limpia en Excel (`Ctrl + V`).
2. Haz clic en cualquier celda dentro de los datos insertados.
3. Ve a la pestaña **Insertar** en la cinta de opciones y haz clic en **Tabla** (o utiliza el atajo `Ctrl + T`).
4. Asegúrate de marcar la casilla *"La tabla tiene encabezados"* y pulsa **Aceptar**.
5. Con la tabla seleccionada, dirígete a la pestaña contextual **Diseño de tabla** y escribe `Tbl_TurismoAsturias` en el cuadro **Nombre de tabla** (esquina superior izquierda).

---

### Paso 2: Creación de Columna Calculada con Funciones Lógicas

1. Haz clic en la celda situada inmediatamente a la derecha del último encabezado (`I1`), escribe el título `Tipo_Estancia` y presiona *Intro* (verás cómo la Tabla Estructurada se expande automáticamente).
2. Para clasificar las estancias según las reglas de negocio utilizando un condicional anidado, introduce la siguiente fórmula en la primera celda de datos de la columna nueva (`I2`):
```excel
=SI([@Noches]<=3; "Escapada breve"; SI([@Noches]<=5; "Estancia media"; "Vacaciones largas"))

```


3. Presiona *Intro*. Excel rellenará automáticamente toda la columna gracias a las referencias estructuradas.

---

### Paso 3: Inserción y Configuración de la Tabla Dinámica

1. Haz clic en cualquier celda dentro de `Tbl_TurismoAsturias`.
2. Dirígete a **Insertar** > **Tabla dinámica** > **Desde una tabla o rango**.
3. Selecciona **Nueva hoja de cálculo** y pulsa **Aceptar**.
4. Cambia el nombre de la nueva pestaña de la hoja de cálculo por **`TD_Turismo`**.
5. En el panel de campos de la tabla dinámica (derecha):
* Arrastra el campo **`Zona_Turistica`** a la sección **FILAS**.
* Arrastra el campo **`Tipo_Alojamiento`** a la sección **COLUMNAS**.
* Arrastra el campo **`Importe_Total`** a la sección **VALORES**.


6. Configura el campo de valor:
* Haz clic sobre `Suma de Importe_Total` en el área de valores y selecciona **Configuración de campo de valor...**
* Cambia el nombre personalizado a `Facturación Total`.
* Haz clic en el botón **Formato de número**, selecciona la categoría **Moneda**, asigna **2 decimales** y el símbolo **€**. Pulsa **Aceptar** en ambas ventanas.



---

### Paso 4: Incorporación de Segmentadores de Datos (Slicers)

1. Haz clic en cualquier celda de la Tabla Dinámica para activar las pestañas contextuales superiores.
2. Ve a la pestaña **Analizar tabla dinámica** (o *Análisis de tabla dinámica*).
3. En el grupo *Filtrar*, haz clic en **Insertar segmentación de datos**.
4. En la ventana emergente, marca la casilla correspondiente al campo **`Agencia`** y haz clic en **Aceptar**.
5. Aparecerá un panel flotante con los botones de las agencias turísticas. Haz clic sobre cualquiera de ellas (por ejemplo, *AsturiasNatural*) para comprobar cómo la Tabla Dinámica filtra de forma instantánea la facturación por zona y tipo de alojamiento en función de la agencia seleccionada.
