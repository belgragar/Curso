# Ejercicio 14: Tablas dinámicas

Una empresa de distribución de material de oficina quiere analizar las operaciones realizadas por sus comerciales durante varios meses.

> **Instrucciones:** pulsa **Copy** en el bloque inferior y pega directamente los datos en la celda **A1** de una hoja nueva de Excel.

```tsv
ID_Operacion	Fecha	Comercial	Provincia	Canal	Familia_Producto	Tipo_Cliente	Importe
OP-1001	05/01/2026	Ana	Madrid	Tienda	Hardware	Empresa	1250,00
OP-1002	08/01/2026	Carlos	Barcelona	Online	Software	Profesional	890,00
OP-1003	12/01/2026	Marta	Valencia	Tienda	Consumibles	Empresa	425,00
OP-1004	15/01/2026	Javier	Madrid	Online	Hardware	Particular	1680,00
OP-1005	20/01/2026	Ana	Sevilla	Tienda	Software	Empresa	2150,00
OP-1006	24/01/2026	Carlos	Madrid	Online	Consumibles	Profesional	375,00
OP-1007	03/02/2026	Marta	Barcelona	Tienda	Hardware	Empresa	1320,00
OP-1008	07/02/2026	Javier	Valencia	Online	Software	Empresa	2450,00
OP-1009	11/02/2026	Ana	Madrid	Tienda	Consumibles	Particular	580,00
OP-1010	16/02/2026	Carlos	Sevilla	Online	Hardware	Empresa	1920,00
OP-1011	21/02/2026	Marta	Madrid	Tienda	Software	Profesional	760,00
OP-1012	26/02/2026	Javier	Barcelona	Online	Consumibles	Empresa	310,00
OP-1013	04/03/2026	Ana	Valencia	Tienda	Hardware	Empresa	1475,00
OP-1014	09/03/2026	Carlos	Madrid	Online	Software	Particular	980,00
OP-1015	14/03/2026	Marta	Sevilla	Tienda	Consumibles	Empresa	640,00
OP-1016	19/03/2026	Javier	Madrid	Online	Hardware	Profesional	2250,00
OP-1017	24/03/2026	Ana	Barcelona	Tienda	Software	Empresa	1890,00
OP-1018	29/03/2026	Carlos	Valencia	Online	Consumibles	Empresa	455,00
OP-1019	03/04/2026	Marta	Madrid	Tienda	Hardware	Particular	1180,00
OP-1020	08/04/2026	Javier	Sevilla	Online	Software	Empresa	2760,00
OP-1021	13/04/2026	Ana	Madrid	Tienda	Consumibles	Profesional	520,00
OP-1022	18/04/2026	Carlos	Barcelona	Online	Hardware	Empresa	1540,00
OP-1023	23/04/2026	Marta	Valencia	Tienda	Software	Empresa	920,00
OP-1024	28/04/2026	Javier	Madrid	Online	Consumibles	Particular	685,00
OP-1025	05/05/2026	Ana	Sevilla	Tienda	Hardware	Empresa	1725,00
OP-1026	10/05/2026	Carlos	Madrid	Online	Software	Profesional	1120,00
OP-1027	15/05/2026	Marta	Barcelona	Tienda	Consumibles	Empresa	395,00
OP-1028	20/05/2026	Javier	Valencia	Online	Hardware	Empresa	2380,00
OP-1029	25/05/2026	Ana	Madrid	Tienda	Software	Particular	1340,00
OP-1030	30/05/2026	Carlos	Sevilla	Online	Consumibles	Empresa	610,00
```

---

### Preparación de los datos

Antes de comenzar los ejercicios:

1. Pega los datos en una hoja nueva.
2. Asigna a la hoja el nombre `Ventas`.
3. Selecciona todo el rango de datos.
4. Convierte el rango en una **Tabla Estructurada**.
5. Asigna a la tabla el nombre `Tbl_Ventas_Practica`

---

## 🟢 Nivel básico — Creación y organización de una Tabla Dinámica

**Objetivo:** crear una Tabla Dinámica y configurar correctamente sus campos.

La empresa quiere conocer cuánto ha facturado cada comercial.

### Tarea

1. Inserta una Tabla Dinámica a partir de `Tbl_Ventas_Practica`.
2. Colócala en una hoja nueva denominada `TD_Comerciales`
3. Configura los campos:
   * **FILAS:** `Comercial`
   * **VALORES:** `Importe`
4. Comprueba que `Importe` se calcula mediante **Suma**.
5. Configura el campo `Importe` para que los resultados se muestren en **Moneda (€)**.
   - Utiliza **Configuración de campo de valor** para aplicar el formato.

### Reflexión

Explica brevemente:

> ¿Qué diferencia habría entre utilizar **Suma de Importe** y **Recuento de Importe**?

---

