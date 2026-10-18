# Práctica guiada: Normalización y clasificación de envíos

## Objetivo

En esta práctica vas a construir, paso a paso, una pequeña herramienta para gestionar los envíos de una empresa logística.

Partiremos de un listado de entradas recibido desde diferentes delegaciones. Los datos contienen algunos problemas habituales en archivos procedentes de otros sistemas:

* Códigos escritos en minúsculas.
* Espacios innecesarios al principio o al final.
* Nombres de delegaciones escritos con diferentes formatos.
* Códigos compuestos por varias partes.
* Pesos que determinarán automáticamente una tarifa de envío.
* Datos que posteriormente utilizaremos para construir códigos y descripciones normalizadas.

La práctica se realizará **a la vez que se explican los conceptos del tema**. No se trata de completar todos los pasos de una vez, sino de ir incorporando cada transformación conforme se estudie la función correspondiente.

---

## 1. Datos iniciales

Crea un libro nuevo, llama a la Hoja1 `Envios`.

Copia el siguiente bloque y pégalo directamente en la celda `A1`.

> **Importante:** el bloque utiliza tabulaciones entre columnas. No modifiques los datos antes de comenzar la práctica, ya que algunos espacios y diferencias de formato son intencionados.

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

# 2. Primera fase: limpieza y normalización

### Paso 1 — Limpiar el código de entrada

Añade una nueva columna llamada:

`Codigo_Normalizado`

En `F2`, utiliza:

```excel
=MAYUSC(ESPACIOS(A2))
```

Copia la fórmula hacia abajo.

### ¿Qué estamos consiguiendo?

La fórmula realiza dos operaciones:

1. `ESPACIOS(A2)` elimina los espacios innecesarios.
2. `MAYUSC(...)` convierte el código a mayúsculas.

Por ejemplo:

```text
  bcn-7741-exp 
```

se convierte en:

```text
BCN-7741-EXP
```

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
