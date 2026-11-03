# Ejercicio 24: Funciones matemáticas avanzadas

En este ejercicio utilizaremos una **Tabla Estructurada** nombrada `Tbl_ParteTrabajo` y combinaremos:

1. **`SUMAR.SI.CONJUNTO`**: Agregación multidimensional con varios criterios.


2. **`SUMAPRODUCTO`**: Multiplicación matricial sin columnas auxiliares.


3. **`SUBTOTALES`**: Subtotal dinámico que respeta los filtros aplicados.


4. **`AGREGAR`**: Subtotal avanzado que omite errores estructurales (`#¡VALOR!`) y filtros.


5. **`REDONDEAR.MAS`**: Redondeo al alza alejado de cero (para reglas de facturación).


6. **`REDONDEAR.MENOS`**: Redondeo hacia el cero (para conteo estricto de horas completadas).


7. **`ENTERO`**: Truncamiento al entero inferior más próximo (incluyendo la diferencia de comportamiento con valores negativos).


8. **`RESIDUO`**: Lógica de división e interruptor binario para automatización visual con formato condicional.



---

### 1. Contexto de Negocio

Trabajas como analista de operaciones en una empresa de servicios industriales y tecnológicos en Asturias. La dirección necesita auditar el parte semanal de trabajo de los técnicos para preparar la facturación a clientes, controlar los costes de producción interna y ajustar las desviaciones presupuestarias acumuladas.

Para asegurar la escalabilidad del modelo, trabajarás sobre una **Tabla Estructurada de Excel**. Deberás procesar horas de servicio con decimales, evaluar reglas estrictas de precisión financiera, asegurar los sumatorios globales ante registros que contienen errores, realizar comparativas de truncamiento de penalizaciones negativas y aplicar una lectura visual alternada (cebreado) totalmente dinámica.

---

### 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de texto en formato CSV (delimitado por punto y coma `;` adaptado a la configuración regional de España) y pégalo directamente en la celda **A1** de una hoja nueva de Excel:

```csv
ID_Parte;Servicio;Horas_Reales;Tarifa_Hora;Turno_Noche;Importe_Material;Ajuste_Presupuesto
PAR-101;Mantenimiento;10,25;50,00;SI;120,50;-2,20
PAR-102;Soporte;8,50;60,00;NO;45,00;-1,80
PAR-103;Mantenimiento;12,75;55,00;SI;#¡VALOR!;-3,50
PAR-104;Ventas;7,10;45,00;NO;0,00;0,00
PAR-105;Mantenimiento;9,00;52,00;NO;85,25;-4,10
PAR-106;Soporte;11,80;48,00;NO;15,00;-0,50
PAR-107;Mantenimiento;6,40;58,00;SI;300,00;-1,20

```

---

### 3. Tareas a Resolver

1. **Estructuración de Datos:** Convierte el rango `A1:G8` en una Tabla Estructurada con el nombre **`Tbl_ParteTrabajo`**.


2. **Agregación Multidimensional (`SUMAR.SI.CONJUNTO`):** Calcula el total de horas reales acumuladas para el servicio de `"Mantenimiento"` realizadas en `"Turno_Noche = SI"` utilizando referencias estructuradas.


3. **Multiplicación Matricial Directa (`SUMAPRODUCTO`):** Calcula el coste total bruto de mano de obra en un solo paso multiplicando la columna `Horas_Reales` por `Tarifa_Hora` sin añadir columnas intermedias.


4. **Subtotales ante Filtros e Interfaz (`SUBTOTALES`):** Añade la **Fila de Totales** a la tabla y configura la celda de la columna `Horas_Reales` con la función `SUBTOTALES` (código `109`) para que el sumatorio responda visualmente a los filtros aplicados.


5. **Integridad ante Errores (`AGREGAR`):** Calcula fuera de la tabla el importe total de la columna `Importe_Material` mediante la función `AGREGAR` para omitir automáticamente el valor `#¡VALOR!` de la fila 4.


6. **Control de Precisión y Reglas de Facturación (`REDONDEAR.MAS` y `REDONDEAR.MENOS`):**
* Añade la columna **`Horas_Facturables`**: Aplica la regla comercial donde las fracciones de hora se cobren como hora completa (`REDONDEAR.MAS` a `0` decimales).


* Añade la columna **`Horas_Enteras`**: Calcula solo las horas completas trabajadas para el cómputo estricto de producción (`REDONDEAR.MENOS` a `0` decimales).




7. **Comparativa de Truncamiento y Negativos (`ENTERO` vs `REDONDEAR.MENOS`):**
* Añade la columna **`Ajuste_Entero`**: Trunca la columna `Ajuste_Presupuesto` utilizando `=ENTERO([@[Ajuste_Presupuesto]])`.


* Añade la columna **`Ajuste_Menos`**: Trunca la misma columna utilizando `=REDONDEAR.MENOS([@[Ajuste_Presupuesto]]; 0)`.


* *Analiza la diferencia entre ambos resultados con números negativos*.




8. **Automatización Visual por Filas (`RESIDUO`):** Aplica una regla de Formato Condicional con `RESIDUO` y `FILA` para colorear en un verde claro tenue únicamente las filas pares de la tabla.



---

### 4. Guía de Solución Paso a Paso

#### Tarea 1: Convertir en Tabla Estructurada

1. Selecciona cualquier celda del rango `A1:G8`.
2. Presiona **`Ctrl + T`** (o ve a **Insertar > Tabla**).


