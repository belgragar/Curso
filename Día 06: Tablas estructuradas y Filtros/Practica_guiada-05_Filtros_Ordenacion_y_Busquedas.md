# Práctica Guiada: Sistema Integral de Análisis y Búsquedas con Comodines

¡Hola! Excelente propuesta. Como tutor de Excel, he diseñado una práctica completa con una **empresa y datos totalmente nuevos**, estructurada en **6 pestañas/hojas independientes de Excel**.

Esta práctica incluye el trabajo con **búsquedas con comodines (`*`, `?`)** y respeta al 100% la **configuración regional de España** (coma `,` para decimales y punto y coma `;` para separar argumentos y columnas en datos).

---

## Estructura del Libro de Trabajo (6 Hojas Independientes)

* **Hoja 1:** `1_Rangos_y_Autofiltros`
* **Hoja 2:** `2_Tablas_Estructuradas`
* **Hoja 3:** `3_Tablas_Dinamicas`
* **Hoja 4:** `4_Funciones_BD`
* **Hoja 5:** `5_Matrices_y_Comodines`
* **Hoja 6:** `6_Segmentadores`

---

## Conjuntos de Datos de Origen

### Dataset Base (Para Hojas 1, 2, 4 y 6)

*Empresa: **Iberia Tech Solutions S.L.***
*Copia el siguiente bloque y pégalo a partir de la celda **A1** en las hojas 1, 2, 4 y 6:*

```csv
ID_Factura;Fecha;Comercial;Cliente;Importe;Unidades;Estado
FAC-1001;02/11/2026;Marta Gómez;IberCorp Norte;1450,50;10;Pagado
FAC-1002;05/11/2026;Carlos Ruiz;DataSur S.L.;820,00;4;Pendiente
FAC-1003;07/11/2026;Marta Gómez;IberCorp Centro;2300,00;15;Pagado
FAC-1004;10/11/2026;Pedro López;LogisTech España;450,00;25;Anulado
FAC-1005;12/11/2026;Laura Martín;IberCorp Norte;3100,00;8;Pagado
FAC-1006;15/11/2026;Carlos Ruiz;InnovaLab Sur;1250,00;12;Pendiente
FAC-1007;18/11/2026;Marta Gómez;LogisTech Centro;950,00;20;Pagado
FAC-1008;20/11/2026;Pedro López;DataSur Norte;180,00;50;Anulado
FAC-1009;22/11/2026;Laura Martín;InnovaLab Norte;2750,00;6;Pagado
FAC-1010;25/11/2026;Carlos Ruiz;IberCorp Sur;1900,00;9;Pendiente

```

### Dataset Ampliado (Para Hojas 3 y 5)

*Copia el siguiente bloque y pégalo a partir de la celda **A1** en las hojas 3 y 5:*

```csv
ID_Factura;Fecha;Comercial;Cliente;Importe;Unidades;Estado
FAC-2001;01/10/2026;Marta Gómez;IberCorp Norte;12500,00;45;Pagado
FAC-2002;03/10/2026;Carlos Ruiz;DataSur S.L.;4800,00;12;Pendiente
FAC-2003;05/10/2026;Laura Martín;LogisTech España;22000,00;300;Pagado
FAC-2004;07/10/2026;Pedro López;RetailSur S.A.;8300,00;8;Anulado
FAC-2005;10/10/2026;Marta Gómez;InnovaLab Norte;15100,00;5;Pagado
FAC-2006;12/10/2026;Carlos Ruiz;IberCorp Norte;18200,00;90;Pagado
FAC-2007;15/10/2026;Laura Martín;DataSur S.L.;3400,00;15;Pendiente
FAC-2008;18/10/2026;Pedro López;LogisTech Centro;9100,00;500;Pagado
FAC-2009;22/10/2026;Marta Gómez;RetailSur Norte;11200,00;210;Anulado
FAC-2010;25/10/2026;Carlos Ruiz;InnovaLab Sur;6500,00;30;Pagado

```

---

# GUÍA Y TAREAS PASO A PASO POR HOJA

---

