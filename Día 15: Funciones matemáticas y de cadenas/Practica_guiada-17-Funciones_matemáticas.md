# Práctica guiada 17: Funciones matemáticas

## 1. Contexto de Negocio

Trabajas como analista de operaciones en una empresa de servicios tecnológicos e industriales en Asturias. La dirección te ha entregado el parte operativo semanal de los técnicos.

Para profesionalizar el modelo, debes convertir el listado inicial en una **Tabla Estructurada de Excel** llamada `Tbl_ParteTrabajo`. A partir de ella, consolidarás las horas mediante criterios multidimensionales, calcularás los costes totales con un motor matricial, aplicarás reglas estrictas de facturación y producción al alza y a la baja, asegurarás los cálculos globales frente a valores de error y diseñarás un cebreado visual dinámico que resista la inserción o eliminación de registros.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque CSV (delimitado por punto y coma `;` adaptado a la configuración regional de España) y pégalo directamente en la celda **A1** de una hoja nueva de Excel:

```csv
Servicio;Horas_Reales;Tarifa_Hora;Turno_Noche;Importe_Material
Mantenimiento;10,25;50,00;SI;120,50
Soporte;8,50;60,00;NO;45,00
Mantenimiento;12,75;55,00;SI;#¡VALOR!
Ventas;7,10;45,00;NO;0,00
Mantenimiento;9,00;52,00;NO;85,25
Soporte;11,80;48,00;NO;15,00
Mantenimiento;6,40;58,00;SI;300,00

```

---

## 3. Tareas a Resolver

1. **Conversión a Tabla Estructurada:** Convierte el rango `A1:E8` en una Tabla Estructurada de Excel con encabezados. Asígnale el nombre **`Tbl_ParteTrabajo`**.


2. **Agregación Multidimensional (`SUMAR.SI.CONJUNTO`):** Calcula el total de horas reales dedicadas al servicio de `"Mantenimiento"` realizadas en `"Turno_Noche"` (`"SI"`) utilizando referencias estructuradas.


3. **Cálculo Matricial Directo (`SUMAPRODUCTO`):** Calcula el coste total bruto multiplicando las horas reales por la tarifa horaria en un solo paso, utilizando el objeto tabla.


4. **Subtotales Robustos ante Errores (`AGREGAR`):** Calcula la suma total de la columna `Importe_Material` ignorando automáticamente el error `#¡VALOR!` presente en los datos.


5. **Control de Precisión y Reglas de Negocio (`REDONDEAR.MAS` y `REDONDEAR.MENOS`):**
* Crea una columna calculada llamada **`Horas_Facturables`** que aplique la regla de facturación de la empresa: toda fracción de hora se cobra como hora completa (`REDONDEAR.MAS` a `0` decimales).


* Crea otra columna calculada llamada **`Horas_Enteras`** que compute únicamente las horas enteras completadas para el control de producción (`REDONDEAR.MENOS` a `0` decimales).




6. **Diseño Visual Dinámico por Filas (`RESIDUO`):** Aplica una regla de formato condicional con las funciones `RESIDUO` y `FILA` para colorear en un tono gris claro las filas pares de la tabla.



---

## 4. Guía de Solución Paso a Paso

### Tarea 1: Convertir en Tabla Estructurada

* **Pasos en Excel:**
1. Haz clic en cualquier celda de los datos (`A1:E8`).
2. Presiona el atajo de teclado **`Ctrl + T`** (o ve a **Insertar > Tabla**).


3. Asegúrate de que la casilla *"La tabla tiene encabezados"* esté **activada** y pulsa **Aceptar**.


4. Con la tabla seleccionada, ve a la pestaña superior **Diseño de tabla**. En el extremo izquierdo (*Nombre de la tabla*), cambia el nombre genérico por **`Tbl_ParteTrabajo`** y pulsa Intro.





---

### Tarea 2: Agregación con `SUMAR.SI.CONJUNTO`

* **Explicación:** Evalúa simultáneamente que el servicio sea `"Mantenimiento"` y el turno de noche sea `"SI"`.


