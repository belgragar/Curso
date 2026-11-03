# Ejercicio 25: Funciones de cadenas de texto

El ejercicio integra **todas las funciones tradicionales de cadenas de texto** presentes en la imagen original de tu referencia (`ESPACIOS`, `MAYUSC`, `MINUSC`, `NOMPROPIO`, `IZQUIERDA`, `DERECHA`, `EXTRAE`, `&`, `CONCAT`, `UNIRCADENAS`, `HALLAR`, `ENCONTRAR`, `SUSTITUIR`, `REEMPLAZAR`, `LARGO`, `VALOR`, `TEXTO`, `SI`, `SI.CONJUNTO`) y añade las **nuevas funciones de matriz dinámica de Microsoft 365** (`TEXTOANTES`, `TEXTODESPUES` y `DIVIDIRTEXTO`).

Todo está configurado según la normativa regional de España (separador de argumentos por punto y coma `;` y decimales por coma `,`).

---

## 1. Contexto de Negocio

Eres el responsable de auditoría y análisis de operaciones de la asociación de atracciones del **Parque de Atracciones "Feria Mágica"**. Tras el fin de semana de mayor afluencia, has recibido la base de datos de control de acceso, mantenimiento de atracciones y ventas de tickets.

Los datos proceden de terminales de punto de venta (TPV) antiguos y dispositivos portátiles de lectura de códigos de barras. Debido a esto, presentan inconsistencias graves: nombres de visitantes o atracciones con espacios sobrantes, combinaciones desordenadas de mayúsculas y minúsculas, códigos de registro internos en los que están anidados la ciudad, la atracción y el sector, e importes de recaudación en formato de texto. Tu objetivo es limpiar, transformar, unir y estructurar esta información para generar un informe operativo oficial para la dirección del parque.

---

## 2. Conjunto de Datos (Dataset)

Para comenzar, crea una hoja limpia en Excel y asigna el nombre **Control_Feria**. Copia el siguiente bloque delimitado por punto y coma (`;`) y pégalo directamente desde la celda **A1**:

```csv
ID_TICKET_BRUTO;EMPLEADO_NOMBRES;REGISTRO_CRUDO;CODIGO_INSPECCION;RECAUDACION_TEXTO;INCIDENCIA_COD
  FER-101/MAD  ;  gÓmez lÓpez, ana  ;SEV/60321/Montaña Rusa/A;900-8452-X;1250,50;INC-3
  FER-102/BCN  ; martín ruiz, Carlos ;MAD/20149/Coches de Choque/A;800-3911-Y;2410,11;INC-1
  FER-103/SEV  ;MUÑIZ gómez, laura  ;SEV/80932/Noria Gigante/C;900-5520-Z;850,78;INC-5
  FER-104/MAD  ;Iópez Martín, pedro ;MAD/20150/Coches de Choque/B;750-1049-W;3100,00;INC-2
  FER-105/VAL  ;  martín ruiz, carlos;VAL/40211/Casa del Terror/A;900-9988-V;1950,80;INC-0

```

---

## 3. Tareas a Resolver

### Bloque 1: Limpieza Básica y Normalización de Caja

* **Tarea 1.1 (`ESPACIOS` y `NOMPROPIO` anidados):** En la columna G (`Empleado_Limpio`), limpia los espacios al inicio/final/dobles del `EMPLEADO_NOMBRES` y aplica formato de nombre propio.
* **Tarea 1.2 (`MAYUSC`):** En la columna H (`ID_Mayusculas`), limpia y convierte el `ID_TICKET_BRUTO` a mayúsculas puras.
* **Tarea 1.3 (`MINUSC`):** En la columna I (`Sector_Minusculas`), extrae el último carácter del `REGISTRO_CRUDO` y conviértelo a minúsculas.

### Bloque 2: Extracción Posicional y Medición de Cadenas

