# Ejercicio 24: Funciones matemáticas avanzadas - Ejercicio Práctico Avanzado: Auditoría Logística y Facturación de Portes

## 1. Contexto de Negocio

Trabajas como analista de logística y costes en una empresa de distribución de suministros industriales con sede en Gijón. La dirección comercial te ha entregado el registro de los envíos interurbanos de la última semana.

Para profesionalizar el control de costes y facturación, debes convertir el registro inicial en una **Tabla Estructurada de Excel** denominada `Tbl_EnviosLogistica`. Tu objetivo es:

1. Auditar los pesos de las expediciones y aplicar las reglas del transportista (cobro por tramos de tonelada/kilo completo al alza).


2. Calcular los costes brutos mediante multiplicación matricial directa sin columnas intermedias.


3. Garantizar la consolidación de importes ignorando incidencias de carga de datos (`#¡VALOR!`).


4. Evaluar las bonificaciones por volumen mediante agregación condicional multidimensional.


5. Comparar los comportamientos de truncamiento sobre penalizaciones por retraso en entregas (diferenciando `ENTERO` de `REDONDEAR.MENOS` con valores negativos).


6. Automatizar un patrón de lectura alterno (cebreado) mediante lógica divisional de filas que no se desconfigure al filtrar o reorganizar datos.



---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente contenido en formato CSV (adaptado a la configuración regional de España con `;` como separador de columnas y `,` como separador decimal) y pégalo directamente en la celda **A1** de una hoja nueva de Excel:

```csv
ID_Envio;Zona_Destino;Peso_Toneladas;Tarifa_Tonelada;Transporte_Nocturno;Seguro_Riesgo;Penalizacion_Retraso
ENV-801;Norte;3,15;85,00;SI;150,25;-12,40
ENV-802;Centro;5,80;72,50;NO;60,00;-8,10
ENV-803;Norte;2,05;90,00;SI;#¡VALOR!;-15,75
ENV-804;Sur;4,10;68,00;NO;0,00;0,00
ENV-805;Norte;6,90;80,00;NO;110,50;-22,30
ENV-806;Centro;8,35;70,00;NO;40,00;-3,80
ENV-807;Norte;1,20;95,00;SI;210,00;-5,60

```

---

## 3. Tareas a Resolver

1. **Conversión a Tabla Estructurada:** Convierte el rango `A1:G8` en una Tabla Estructurada de Excel y asígnale el nombre **`Tbl_EnviosLogistica`**.


2. **Agregación Multidimensional (`SUMAR.SI.CONJUNTO`):** En una celda fuera de la tabla, calcula el total de `Peso_Toneladas` para la `"Zona_Destino"` igual a `"Norte"` que además se hayan realizado con `"Transporte_Nocturno"` igual a `"SI"` utilizando referencias estructuradas.


3. **Multiplicación Matricial Directa (`SUMAPRODUCTO`):** En otra celda externa, calcula el coste global base del transporte multiplicando la columna `Peso_Toneladas` por `Tarifa_Tonelada` en un solo paso y sin crear columnas auxiliares.


4. **Subtotales Dinámicos (`SUBTOTALES`):** Activa la **Fila de Totales** de la tabla estructurada y configura el sumatorio dinámico de la columna `Peso_Toneladas` mediante la función `SUBTOTALES` (código `109`) para que responda a los filtros de interfaz.


5. **Consolidación Robusta ante Errores (`AGREGAR`):** Calcula fuera de la tabla la suma total de la columna `Seguro_Riesgo` omitiendo automáticamente el valor de error `#¡VALOR!`.


6. **Control de Precisión y Reglas de Facturación (`REDONDEAR.MAS` y `REDONDEAR.MENOS`):**
* Añade una columna calculada llamada **`Toneladas_Facturables`**: La agencia de transportes factura por cada fracción de tonelada iniciada como una tonelada completa (`REDONDEAR.MAS` a `0` decimales).


* Añade una columna calculada llamada **`Toneladas_Base`**: Muestra únicamente las toneladas enteras completas para la liquidación de incentivos (`REDONDEAR.MENOS` a `0` decimales).




7. **Comparativa de Truncamiento en Negativos (`ENTERO` vs `REDONDEAR.MENOS`):**
* Añade una columna calculada llamada **`Penalizacion_Entero`**: Evalúa el entero de la columna `Penalizacion_Retraso` mediante `=ENTERO([@[Penalizacion_Retraso]])`.


* Añade una columna calculada llamada **`Penalizacion_Menos`**: Evalúa el truncamiento hacia cero con `=REDONDEAR.MENOS([@[Penalizacion_Retraso]]; 0)`.




8. **Automatización Visual por Filas (`RESIDUO`):** Aplica un Formato Condicional mediante fórmula utilizando `RESIDUO` y `FILA` para colorear en un tono gris o azul claro tenue únicamente las filas pares de la tabla.



---

## 4. Guía de Solución Paso a Paso

### Tarea 1: Convertir en Tabla Estructurada

* **Pasos:**
1. Haz clic en cualquier celda con datos (rango `A1:G8`).
2. Pulsa el atajo de teclado **`Ctrl + T`** (o ve a **Insertar > Tabla**).


3. Comprueba que la casilla *"La tabla tiene encabezados"* esté seleccionada y haz clic en **Aceptar**.


4. Ve a la pestaña **Diseño de tabla**, dirígete al cuadro *Nombre de la tabla* (a la izquierda) y escribe **`Tbl_EnviosLogistica`**.





---

### Tarea 2: Agregación Multidimensional con `SUMAR.SI.CONJUNTO`

* **Explicación:** Permite evaluar simultáneamente múltiples criterios lógicos (`"Norte"` y `"SI"`) en sus respectivos rangos de columna.