3. Verifica que la opción *"La tabla tiene encabezados"* esté marcada y haz clic en **Aceptar**.


4. En la pestaña superior **Diseño de tabla**, ve a **Nombre de la tabla** (extremo izquierdo) y escribe **`Tbl_ParteTrabajo`**.



---

#### Tarea 2: Agregación Multidimensional con `SUMAR.SI.CONJUNTO`

* **Fórmula (en una celda libre fuera de la tabla, p. ej. `I2`):**
```excel
=SUMAR.SI.CONJUNTO(Tbl_ParteTrabajo[Horas_Reales]; Tbl_ParteTrabajo[Servicio]; "Mantenimiento"; Tbl_ParteTrabajo[Turno_Noche]; "SI")

```


* **Explicación:** Evalúa simultáneamente dos criterios (`"Mantenimiento"` y `"SI"`) en sus respectivos rangos de columna antes de sumar.



---

#### Tarea 3: Multiplicación Matricial con `SUMAPRODUCTO`

* **Fórmula (en `I3`):**
```excel
=SUMAPRODUCTO(Tbl_ParteTrabajo[Horas_Reales]; Tbl_ParteTrabajo[Tarifa_Hora])

```


* **Explicación:** Procesa internamente en memoria los productos de cada fila ($10,25 \times 50,00 + 8,50 \times 60,00 + \dots$) y devuelve el total acumulado sin necesidad de crear una columna de importe intermedio.



---

#### Tarea 4: Subtotales Dinámicos con `SUBTOTALES`

1. Haz clic dentro de la tabla y ve a **Diseño de tabla > Fila de totales**.


2. En la celda de total de la columna `Horas_Reales`, abre el menú desplegable y selecciona **Suma**.


3. Excel generará la fórmula:
```excel
=SUBTOTALES(109; [Horas_Reales])

```



* **Explicación:** El código `109` indica una suma que ignora automáticamente las filas que hayan sido ocultadas mediante filtros de tabla.



---

#### Tarea 5: Subtotales Robustos ante Errores con `AGREGAR`

* **Fórmula (en `I4`):**
```excel
=AGREGAR(9; 6; Tbl_ParteTrabajo[Importe_Material])

```


* **Explicación:**
* El argumento `9` ejecuta la operación **SUMA**.


* El argumento `6` indica a Excel que **ignore los valores de error** (como `#¡VALOR!`).





---

#### Tarea 6: Redondeos Controlados (`REDONDEAR.MAS` y `REDONDEAR.MENOS`)

1. Escribe el nombre de la columna **`Horas_Facturables`** en la celda `H1`.


2. En `H2`, introduce la fórmula:


```excel
=REDONDEAR.MAS([@[Horas_Reales]]; 0)

```


3. Escribe **`Horas_Enteras`** en la celda `I1`.


4. En `I2`, introduce la fórmula:


```excel
=REDONDEAR.MENOS([@[Horas_Reales]]; 0)

```



---

#### Tarea 7: Truncamiento en Negativos (`ENTERO` vs `REDONDEAR.MENOS`)

1. Añade las columnas **`Ajuste_Entero`** (en `J1`) y **`Ajuste_Menos`** (en `K1`).


2. En `J2`, escribe:
```excel
=ENTERO([@[Ajuste_Presupuesto]])

```


3. En `K2`, escribe:
```excel
=REDONDEAR.MENOS([@[Ajuste_Presupuesto]]; 0)

```



* **Tabla comparativa de resultados obtenidos en las tareas 6 y 7:**

| ID_Parte | Horas_Reales | Horas_Facturables (`REDONDEAR.MAS`) | Horas_Enteras (`REDONDEAR.MENOS`) | Ajuste_Presupuesto | Ajuste_Entero (`ENTERO`) | Ajuste_Menos (`REDONDEAR.MENOS`) |
| --- | --- | --- | --- | --- | --- | --- |
| PAR-101 | **10,25** | **11** | **10** | **-2,20** | **-3** | **-2** |
| PAR-102 | **8,50** | **9** | **8** | **-1,80** | **-2** | **-1** |
| PAR-103 | **12,75** | **13** | **12** | **-3,50** | **-4** | **-3** |
| PAR-104 | **7,10** | **8** | **7** | **0,00** | **0** | **0** |
| PAR-105 | **9,00** | **9** | **9** | **-4,10** | **-5** | **-4** |
| PAR-106 | **11,80** | **12** | **11** | **-0,50** | **-1** | **0** |
| PAR-107 | **6,40** | **7** | **6** | **-1,20** | **-2** | **-1** |

> 💡 **Nota Didáctica sobre Negativos:**
> Observa cómo para `-2,20`:
> 
> 
> * `ENTERO(-2,20)` devuelve **`-3`** porque busca siempre el entero inferior más próximo (se aleja del cero en el eje negativo).
> 
> 
> * `REDONDEAR.MENOS(-2,20; 0)` devuelve **`-2`** porque trunca hacia el cero.
> 
> 
> 
> 

---

#### Tarea 8: Lógica Divisional e Interruptor Binario (`RESIDUO`)

1. Selecciona todas las celdas de datos de la tabla (rango `A2:K8`).
2. Ve a la pestaña **Inicio > Formato condicional > Nueva regla**.
3. Selecciona *"Utilice una fórmula que determine las celdas para aplicar formato"*.
4. En el campo de fórmula, introduce:


```excel
=RESIDUO(FILA(); 2) = 0

```


5. Haz clic en **Formato**, elige un color de relleno verde muy claro y pulsa **Aceptar**.

