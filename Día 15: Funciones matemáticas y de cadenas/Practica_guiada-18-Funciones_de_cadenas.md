# Práctica guiada 18: Funciones de cadenas de texto

## 1. Contexto de Negocio

Como analista de operaciones en una multinacional de servicios con sede en Madrid, se te ha encargado consolidar y depurar la base de datos de recursos humanos y logística. Los registros provienen de diferentes delegaciones y contienen errores de espaciado, formatos mixtos de mayúsculas y minúsculas, códigos internos anidados y cadenas crudas que necesitan ser procesadas mediante fórmulas de texto avanzadas y las nuevas capacidades dinámicas de Microsoft 365 para un informe ejecutivo impecable.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente contenido delimitado por punto y coma (`;`) y pégalo directamente en la celda **A1** de tu hoja de Excel en blanco:

```csv
ID_Empleado;Nombre_Bruto;Registro_Crudo;Codigo_Tributo;Horas_Trabajadas
  EMP-101/MAD  ;  gÓmez lÓpez, ana  ;OVD/60321/Soporte/B;900-8452-X;38,42
  EMP-102/BCN  ; martín ruiz, Carlos ;MAD/20149/Ventas/A;800-3911-Y;40,11
  EMP-103/SEV  ;MUÑIZ gómez, laura  ;SEV/80932/Logistica/C;900-5520-Z;35,78
  EMP-104/MAD  ;Iópez Martín, pedro ;MAD/20150/Ventas/B;750-1049-W;41,50
  EMP-105/VLC  ;  martín ruiz, carlos;VAL/40211/Soporte/A;900-9988-V;39,80

```

---

## 3. Tareas a Resolver

1. **Limpieza y Normalización Básica (`ESPACIOS`, `MAYUSC`, `MINUSC`, `NOMPROPIO`, `ESPACIOS(NOMPROPIO())`):**
* **Tarea 1.1:** En la columna F (`Nombre_Limpio`), limpia los espacios redundantes y aplica el formato de nombre propio al `Nombre_Bruto` usando la combinación anidada vista en clase.


* **Tarea 1.2:** En la columna G (`ID_Mayusc`), convierte el `ID_Empleado` a mayúsculas puras eliminando espacios. En la columna H (`Inicial_Minusc`), extrae el último carácter del `Registro_Crudo` en minúsculas.




2. **Extracción y Posicionamiento de Cadenas (`IZQUIERDA`, `DERECHA`, `EXTRAE`, `HALLAR`, `ENCONTRAR`, `LARGO`):**
* **Tarea 2.1:** En la columna I (`Ciudad_Origen`), extrae los primeros 3 caracteres del `Registro_Crudo` usando `IZQUIERDA`.


* **Tarea 2.2:** En la columna J (`Ultimos_Digitos`), extrae los últimos 3 caracteres del `ID_Empleado` utilizando `DERECHA`.


* **Tarea 2.3:** En la columna K (`Secuencia_Central`), utiliza `EXTRAE` combinada con `HALLAR` para aislar el número central de 5 dígitos del `Registro_Crudo`.


* **Tarea 2.4:** En la columna L (`Posicion_Barra`), busca la posición exacta de la barra `/` distinguiendo mayúsculas/minúsculas con `ENCONTRAR`, y en la columna M (`Longitud_Registro`), calcula la longitud total del `Registro_Crudo` con `LARGO`.




3. **Sustitución y Reemplazo (`SUSTITUIR`, `REEMPLAZAR`):**
* **Tarea 3.1:** En la columna N (`Registro_Modificado`), sustituye todas las ocurrencias de la barra `/` por un guion medio `-` usando `SUSTITUIR`.


* **Tarea 3.2:** En la columna O (`Codigo_Seguro`), reemplaza los primeros 3 caracteres del `Codigo_Tributo` por el texto `"SEC"` mediante `REEMPLAZAR`.




4. **Conversión Numérica y Métodos de Unión (`VALOR`, `TEXTO`, `&`, `CONCAT`, `UNIRCADENAS`):**
* **Tarea 4.1:** En la columna P (`Horas_Numericas`), convierte las horas de texto a número con `VALOR`.


* **Tarea 4.2:** En la columna Q (`Reporte_Concatenado`), une el nombre limpio y las horas formateadas a dos decimales con el operador `&` y la función `TEXTO`.


* **Tarea 4.3:** En la columna R (`Unido_Concat`), une el ID y el nombre usando la función `CONCAT`.


* **Tarea 4.4:** En la columna S (`Ficha_Completa`), une el ID, el nombre y el registro usando `UNIRCADENAS` con un separador de barra espaciada `" | "` y omitiendo celdas vacías.