## 🟡 Nivel intermedio — Análisis multidimensional

**Objetivo:** utilizar simultáneamente las diferentes áreas de una Tabla Dinámica.

La empresa quiere analizar cómo se distribuyen las ventas de sus comerciales según el canal utilizado.

Crea una nueva Tabla Dinámica a partir de `Tbl_Ventas_Practica`.

Configura:

* **FILTROS:** `Provincia`
* **FILAS:** `Comercial`
* **COLUMNAS:** `Canal`
* **VALORES:** `Importe`

### Tareas

1. Selecciona únicamente la provincia de **Madrid** utilizando el área **FILTROS**.

2. Observa cómo cambia el informe.

3. Cambia el cálculo de `Importe` para mostrar sucesivamente:

   * **Suma**
   * **Promedio**
   * **Máximo**

4. Compara los resultados.

5. Vuelve a dejar el campo `Importe` configurado como **Suma**.

6. Aplica formato **Moneda (€)** desde la configuración del campo de valor.

### Reflexión

Explica qué información aporta cada cálculo:

| Cálculo  | ¿Qué información proporciona? |
| -------- | ----------------------------- |
| Suma     |                               |
| Promedio |                               |
| Máximo   |                               |

---

## 🟠 Nivel avanzado — Reorganización y actualización de una Tabla Dinámica

**Objetivo:** comprobar que una Tabla Dinámica puede reorganizarse y actualizarse sin modificar las fórmulas de los datos originales.

Partiendo de los datos de `Tbl_Ventas_Practica`, crea una Tabla Dinámica, en la hoja `TD_Familias`, que permita responder:

> ¿Qué familia de producto genera mayor facturación en cada provincia?

Configura inicialmente:

* **FILAS:** `Provincia`
* **COLUMNAS:** `Familia_Producto`
* **VALORES:** `Importe`

### Parte 1 — Reorganización

Modifica la Tabla Dinámica para responder ahora:

> ¿Cuánto ha facturado cada comercial en cada familia de producto?

Configura:

* **FILAS:** `Comercial`
* **COLUMNAS:** `Familia_Producto`
* **VALORES:** `Importe`

A continuación, reorganízala de nuevo para analizar:

> ¿Cuánto se ha vendido por tipo de cliente y canal?

Configura:

* **FILAS:** `Tipo_Cliente`
* **COLUMNAS:** `Canal`
* **VALORES:** `Importe`

### Parte 2 — Actualización

Ahora añade **cinco nuevas operaciones** al final de `Tbl_Ventas_Practica`.

Puedes utilizar los siguientes registros:

```text
OP-1031	04/06/2026	Ana	Madrid	Online	Hardware	Empresa	1980,00
OP-1032	09/06/2026	Carlos	Valencia	Tienda	Software	Profesional	875,00
OP-1033	14/06/2026	Marta	Sevilla	Online	Consumibles	Empresa	540,00
OP-1034	19/06/2026	Javier	Barcelona	Tienda	Hardware	Empresa	2150,00
OP-1035	24/06/2026	Ana	Madrid	Online	Software	Particular	1260,00
```

Después:

1. Comprueba si la Tabla Dinámica incorpora automáticamente los nuevos registros.
2. Actualiza la Tabla Dinámica utilizando:

   * Menú contextual.
   * Comando **Actualizar**.
   * Atajo `Alt+F5`.
3. Comprueba que las nuevas operaciones aparecen en el análisis.

### Reflexión

Explica:

> ¿Qué ventaja aporta poder modificar la estructura de un informe mediante los campos de la Tabla Dinámica sin tener que modificar las fórmulas de los datos originales?

---

## 🔴 Nivel experto — Auditoría y corrección de errores

**Objetivo:** utilizar las herramientas de auditoría de Excel para localizar y corregir errores en fórmulas.

Crea una hoja nueva denominada `Auditoria`.

En ella crea los siguientes ejemplos.

| Caso | Fórmula                                              | Error esperado |
| ---- | ---------------------------------------------------- | -------------- |
| 1    | `=A1+B1` siendo A2 un texto no convertible en número | `#¡VALOR!`     |
| 2    | `=A2/B2` siendo B2 igual a 0                         | `#¡DIV/0!`     |
| 3    | `=SUMAA(A1:A5)`                                      | `#¿NOMBRE?`    |
| 4    | Fórmula que haga referencia a una celda eliminada    | `#¡REF!`       |

### Tareas

Para cada caso:

1. Explica qué provoca el error.
2. Utiliza **Evaluar fórmula** para analizar la operación paso a paso.
3. Utiliza **Rastrear precedentes** y **Rastrear dependientes** cuando resulte apropiado.
4. Corrige la fórmula.
5. Comprueba el resultado.
6. Cuando sea apropiado, utiliza `SI.ERROR()` para controlar el error.

### Reflexión