## HOJA 1: Operaciones en Rangos y Autofiltros (`1_Rangos_y_Autofiltros`)

### 1. Contexto de Negocio

El departamento de administración necesita clasificar las facturas según su estado mediante alertas de color, aplicar filtros avanzados numéricos y de fechas, y ordenar las facturas priorizando el riesgo comercial.

### 2. Tareas a Resolver

1. **Formato Condicional:** Aplica reglas para resaltar la columna `Estado`:
* Rojo claro con texto rojo oscuro para `"Anulado"`.
* Amarillo claro para `"Pendiente"`.
* Verde claro para `"Pagado"`.


2. **Ordenación Multinivel:**
* **Nivel 1:** Ordena por **Color de celda** en la columna `Estado` (poniendo el relleno rojo arriba).
* **Nivel 2:** Ordena por `Importe` de mayor a menor.


3. **Filtro Avanzado de Texto:** Filtra la columna `Cliente` para ver únicamente las empresas que **contengan** la palabra `"IberCorp"`.
4. **Filtro de Número con Regla de Promedio:** Filtra la columna `Importe` mostrando solo los registros cuyos valores sean **Superiores al promedio**.
5. **Filtro de Fechas:** Filtra la columna `Fecha` para ver facturas emitidas **entre el `05/11/2026` y el `18/11/2026**`.

### 3. Guía de Solución Paso a Paso

1. **Formato Condicional:**
* Selecciona `G2:G11`.
* Ve a **Inicio** > **Formato condicional** > **Reglas para resaltar celdas** > **Es igual a...**
* Aplica `"Anulado"` (Rojo), `"Pendiente"` (Amarillo) y `"Pagado"` (Verde).


2. **Ordenación Multinivel por Color y Valor:**
* Selecciona el rango `A1:G11`.
* Ve a **Datos** > **Ordenar**.
* **Nivel 1:** Columna `Estado` | Ordenar según: **Color de celda** | Criterio: Relleno rojo | En la parte: Arriba.
* Haz clic en **Agregar nivel**.
* **Nivel 2:** Columna `Importe` | Ordenar según: **Valores de celda** | Criterio: **De mayor a menor**. Haz clic en **Aceptar**.


3. **Autofiltros Especiales:**
* Ve a **Datos** > **Filtro**.
* **Filtro de Texto:** En `Cliente` > **Filtros de texto** > **Contiene...** > Escribe `IberCorp`.
* **Filtro de Número:** Borra el filtro previo. En `Importe` > **Filtros de número** > **Superior al promedio**.
* **Filtro de Fecha:** En `Fecha` > **Filtros de fecha** > **Entre...** > Introduce `05/11/2026` y `18/11/2026`.



---

## HOJA 2: Tablas Estructuradas (`2_Tablas_Estructuradas`)

### 1. Contexto de Negocio

Se requiere convertir los datos planos en una Tabla de Excel para automatizar la gestión de totales y ordenar a los comerciales según la estructura directiva corporativa.

### 2. Tareas a Resolver

1. Convierte el rango `A1:G11` en una **Tabla Estructurada** de Excel.
2. Aplica un filtro numérico en `Unidades` utilizando la regla **10 mejores** (configurada para ver las 4 facturas de mayor volumen).
3. Aplica una **Lista Personalizada** para ordenar la columna `Comercial` con el siguiente orden exacto: **Laura Martín, Marta Gómez, Carlos Ruiz, Pedro López**.
4. Activa la **Fila de Totales** para calcular la suma de `Importe` y el valor promedio de `Unidades`.

### 3. Guía de Solución Paso a Paso

1. Selecciona cualquier celda y presiona **`Ctrl + T`**. Asegúrate de marcar *"La tabla tiene encabezados"* y acepta.


2. **Filtro 10 mejores:** En el desplegable de `Unidades` > **Filtros de número** > **Diez mejores...** > Cambia `10` por `4` elementos.
3. **Ordenación por Lista Personalizada:**
* Ve a **Datos** > **Ordenar**.
* En *Criterio de ordenación*, selecciona **Lista personalizada...**.
* En *Entradas de lista*, escribe las cuatro personas en líneas separadas:
```text
Laura Martín
Marta Gómez
Carlos Ruiz
Pedro López

```


