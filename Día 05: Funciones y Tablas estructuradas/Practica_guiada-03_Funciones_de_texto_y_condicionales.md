# Práctica guiada: Normalización, conversión y clasificación de envíos

## 1. Objetivo

En esta práctica vas a construir, paso a paso, una herramienta para gestionar los envíos de una empresa logística.

Partiremos de un listado de entradas recibido desde diferentes delegaciones con problemas habituales de integración entre sistemas:

* Códigos escritos en minúsculas.


* Espacios innecesarios al principio o al final.


* Nombres de delegaciones deshomogeneizados.


* Subcadenas extraídas mediante funciones de texto que quedan almacenadas como texto y deben operarse matemáticamente (conversión texto a número).


* Números que deben formatearse con ceros a la izquierda para generar identificadores normalizados (conversión número a texto).


* Asignación automática de tarifas mediante funciones condicionales (`SI.CONJUNTO`).



---

## 2. Conjunto de Datos (Dataset)

Crea un libro nuevo y nombra la hoja como `Envios`. Copia el siguiente bloque de datos con formato CSV (delimitado por punto y coma `;` adaptado a la configuración regional de España) y pégalo directamente en la celda `A1`.

```text
Codigo_Entrada	Delegacion	Producto	Peso_kg	Unidades
  bcn-7741-exp 	Barcelona	teclado mecánico	14,5	12
mad-2230-std	MADRID	monitor 24 pulgadas	2,1	8
 sev-5512-exp	Sevilla	impresora láser	7,8	5
VAL-3489-STD	valencia	disco externo	1,9	20
 bil-6621-exp 	BILBAO	ordenador portátil	11,4	4
  bcn-9182-std	barcelona	webcam full hd	3,2	15
MAD-4470-EXP	madrid	servidor rack	18,6	2
sev-1205-std	 SEVILLA 	teclado inalámbrico	2,7	25
 val-7301-exp	Valencia	monitor profesional	6,5	6
BIL-2854-STD	bilbao	lector código barras	1,4	18
 bcn-6048-exp	BARCELONA	switch red	9,7	7
MAD-8316-STD	 Madrid 	impresora térmica	3,8	10
```

---

## 3. Tareas a Resolver

1. **Limpieza y normalización inicial:** Limpiar espacios y homogeneizar a mayúsculas/formato propio.


2. **Extracción de componentes:** Separar código de delegación, número de operación y tipo de envío.


3. **Conversión de Texto a Número (`VALOR`):** Convertir la subcadena de texto extraída del número de operación a un número real para poder realizar un incremento numérico.


4. **Construcción de texto normalizado:** Generar descripciones formateadas.


5. **Conversión de Número a Texto (`TEXTO`):** Convertir el número de operación modificado de nuevo a texto manteniendo una longitud fija de 5 dígitos con ceros a la izquierda (ejemplo: `07741`).


6. **Clasificación condicional y cálculo:** Aplicar reglas de negocio con `SI.CONJUNTO` para determinar categoría y tarifa, y calcular el coste total.


7. **Generación del código final de seguimiento:** Combinar los bloques normalizados.



---

## 4. Guía de Solución Paso a Paso

### Fase 1: Limpieza de texto

* **Columna F (`Codigo_Normalizado`):** En `F2`, elimina espacios y convierte a mayúsculas:

```excel
=MAYUSC(ESPACIOS(A2))
```

Copia la fórmula hacia abajo.

### ¿Qué estamos consiguiendo?

La fórmula realiza dos operaciones:

1. `ESPACIOS(A2)` elimina los espacios innecesarios.
2. `MAYUSC(...)` convierte el código a mayúsculas.

Por ejemplo: `bcn-7741-exp` se convierte en `BCN-7741-EXP`

* **Columna G (`Delegacion_Normalizada`):** En `G2`, elimina espacios y aplica formato de tipo nombre propio:


```excel
=NOMPROPIO(ESPACIOS(B2))

```



---

### Fase 2: Extracción de subcadenas

* **Columna H (`Codigo_Delegacion`):** Extrae las 3 primeras letras de la izquierda:


```excel
=IZQUIERDA(F2;3)

```


* **Columna J (`Tipo_Envio`):** Extrae las 3 letras de la derecha:


```excel
=DERECHA(F2;3)

```


* **Columna I (`Num_Op_Texto`):** Extrae los 4 caracteres centrales a partir de la posición 5:


```excel
=EXTRAE(F2;5;4)

```



---

### Fase 3: Conversión de Texto a Número (`VALOR`)