5. **Lógica Avanzada y Nuevas Funciones Microsoft 365 (`SI`, `SI.CONJUNTO`, `TEXTOANTES`, `TEXTODESPUES`, `DIVIDIRTEXTO`):**
* **Tarea 5.1:** En la columna T (`Bono_Productividad`), evalúa con `SI` si las horas trabajadas son mayores a 40 para asignar `"Sí"` o `"No"`.
* **Tarea 5.2:** En la columna U (`Clasificacion_Jornada`), implementa `SI.CONJUNTO` para clasificar: $>40$ como `"Completa"`, $\ge38$ como `"Estándar"`, y el resto como `"Parcial"`.
* **Tarea 5.3 (M365):** En las columnas V y W (`Prefijo_Tributo` y `Sufijo_Tributo`), extrae la parte anterior y posterior al guion del `Codigo_Tributo` empleando `TEXTOANTES` y `TEXTODESPUES`.


* **Tarea 5.4 (M365):** En la celda auxiliar **X2**, aplica `DIVIDIRTEXTO` sobre el `Registro_Crudo` usando la barra `/` como delimitador de columna para desbordar los datos.





---

## 4. Guía de Solución Paso a Paso

* **Tarea 1.1 (`ESPACIOS` y `NOMPROPIO`):**
* Fórmula en `F2`: `=ESPACIOS(NOMPROPIO(B2))`
* *Explicación:* `ESPACIOS` elimina los espacios dobles y al margen, y `NOMPROPIO` normaliza la capitalización de los nombres.




* **Tarea 1.2 (`MAYUSC` y `MINUSC`):**
* Fórmula en `G2`: `=MAYUSC(ESPACIOS(A2))`


* Fórmula en `H2`: `=MINUSC(DERECHA(C2; 1))`




* **Tarea 2.1 y 2.2 (`IZQUIERDA` y `DERECHA`):**
* Fórmula en `I2`: `=IZQUIERDA(C2; 3)` *(Devuelve "OVD")*


* Fórmula en `J2`: `=DERECHA(A2; 3)` *(Devuelve "MAD")*




* **Tarea 2.3 y 2.4 (`EXTRAE`, `HALLAR`, `ENCONTRAR`, `LARGO`):**
* Fórmula en `K2`: `=EXTRAE(C2; HALLAR("/"; C2) + 1; 5)`


* Fórmula en `L2`: `=ENCONTRAR("/"; C2)` *(Localiza la posición exacta de la barra distinguiendo mayúsculas)*


* Fórmula en `M2`: `=LARGO(C2)`




* **Tarea 3.1 y 3.2 (`SUSTITUIR` y `REEMPLAZAR`):**
* Fórmula en `N2`: `=SUSTITUIR(C2; "/"; "-")`


* Fórmula en `O2`: `=REEMPLAZAR(D2; 1; 3; "SEC")`




* **Tarea 4.1, 4.2, 4.3 y 4.4 (`VALOR`, `TEXTO`, `&`, `CONCAT`, `UNIRCADENAS`):**
* Fórmula en `P2`: `=VALOR(E2)`


* Fórmula en `Q2`: `="Empleado: " & F2 & " - Horas: " & TEXTO(P2; "#,00")`


* Fórmula en `R2`: `=CONCAT(A2; " - "; F2)`


* Fórmula en `S2`: `=UNIRCADENAS(" | "; VERDADERO; A2; F2; C2)`




* **Tarea 5.1 y 5.2 (`SI` y `SI.CONJUNTO`):**
* Fórmula en `T2`: `=SI(P2 > 40; "Sí"; "No")`
* Fórmula en `U2`: `=SI.CONJUNTO(P2 > 40; "Completa"; P2 >= 38; "Estándar"; VERDADERO; "Parcial")`


* **Tarea 5.3 (`TEXTOANTES` y `TEXTODESPUES` - M365):**
* Fórmula en `V2`: `=TEXTOANTES(D2; "-")` *(Devuelve "900")*


* Fórmula en `W2`: `=TEXTODESPUES(D2; "-"; -1)` *(Devuelve "X" usando instancia negativa)*




* **Tarea 5.4 (`DIVIDIRTEXTO` - M365):**
* Fórmula en `X2`: `=DIVIDIRTEXTO(C2; "/")`


* *Explicación:* Al presionar Intro, la matriz se desbordará horizontalmente en las celdas contiguas (`X2:AA2`) separando la ciudad, el código, el área y la categoría de forma automática.