* **Tarea 2.1 (`IZQUIERDA`):** En la columna J (`Origen_Ciudad`), extrae los primeros 3 caracteres del `REGISTRO_CRUDO`.
* **Tarea 2.2 (`DERECHA`):** En la columna K (`Sede_Ticket`), extrae los 3 caracteres situados más a la derecha del `ID_TICKET_BRUTO`.
* **Tarea 2.3 (`EXTRAE` y `HALLAR`):** En la columna L (`Num_Licencia`), extrae el número de 5 dígitos situado justo después de la primera barra `/` en el `REGISTRO_CRUDO`.
* **Tarea 2.4 (`ENCONTRAR` y `LARGO`):** En la columna M (`Posicion_Barra`), busca la posición exacta de la primera barra `/` en el `REGISTRO_CRUDO` sensible a mayúsculas. En la columna N (`Longitud_Código`), calcula la cantidad total de caracteres de `REGISTRO_CRUDO`.

### Bloque 3: Modificación y Sustitución de Textos

* **Tarea 3.1 (`SUSTITUIR`):** En la columna O (`Registro_Guiones`), sustituye todas las barras inclinadas `/` del `REGISTRO_CRUDO` por un guion medio `-`.
* **Tarea 3.2 (`REEMPLAZAR`):** En la columna P (`Codigo_Securizado`), reemplaza los primeros 3 caracteres del `CODIGO_INSPECCION` por la sigla de control `"SEC"`.

### Bloque 4: Conversión Numérica y Métodos de Concatención

* **Tarea 4.1 (`VALOR`):** En la columna Q (`Recaudacion_Num`), convierte el campo de texto `RECAUDACION_TEXTO` en un valor numérico real.
* **Tarea 4.2 (`&` y `TEXTO`):** En la columna R (`Resumen_Recaudacion`), une el `Empleado_Limpio` con su recaudación formateada en formato de moneda (`#,##0,00 €`).
* **Tarea 4.3 (`CONCAT`):** En la columna S (`Etiqueta_Rapida`), une el `ID_Mayusculas` con la `Origen_Ciudad` separados por un espacio.
* **Tarea 4.4 (`UNIRCADENAS`):** En la columna T (`Ficha_Tecnica`), une el `ID_Mayusculas`, `Empleado_Limpio` y `Registro_Guiones` utilizando como delimitador una barra espaciada `" | "` y omitiendo celdas vacías.

### Bloque 5: Lógica de Negocio y Funciones de Vanguardia Microsoft 365

* **Tarea 5.1 (`SI` y `SI.CONJUNTO`):**
* En la columna U (`Supera_Objetivo`), evalúa con la función `SI` si la `Recaudacion_Num` es mayor a `1.500,00 €` (Devuelve `"Objetivo Cumplido"` o `"Pendiente"`).
* En la columna V (`Nivel_Afluencia`), utiliza `SI.CONJUNTO` sobre `Recaudacion_Num`: Si es $> 2.000$, `"Alta Afluencia"`; si es $\ge 1.000$, `"Afluencia Media"`; de lo contrario, `"Baja Afluencia"`.


* **Tarea 5.2 (Novedad M365 - `TEXTOANTES` y `TEXTODESPUES`):**
* En la columna W (`Prefijo_Insp`), extrae el bloque de texto previo al primer guion del `CODIGO_INSPECCION`.
* En la columna X (`Letra_Control_Insp`), extrae el carácter posterior al último guion del `CODIGO_INSPECCION`.


* **Tarea 5.3 (Novedad M365 - `DIVIDIRTEXTO`):**
* En la celda **Y2**, utiliza `DIVIDIRTEXTO` para desbordar horizontalmente el `REGISTRO_CRUDO` de la atracción en 4 columnas independientes (Ciudad, Licencia, Atracción, Sector).



---

## 4. Guía de Solución Paso a Paso

Introduce las siguientes fórmulas en la **fila 2** de las columnas correspondientes y arrástralas hacia abajo hasta la fila 6:

### Bloque 1