* **Fórmula sugerida (en una celda fuera de la tabla, p. ej. `I2`):**
```excel
=SUMAR.SI.CONJUNTO(Tbl_EnviosLogistica[Peso_Toneladas]; Tbl_EnviosLogistica[Zona_Destino]; "Norte"; Tbl_EnviosLogistica[Transporte_Nocturno]; "SI")

```


* **Resultado esperado:** `6,40` toneladas ($3,15 + 2,05 + 1,20$).

---

### Tarea 3: Multiplicación Matricial con `SUMAPRODUCTO`

* **Explicación:** Procesa en memoria la multiplicación elemento a elemento de dos matrices de igual dimensión y las suma en una sola operación.


* **Fórmula sugerida (en `I3`):**
```excel
=SUMAPRODUCTO(Tbl_EnviosLogistica[Peso_Toneladas]; Tbl_EnviosLogistica[Tarifa_Tonelada])

```


* **Resultado esperado:** `2.378,75 €` ($3,15 \times 85 + 5,80 \times 72,50 + \dots$).

---

### Tarea 4: Subtotales Dinámicos con `SUBTOTALES`

* **Pasos:**
1. Haz clic dentro de la tabla y activa **Diseño de tabla > Fila de totales**.
2. En la celda de la Fila de Totales correspondiente a `Peso_Toneladas`, selecciona **Suma** en el desplegable.


* **Fórmula generada:**
```excel
=SUBTOTALES(109; [Peso_Toneladas])

```


* **Explicación:** El argumento `109` asegura que la suma vuelva a calcularse solo con las filas visibles si aplicas un filtro por zona o transporte.



---

### Tarea 5: Consolidación Robusta ante Errores con `AGREGAR`

* **Explicación:** La función `AGREGAR` ejecuta resúmenes estadísticos omitiendo filas con errores sin interrumpir la fórmula.


* **Fórmula sugerida (en `I4`):**
```excel
=AGREGAR(9; 6; Tbl_EnviosLogistica[Seguro_Riesgo])

```


* **Parámetros:** `9` indica la función **SUMA**; `6` le indica a Excel que **ignore los valores de error** (`#¡VALOR!`).


* **Resultado esperado:** `571,25 €` ($150,25 + 60,00 + 0,00 + 110,50 + 40,00 + 210,00$).

---

### Tarea 6: Redondeo Controlado (`REDONDEAR.MAS` y `REDONDEAR.MENOS`)

1. En la celda **`H1`**, escribe `Toneladas_Facturables` y pulsa Intro.
2. En **`H2`**, introduce la fórmula:


```excel
=REDONDEAR.MAS([@[Peso_Toneladas]]; 0)

```


3. En la celda **`I1`**, escribe `Toneladas_Base` y pulsa Intro.
4. En **`I2`**, introduce la fórmula:


```excel
=REDONDEAR.MENOS([@[Peso_Toneladas]]; 0)

```



---

### Tarea 7: Truncamiento en Negativos (`ENTERO` vs `REDONDEAR.MENOS`)

1. En **`J1`**, escribe `Penalizacion_Entero`.
2. En **`J2`**, introduce la fórmula:


```excel
=ENTERO([@[Penalizacion_Retraso]])

```


3. En **`K1`**, escribe `Penalizacion_Menos`.
4. En **`K2`**, introduce la fórmula:


```excel
=REDONDEAR.MENOS([@[Penalizacion_Retraso]]; 0)

```



#### Tabla Resumen de Resultados Esperados (Columnas Calculadas)

| ID_Envio | Peso_Toneladas | Toneladas_Facturables (`REDONDEAR.MAS`) | Toneladas_Base (`REDONDEAR.MENOS`) | Penalizacion_Retraso | Penalizacion_Entero (`ENTERO`) | Penalizacion_Menos (`REDONDEAR.MENOS`) |
| --- | --- | --- | --- | --- | --- | --- |
| ENV-801 | **3,15** | **4** | **3** | **-12,40** | **-13** | **-12** |
| ENV-802 | **5,80** | **6** | **5** | **-8,10** | **-9** | **-8** |
| ENV-803 | **2,05** | **3** | **2** | **-15,75** | **-16** | **-15** |
| ENV-804 | **4,10** | **5** | **4** | **0,00** | **0** | **0** |
| ENV-805 | **6,90** | **7** | **6** | **-22,30** | **-23** | **-22** |
| ENV-806 | **8,35** | **9** | **8** | **-3,80** | **-4** | **-3** |
| ENV-807 | **1,20** | **2** | **1** | **-5,60** | **-6** | **-5** |

> 📌 **Explicación Didáctica sobre Valores Negativos:**
> * **`ENTERO(-12,40)`** devuelve **`-13`** porque busca siempre el número entero estrictamente inferior (alejándose del cero sobre la recta numérica hacia la izquierda).
> 
> 
> * **`REDONDEAR.MENOS(-12,40; 0)`** devuelve **`-12`** porque trunca los decimales aproximándose siempre hacia el cero.
> 
> 
> 
> 

---

### Tarea 8: Lógica Divisional e Interruptor Binario (`RESIDUO`)

1. Selecciona todo el rango de datos de la tabla estructurada (por ejemplo, `A2:K8`).
2. Dirígete a la pestaña **Inicio > Formato condicional > Nueva regla**.
3. Haz clic en *"Utilice una fórmula que determine las celdas para aplicar formato"*.
4. Escribe la fórmula exacta con la coma/punto y coma correspondiente:


```excel
=RESIDUO(FILA(); 2) = 0

```


5. Haz clic en **Formato**, selecciona un color de relleno gris/azul claro tenue y pulsa **Aceptar**.