* **Fórmula sugerida (en una celda fuera de la tabla, p. ej. `H2`):**
```excel
=SUMAR.SI.CONJUNTO(Tbl_ParteTrabajo[Horas_Reales]; Tbl_ParteTrabajo[Servicio]; "Mantenimiento"; Tbl_ParteTrabajo[Turno_Noche]; "SI")

```


* **Pasos:** Escribe `=SUMAR.SI.CONJUNTO(` y haz clic sobre los encabezados o rangos de la tabla `Tbl_ParteTrabajo` para que Excel inserte automáticamente las referencias estructuradas.



---

### Tarea 3: Cálculo matricial con `SUMAPRODUCTO`

* **Explicación:** Multiplica elemento a elemento la columna de horas por la columna de tarifas y suma los productos en memoria sin requerir columnas auxiliares.


* **Fórmula sugerida:**
```excel
=SUMAPRODUCTO(Tbl_ParteTrabajo[Horas_Reales]; Tbl_ParteTrabajo[Tarifa_Hora])

```


* **Pasos:** Introduce la función pasando como argumentos las dos columnas completas de la tabla separadas por punto y coma (`;`).



---

### Tarea 4: Subtotales avanzados con `AGREGAR`

* **Explicación:** La función `AGREGAR` permite aplicar funciones de resumen omitiendo errores explícitamente mediante el argumento `6`.


* **Fórmula sugerida:**
```excel
=AGREGAR(9; 6; Tbl_ParteTrabajo[Importe_Material])

```


* **Pasos:**
1. Escribe `=AGREGAR(`.
2. Selecciona `9` (Función SUMA).


3. Escribe `;` y selecciona `6` (Opciones: Ignorar valores de error).


4. Selecciona la columna `Tbl_ParteTrabajo[Importe_Material]` y cierra el paréntesis.



---

### Tarea 5: Control de precisión (`REDONDEAR.MAS` y `REDONDEAR.MENOS`)

* **Explicación:** Observa el efecto real sobre valores como `10,25` o `12,75`:


* `REDONDEAR.MAS(10,25; 0)` eleva el valor a **`11`**.


* `REDONDEAR.MENOS(10,25; 0)` trunca el valor a **`10`**.




* **Pasos en Excel:**
1. Haz clic en la celda **`F1`**, escribe `Horas_Facturables` y pulsa Intro. La tabla se ampliará automáticamente incorporando la nueva columna.


2. En la celda `F2`, introduce la fórmula con referencia estructurada a la fila actual (`@`):


```excel
=REDONDEAR.MAS([@[Horas_Reales]]; 0)

```


*(Verás cómo Excel completa automáticamente toda la columna calculada)*.


3. Haz clic en la celda **`G1`**, escribe `Horas_Enteras` y pulsa Intro.


4. En la celda `G2`, introduce:
```excel
=REDONDEAR.MENOS([@[Horas_Reales]]; 0)

```




* **Tabla comparativa de resultados esperados en el objeto tabla:**

| Servicio | Horas_Reales | Horas_Facturables (`REDONDEAR.MAS`) | Horas_Enteras (`REDONDEAR.MENOS`) |
| --- | --- | --- | --- |
| Mantenimiento | **10,25** | **11** | **10** |
| Soporte | **8,50** | **9** | **8** |
| Mantenimiento | **12,75** | **13** | **12** |
| Ventas | **7,10** | **8** | **7** |
| Mantenimiento | **9,00** | **9** | **9** |
| Soporte | **11,80** | **12** | **11** |
| Mantenimiento | **6,40** | **7** | **6** |

---

### Tarea 6: Lógica de filas con `RESIDUO` y Formato Condicional

* **Explicación:** Devuelve `0` para las filas cuyos números sean pares. Al combinarlo con la función `FILA()`, crea un patrón de lectura alterno totalmente dinámico.


* **Pasos en Excel:**
1. Selecciona el rango con los datos de la tabla (por ejemplo, `A2:G8`).
2. Ve a **Inicio > Formato condicional > Nueva regla**.
3. Elige la opción *"Utilice una fórmula que determine las celdas para aplicar formato"*.
4. Escribe la fórmula:
```excel
=RESIDUO(FILA(); 2) = 0

```


5. Haz clic en **Formato**, selecciona un color de relleno gris claro y pulsa **Aceptar**.