* Haz clic en **Agregar** y acepta.


4. **Fila de Totales:** En la pestaña **Diseño de tabla**, marca **Fila de totales**. En la fila inferior, selecciona `Suma` para `Importe` y `Promedio` para `Unidades`.



---

## HOJA 3: Tablas Dinámicas (`3_Tablas_Dinamicas`)

### 1. Contexto de Negocio

El equipo directivo necesita un resumen ejecutivo utilizando el dataset ampliado para analizar el volumen facturado por comercial y estado del cobro.

### 2. Tareas a Resolver

1. Crea una **Tabla Dinámica** a partir del dataset de la Hoja 3.
2. Estructura los campos:
* **Filas:** `Comercial`
* **Columnas:** `Estado`
* **Valores:** Suma de `Importe`


3. Aplica un **Filtro de Valor** para mostrar únicamente a los comerciales cuyas facturas totales superen los **`20.000,00 €`**.
4. Ordena la tabla dinámica de mayor a menor según el Total General de la facturación.

### 3. Guía de Solución Paso a Paso

1. Selecciona los datos ampliados en la Hoja 3 y ve a **Insertar** > **Tabla dinámica**.
2. En el panel de la derecha:
* Arrastra `Comercial` a **Filas**.
* Arrastra `Estado` a **Columnas**.
* Arrastra `Importe` a **Valores** (configurado como Suma).


3. **Filtro de Valor:** En el desplegable de *Etiquetas de fila* > **Filtros de valor** > **Mayor que...** > Introduce `20000`.
4. **Ordenación:** Haz clic derecho sobre cualquier celda del *Total general* > **Ordenar** > **Ordenar de mayor a menor**.

---

## HOJA 4: Rango de Criterios y Funciones de Base de Datos (`4_Funciones_BD`)

### 1. Contexto de Negocio

Auditoría requiere consultar la base de datos de facturación mediante criterios complejos combinados (condiciones lógicas Y / O) sin alterar la tabla principal.

### 2. Tareas a Resolver

1. Diseña un **Rango de Criterios** en `I1:K3` que evalúe:
* Facturas con `Estado` = **"Pagado"** e `Importe` mayor a **`2.000,00`**.
* **O** cualquier factura gestionada por el `Comercial` **"Pedro López"**.


2. Calcula el número de facturas que cumplen la condición con `=BDCONTAR()`.
3. Calcula el importe total de dichas facturas con `=BDSUMA()`.

### 3. Guía de Solución Paso a Paso

1. **Configurar Rango de Criterios (`I1:K3`):**
* `I1`: `Estado` | `J1`: `Importe` | `K1`: `Comercial`
* `I2`: `Pagado` | `J2`: `>2000` | `K2`: *(en blanco)*
* `I3`: *(en blanco)* | `J3`: *(en blanco)* | `K3`: `Pedro López`


2. **Fórmulas de Base de Datos:**
* En la celda `I6` (para contar):
```excel
=BDCONTAR(A1:G11; "ID_Factura"; I1:K3)

```


* En la celda `I7` (para sumar):
```excel
=BDSUMA(A1:G11; "Importe"; I1:K3)

```





---

## HOJA 5: Matrices Dinámicas y Búsquedas con Comodines (`5_Matrices_y_Comodines`)

### 1. Contexto de Negocio

En esta hoja combinaremos las **matrices dinámicas** con el poder de los **caracteres comodín (`*` y `?`)** para extraer y consultar información con búsquedas parciales e inteligentes.

> **Recordatorio de Comodines:**
> * `*` (Asterisco): Representa cualquier secuencia de caracteres (ej. `"Iber*"` encuentra `"IberCorp Norte"` e `"IberCorp Centro"`).
> 
> 
> * `?` (Signo de interrogación): Representa un único carácter individual (ej. `"FAC-200?"` encuentra de `"FAC-2001"` a `"FAC-2009"`).
> 
> 
> 
> 

### 2. Tareas a Resolver