Explica la diferencia entre:

> **Corregir un error** y **ocultar un error utilizando `SI.ERROR()`**.

¿Por qué es importante investigar primero la causa del error?

---

## 🔴🔴 Reto profesional — Informe de análisis para Dirección

**Objetivo:** combinar las principales funcionalidades de las Tablas Dinámicas trabajadas durante la sesión.

La dirección de la empresa necesita un informe que permita analizar rápidamente la actividad comercial.

Utilizando exclusivamente `Tbl_Ventas_Practica`, crea una hoja denominada `Informe_Direccion`.

En ella crearás varias Tablas Dinámicas independientes.


### Parte 1 — Facturación por comercial

Crea una Tabla Dinámica con:

* **FILAS:** `Comercial`
* **VALORES:** `Suma de Importe`

Determina:

> ¿Qué comercial ha obtenido la mayor facturación?

---

### Parte 2 — Facturación por provincia y familia

Crea una segunda Tabla Dinámica con:

* **FILAS:** `Provincia`
* **COLUMNAS:** `Familia_Producto`
* **VALORES:** `Suma de Importe`

Determina:

> ¿Qué provincia presenta la mayor facturación?

Y:

> ¿Qué familia de producto genera mayor facturación en esa provincia?

---

### Parte 3 — Análisis de los canales

Crea una tercera Tabla Dinámica con:

* **FILAS:** `Canal`
* **VALORES:** `Suma de Importe`
* **VALORES:** `Recuento de ID_Operacion`

Determina:

1. ¿Qué canal genera mayor facturación?
2. ¿Qué canal concentra más operaciones?
3. ¿Coincide el canal con mayor número de operaciones con el de mayor facturación?

---

### Parte 4 — Importe medio por comercial

Crea una cuarta Tabla Dinámica con:

* **FILAS:** `Comercial`
* **VALORES:** `Promedio de Importe`

Determina:

> ¿Qué comercial presenta el importe medio por operación más elevado?

Compara este resultado con la facturación total obtenida en la Parte 1.

---

### Parte 5 — Interpretación

Redacta un breve informe de **8–10 líneas** dirigido a la dirección.

Incluye:

* El comercial con mayor facturación.
* El comercial con mayor importe medio por operación.
* La provincia con mayor facturación.
* La familia de producto con mayor facturación.
* El canal con mayor volumen de negocio.
* La diferencia entre **suma**, **promedio** y **recuento**.
* Las ventajas de utilizar Tablas Dinámicas para analizar información empresarial.

---

### Parte 6 — Auditoría

En una hoja denominada `Control` y crea deliberadamente varias fórmulas que produzcan:

* `#¡VALOR!`
* `#¡DIV/0!`
* `#¿NOMBRE?`

Utiliza las herramientas de auditoría para localizar y corregir los errores.

Después:

1. Explica la causa de cada error.
2. Utiliza **Evaluar fórmula**.
3. Corrige las fórmulas.
4. Aplica `SI.ERROR()` cuando sea apropiado.
5. Comprueba que el resultado final es correcto.

---

### Parte 7 — Depuración asistida por IA

Selecciona una de las fórmulas que hayas analizado y consulta a un asistente de IA.

Utiliza una estructura de *prompt* similar a:

```text
Esta fórmula de Excel genera un error:

[pega aquí la fórmula]

Explícame qué hace cada parte de la fórmula,
identifica la causa del error y propón una solución corregida.

Indica también si sería apropiado utilizar SI.ERROR()
y explica por qué.
```

Documenta:

* El *prompt* utilizado.
* La respuesta obtenida.
* El error identificado.
* La solución propuesta.
* Las modificaciones que hayas tenido que realizar.
* El resultado comprobado finalmente en Excel.

> **Importante:** la IA es una herramienta de apoyo. Debes comprobar siempre en Excel que la solución propuesta funciona correctamente.

---

## Contenidos que debes haber practicado

Al finalizar estos ejercicios debes ser capaz de:

* Crear Tablas Dinámicas.
* Organizar campos en:

  * **FILAS**
  * **COLUMNAS**
  * **FILTROS**
  * **VALORES**
* Utilizar diferentes cálculos en los campos de valores:

  * Suma.
  * Promedio.
  * Máximo.
  * Recuento.
* Configurar correctamente el formato numérico de los valores.
* Utilizar filtros desde el área **FILTROS**.
* Reorganizar una Tabla Dinámica para obtener diferentes perspectivas.
* Actualizar una Tabla Dinámica.
* Interpretar los resultados obtenidos.
* Utilizar las herramientas de auditoría.
* Utilizar **Evaluar fórmula**.
* Utilizar **Rastrear precedentes**.
* Utilizar **Rastrear dependientes**.
* Comprender el uso de `SI.ERROR()`.
* Utilizar IA como apoyo para la depuración de fórmulas.