> **Concepto clave:** Las funciones de extracción de texto (`IZQUIERDA`, `DERECHA`, `EXTRAE`) siempre devuelven una cadena de texto, incluso si los caracteres son dígitos numéricos. Si intentamos hacer cálculos sobre `I2` o comparaciones numéricas estrictas, podemos obtener errores como `#¡VALOR!`.
> 
> 

* **Columna K (`Num_Op_Numero`):** Convierte la cadena extraída en la celda `I2` en un valor numérico real.
En `K2` escribe:


```excel
=VALOR(I2)

```


* **Columna L (`Num_Op_Incrementado`):** Para comprobar que el dato ahora es verdaderamente numérico, suma un incremento de `100` al número de operación.
En `L2` escribe:


```excel
=K2+100

```



---

### Fase 4: Conversión de Número a Texto (`TEXTO`)

> **Concepto clave:** La función `TEXTO` toma un número real y lo convierte en una cadena de texto aplicando un formato específico (como rellenar con ceros a la izquierda o dar formato de fecha/moneda).
> 
> 

* **Columna M (`Num_Op_Formateado`):** La empresa exige que todos los códigos de operación tengan exactamente **5 dígitos en formato texto**, agregando ceros a la izquierda si el número es menor a 10.000.
En `M2` escribe:


```excel
=TEXTO(L2;"00000")

```


*Ejemplo:* El valor numérico `7841` pasa a ser el texto `"07841"`.

---

### Fase 5: Construcción de descripciones y clasificación

* **Columna N (`Descripcion_Envio`):** Concatena el código de delegación, la delegación normalizada y el producto en formato propio:


```excel
=H2&" - "&G2&" - "&NOMPROPIO(C2)

```


* **Columna O (`Categoria_Envio`):** En `O2`, evalúa el peso del paquete (`D2`):


```excel
=SI.CONJUNTO(D2>10;"Pesada";D2>=3;"Media";VERDADERO;"Ligera")

```


* **Columna P (`Tarifa_Envio`):** En `P2`, asigna la tarifa en euros según el peso:


```excel
=SI.CONJUNTO(D2>10;15;D2>=3;8;VERDADERO;3)

```


* **Columna Q (`Coste_Total`):** Multiplica las unidades por la tarifa:


```excel
=E2*P2

```


(Aplica formato de celda de Moneda `#.##0,00 €`).



---

### Fase 6: Código de Seguimiento Final

* **Columna R (`Codigo_Seguimiento`):** Une el código de la delegación, el nuevo número de operación formateado como texto y el tipo de envío:


```excel
=H2&"-"&M2&"-"&I2

```


*Resultado de ejemplo:* `BCN-07841-EXP`

>Repetirlo sustituyendo los operadores `&` por las funciones CONCAT y UNIRCADENAS.

---

## 5. Estructura de Columnas Resultante

| Columna | Nombre | Función principal / Tipo de conversión |
| --- | --- | --- |
| **A** | `Codigo_Entrada` | Dato de origen

 |
| **B** | `Delegacion` | Dato de origen

 |
| **C** | `Producto` | Dato de origen

 |
| **D** | `Peso_kg` | Dato de origen

 |
| **E** | `Unidades` | Dato de origen

 |
| **F** | `Codigo_Normalizado` | `=MAYUSC(ESPACIOS(A2))`<br> |
| **G** | `Delegacion_Normalizada` | `=NOMPROPIO(ESPACIOS(B2))`<br> |
| **H** | `Codigo_Delegacion` | `=IZQUIERDA(F2;3)`<br> |
| **I** | `Tipo_Envio` | `=DERECHA(F2;3)`<br> |
| **J** | `Num_Op_Texto` | `=EXTRAE(F2;5;4)`<br> |
| **K** | `Num_Op_Numero` | `=VALOR(J2)` **(Texto $\rightarrow$ Número)**<br> |
| **L** | `Num_Op_Incrementado` | `=K2+100` (Operación matemática)

 |
| **M** | `Num_Op_Formateado` | `=TEXTO(L2;"00000")` **(Número $\rightarrow$ Texto)**<br> |
| **N** | `Descripcion_Envio` | `=H2&" - "&G2&" - "&NOMPROPIO(C2)`<br> |
| **O** | `Categoria_Envio` | `=SI.CONJUNTO(D2>10;"Pesada";D2>=3;"Media";VERDADERO;"Ligera")`<br> |
| **P** | `Tarifa_Envio` | `=SI.CONJUNTO(D2>10;15;D2>=3;8;VERDADERO;3)`<br> |
| **Q** | `Coste_Total` | `=E2*P2`<br> |
| **R** | `Codigo_Seguimiento` | `=H2&"-"&M2&"-"&I2`<br> |

---

## 6. Preguntas de Reflexión para el Alumnado