1. **Filtrado Avanzado con Matrices Dinámicas:** Utiliza `=FILTRAR()` y `=ORDENAR()` en `I2` para extraer las facturas pertenecientes a clientes que empiecen por `"IberCorp"` cuya suma de `Unidades` sea superior a `10`, ordenando la matriz por `Importe` de forma descendente.
2. **Búsqueda con Comodines usando `BUSCARX`:**
* Configura una celda de consulta en `I14` donde el usuario escriba un nombre de cliente parcial con comodines (ejemplo: `"*Tech*"`).
* En `J14`, utiliza `=BUSCARX()` configurado con el **`modo_coincidencia = 2`** (caracteres comodín) para recuperar el `Importe` de la factura.




3. **Búsqueda con Comodines usando `HALLAR` y `SI.ERROR`:**
* En `K14`, realiza una búsqueda que determine si el cliente en `I14` contiene la palabra `"Norte"`. Si la contiene, debe devolver `"Zona Norte"`; si no, `"Otra Zona"`.





### 3. Guía de Solución Paso a Paso

1. **Matriz Dinámica con `FILTRAR` y `ORDENAR`:**
Escribe en la celda `I2`:
```excel
=ORDENAR(FILTRAR(A2:G11; (ESNUMERO(HALLAR("IberCorp"; D2:D11))) * (F2:F11>10); "Sin resultados"); 5; -1)

```


*Explicación:* `HALLAR("IberCorp"; D2:D11)` busca el texto en la columna de clientes. La multiplicación (`*`) aplica la condición lógica **Y**, y `ORDENAR( ... ; 5; -1)` ordena los resultados por la columna 5 (`Importe`) descendentemente.


2. **Búsqueda con Comodines (`BUSCARX` con `modo_coincidencia = 2`):**
* Escribe en `I14`: `*Tech*`

* Escribe en `J14`:
```excel
=BUSCARX(I14; D2:D11; E2:E11; "Cliente no encontrado"; 2)

```




*Explicación:* El quinto argumento de `BUSCARX` fijado en `2` activa la coincidencia por caracteres comodín, permitiendo encontrar `"LogisTech España"` o `"LogisTech Centro"`.


3. **Búsqueda Parcial con `HALLAR` + `SI.ERROR`:**
Escribe en `K14`:
```excel
=SI.ERROR(SI(HALLAR("Norte"; I14)>0; "Zona Norte"); "Otra Zona")

```


*Explicación:* `HALLAR` devuelve la posición del texto sin diferenciar mayúsculas/minúsculas. Si no encuentra la palabra, genera error, el cual es capturado por `SI.ERROR`.



---

## HOJA 6: Segmentadores de Datos (`6_Segmentadores`)

### 1. Contexto de Negocio

Para el cuadro de mando de la dirección, crearemos una interfaz interactiva con botones visuales que permitan filtrar en tiempo real por comercial y estado del cobro.

### 2. Tareas a Resolver

1. Convierte la tabla de la Hoja 6 en **Tabla Estructurada**.
2. Inserta dos **Segmentadores de Datos (Slicers)**: uno para `Comercial` y otro para `Estado`.
3. Ajusta el segmentador de `Comercial` a **4 columnas** para disponer sus botones de forma horizontal en la cabecera.
4. Interactúa con los botones para filtrar los datos.

### 3. Guía de Solución Paso a Paso

1. Selecciona los datos y presiona **`Ctrl + T`**.
2. Ve a la pestaña **Diseño de tabla** > **Insertar segmentación de datos**.
3. Selecciona **Comercial** y **Estado**, y haz clic en **Aceptar**.
4. **Formato del Segmentador:**
* Haz clic sobre el panel del segmentador `Comercial`.
* En la pestaña emergente **Segmentación**, cambia el valor de **Columnas** a `4`.
* Ajusta el tamaño del panel estirándolo horizontalmente y colócalo arriba de la tabla.



---

¿Qué te parece este nuevo planteamiento? Quedo a tu disposición para resolver cualquier duda sobre las fórmulas, validar las soluciones o profundizar en la teoría de las búsquedas avanzadas.