* **Columna G (`Empleado_Limpio`):**
`=ESPACIOS(NOMPROPIO(B2))`
* *Explicación:* `NOMPROPIO` corrige las mayúsculas/minúsculas desordenadas (ej. "gÓmez lÓpez, ana" $\rightarrow$ "Gómez López, Ana") y `ESPACIOS` elimina las tabulaciones o espacios residuales.


* **Columna H (`ID_Mayusculas`):**
`=MAYUSC(ESPACIOS(A2))`
* **Columna I (`Sector_Minusculas`):**
`=MINUSC(DERECHA(C2; 1))`
* *Explicación:* Extrae la letra del sector al final de la cadena ("A", "B", "C") y la convierte a minúscula ("a", "b", "c").



### Bloque 2

* **Columna J (`Origen_Ciudad`):**
`=IZQUIERDA(C2; 3)`
* **Columna K (`Sede_Ticket`):**
`=DERECHA(A2; 3)`
* **Columna L (`Num_Licencia`):**
`=EXTRAE(C2; HALLAR("/"; C2) + 1; 5)`
* *Explicación:* `HALLAR` encuentra la primera posición de la barra `/`. Le sumamos `1` para situarnos en el primer dígito y `EXTRAE` toma exactamente 5 caracteres.


* **Columna M (`Posicion_Barra`):**
`=ENCONTRAR("/"; C2)`
* **Columna N (`Longitud_Código`):**
`=LARGO(C2)`

### Bloque 3

* **Columna O (`Registro_Guiones`):**
`=SUSTITUIR(C2; "/"; "-")`
* **Columna P (`Codigo_Securizado`):**
`=REEMPLAZAR(D2; 1; 3; "SEC")`
* *Explicación:* Reemplaza desde la posición 1 los primeros 3 caracteres del código ("900", "800", etc.) por la palabra `"SEC"`.



### Bloque 4

* **Columna Q (`Recaudacion_Num`):**
`=VALOR(E2)`
* *Explicación:* Convierte el texto numérico en una cifra real calculable por Excel.


* **Columna R (`Resumen_Recaudacion`):**
`="Encargado: " & G2 & " | Recaudado: " & TEXTO(Q2; "#.##0,00 €")`
* *Explicación:* El operador `&` concatena y `TEXTO` asigna el formato visual con el separador de miles en punto (`.`), el decimal en coma (`,`) y el símbolo de la moneda.


* **Columna S (`Etiqueta_Rapida`):**
`=CONCAT(H2; " - "; J2)`
* **Columna T (`Ficha_Tecnica`):**
`=UNIRCADENAS(" | "; VERDADERO; H2; G2; O2)`
* *Explicación:* Une múltiples rangos o celdas mediante el delimitador especificado e ignora las celdas vacías según el parámetro `VERDADERO`.



### Bloque 5

* **Columna U (`Supera_Objetivo`):**
`=SI(Q2 > 1500; "Objetivo Cumplido"; "Pendiente")`
* **Columna V (`Nivel_Afluencia`):**
`=SI.CONJUNTO(Q2 > 2000; "Alta Afluencia"; Q2 >= 1000; "Afluencia Media"; VERDADERO; "Baja Afluencia")`
* *Explicación:* Evalúa las condiciones en orden jerárquico descendente. La condición `VERDADERO` final actúa como caso por defecto.


* **Columna W (`Prefijo_Insp` - M365):**
`=TEXTOANTES(D2; "-")`
* **Columna X (`Letra_Control_Insp` - M365):**
`=TEXTODESPUES(D2; "-"; -1)`
* *Explicación:* El argumento `-1` le indica a `TEXTODESPUES` que busque partiendo desde la derecha, aislando la última letra tras el segundo guion.


* **Columna Y (`Separación Dinámica` - M365):**
Escribe en la celda **Y2**:
`=DIVIDIRTEXTO(C2; "/")`
* *Explicación:* Esta función de matriz dinámica no necesita ser copiada a las celdas contiguas; automáticamente "desbordará" horizontalmente en `Y2`, `Z2`, `AA2` y `AB2` separando el contenido de la atracción de feria en sus componentes.