1. **¿Por qué la extracción con `EXTRAE` requiere la función `VALOR` si queremos sumar o comparar el número de operación?**

2. **¿Qué sucede si intentas aplicar la función `SUMA` sobre un rango de celdas obtenidas mediante `EXTRAE` directamente?**

3. **¿Cuál es la diferencia entre cambiar el formato de celda a "00000" desde el menú de Excel versus utilizar la función `=TEXTO(celda; "00000")`?** *(Pista: piensa en qué ocurre cuando concatenas la celda con otros textos)*.


---

# 3. Segunda fase: normalización de nombres

### Paso 2 — Normalizar la delegación

Añade una columna llamada:

`Delegacion_Normalizada`

En `G2`, escribe:

```excel
=NOMPROPIO(ESPACIOS(B2))
```

Copia la fórmula hacia abajo.

Comprueba que valores como:

```text
BARCELONA
barcelona
 Barcelona 
```

quedan representados de forma homogénea como:

```text
Barcelona
```

---

# 4. Tercera fase: extraer información de un código

Los códigos normalizados tienen esta estructura:

```text
BCN-7741-EXP
```

La empresa necesita obtener por separado:

* Código de delegación.
* Número de operación.
* Tipo de envío.

Añade tres nuevas columnas:

* `Codigo_Delegacion`
* `Numero_Operacion`
* `Tipo_Envio`

---

## Paso 3 — Extraer la delegación

En `H2` utiliza:

```excel
=IZQUIERDA(F2;3)
```

Copia hacia abajo.

El resultado para:

```text
BCN-7741-EXP
```

será:

```text
BCN
```

---

## Paso 4 — Extraer el tipo de envío

En `J2` utiliza:

```excel
=DERECHA(F2;3)
```

Copia hacia abajo.

Obtendrás valores como:

```text
EXP
STD
```

---

## Paso 5 — Extraer el número de operación

El número de operación ocupa cuatro caracteres en la posición central del código.

En `I2` utiliza:

```excel
=EXTRAE(F2;5;4)
```

Copia hacia abajo.

Por ejemplo:

```text
BCN-7741-EXP
```

produce:

```text
7741
```

### Comprobación

Observa que las tres funciones permiten desmontar el código original:

```text
BCN-7741-EXP
│   │    │
│   │    └── DERECHA
│   └─────── EXTRAE
└─────────── IZQUIERDA
```

---

# 5. Cuarta fase: construir información nueva

La empresa necesita crear una descripción legible de cada envío.

Añade una columna:

`Descripcion_Envio`

Debe tener un resultado similar a:

```text
BCN - Barcelona - Teclado Mecánico
```

En `K2`, utiliza una fórmula que combine:

* `Codigo_Delegacion`
* `Delegacion_Normalizada`
* `Producto`

Puedes utilizar el operador `&`:

```excel
=H2&" - "&G2&" - "&NOMPROPIO(C2)
```

Copia hacia abajo.

### Objetivo

Comprueba que la fórmula permite construir automáticamente una descripción profesional a partir de varias columnas.

---

# 6. Quinta fase: clasificación mediante SI.CONJUNTO

Ahora la empresa necesita determinar la tarifa del envío según su peso.

Las reglas de negocio son:

| Peso del paquete | Categoría | Tarifa |
| ---------------: | --------- | -----: |
|     Más de 10 kg | Pesada    |   15 € |
|  Entre 3 y 10 kg | Media     |    8 € |
|    Menos de 3 kg | Ligera    |    3 € |

Añade dos columnas:

* `Categoria_Envio`
* `Tarifa_Envio`

---

## Paso 6 — Clasificar el envío

En `L2`, escribe:

```excel
=SI.CONJUNTO(D2>10;"Pesada";D2>=3;"Media";VERDADERO;"Ligera")
```

Copia hacia abajo.

### Analiza el orden de las condiciones

La fórmula comprueba las condiciones de izquierda a derecha:

```text
¿Peso > 10?
     │
   Sí ──► Pesada
     │
    No
     ↓
¿Peso >= 3?
     │
   Sí ──► Media
     │
    No
     ↓
   Ligera
```

### Importante

El orden de las condiciones es fundamental.

Por ejemplo, si se comprobara primero:

```excel
=D2>=3
```

un paquete de 15 kg cumpliría esa condición y se clasificaría como `Media`, aunque debería ser `Pesada`.

---

# 7. Sexta fase: asignar la tarifa

En `M2`, utiliza nuevamente `SI.CONJUNTO`:

```excel
=SI.CONJUNTO(D2>10;15;D2>=3;8;VERDADERO;3)
```

Copia hacia abajo.

Comprueba que:

* Un paquete de 14,5 kg obtiene 15 €.
* Un paquete de 7,8 kg obtiene 8 €.
* Un paquete de 2,1 kg obtiene 3 €.

Aplica formato de moneda a la columna `Tarifa_Envio`.

---

# 8. Séptima fase: calcular el coste total

La empresa necesita conocer el coste total de envío teniendo en cuenta el número de unidades.

Añade una columna:

`Coste_Total`

En `N2` escribe:

```excel
=E2*M2
```

Copia hacia abajo.

Aplica formato:

```text
#.##0,00 €
```

---

# 9. Octava fase: utilizar una fórmula anidada

Ahora vamos a combinar varias funciones.

La empresa quiere generar un identificador de seguimiento con este formato:

```text
BCN-7741-EXP
```

pero utilizando únicamente las partes extraídas del código.

En una nueva columna llamada:

`Codigo_Seguimiento`

utiliza:

```excel
=H2&"-"&I2&"-"&J2
```

Compara el resultado con `Codigo_Normalizado`.

### Pregunta

¿El resultado coincide exactamente con el código original normalizado?

Si no coincide en alguna fila, investiga qué dato puede estar provocando la diferencia.

---

# 10. Novena fase: aplicar todo el proceso a una nueva entrada

Para comprobar que las fórmulas son realmente reutilizables, añade manualmente una nueva fila al final de los datos.

Introduce:

```text
  mad-9955-exp 	MADRID	terminal portátil	12,8	3
```

Comprueba que puedes obtener:

* Código normalizado.
* Delegación normalizada.
* Código de delegación.
* Número de operación.
* Tipo de envío.
* Descripción del envío.
* Categoría.
* Tarifa.
* Coste total.
* Código de seguimiento.

---

# 11. Resultado final esperado

Al terminar la práctica, tu hoja deberá contener el listado original y las columnas calculadas:

| Columna | Contenido              |
| ------- | ---------------------- |
| A       | Codigo_Entrada         |
| B       | Delegacion             |
| C       | Producto               |
| D       | Peso_kg                |
| E       | Unidades               |
| F       | Codigo_Normalizado     |
| G       | Delegacion_Normalizada |
| H       | Codigo_Delegacion      |
| I       | Numero_Operacion       |
| J       | Tipo_Envio             |
| K       | Descripcion_Envio      |
| L       | Categoria_Envio        |
| M       | Tarifa_Envio           |
| N       | Coste_Total            |
| O       | Codigo_Seguimiento     |

---

# 12. Qué conceptos hemos practicado

Durante esta práctica has utilizado de forma integrada los principales contenidos del tema:

* `ESPACIOS` para limpiar datos.
* `MAYUSC` para normalizar códigos.
* `NOMPROPIO` para normalizar nombres.
* `IZQUIERDA` para extraer información.
* `DERECHA` para extraer información.
* `EXTRAE` para obtener una parte intermedia de un código.
* Operador `&` para concatenar textos.
* `SI.CONJUNTO` para implementar reglas de negocio.
* Orden de evaluación de condiciones.
* Fórmulas anidadas.
* Referencias a otras celdas.
* Formato de moneda.

---

## 13. Preguntas para comentar durante la práctica

No respondas necesariamente por escrito. Utiliza estas preguntas para razonar junto con el docente:

1. ¿Por qué `ESPACIOS` debe aplicarse antes de realizar determinadas comparaciones de texto?

2. ¿Qué diferencia existe entre `MAYUSC` y `NOMPROPIO`?

3. ¿Cuándo utilizarías `IZQUIERDA` y cuándo `DERECHA`?

4. ¿Por qué necesitamos `EXTRAE` para obtener el número de operación?

5. ¿Qué ocurriría si cambiamos el orden de las condiciones de `SI.CONJUNTO`?

6. ¿Para qué sirve `VERDADERO` como última condición de `SI.CONJUNTO`?

7. ¿Qué ventaja tiene construir `Codigo_Seguimiento` a partir de las partes extraídas en lugar de escribirlo manualmente?

---

## 14. Mini-reto final

Modifica las reglas de clasificación para crear una nueva columna llamada `Nivel_Prioridad`.

Utiliza estas reglas:

| Condición             | Prioridad |
| --------------------- | --------- |
| Peso superior a 15 kg | URGENTE   |
| Entre 8 y 15 kg       | ALTA      |
| Entre 3 y 8 kg        | MEDIA     |
| Menos de 3 kg         | BAJA      |

Utiliza `SI.CONJUNTO`.

Después, pide a un asistente de IA que genere una fórmula equivalente y compara ambas soluciones.

**Objetivo:** no se trata únicamente de conseguir una fórmula que funcione, sino de comprobar si entiendes la lógica que hay detrás de ella.
