# Proyecto Integrador — Módulo 2: Sistema Inteligente de Business Intelligence y Automatización Comercial

## Introducción y Datos de Partida (Punto de Partida Cero)

Para garantizar que todos los alumnos comiencen en igualdad de condiciones —independientemente de sus resultados en el Módulo 1—, **este proyecto parte completamente desde cero** con un nuevo libro de trabajo:

```text
Sistema_Inteligente_BI.xlsx

```

## Contexto empresarial

La empresa **Distribuciones Norte S.L.** requiere evolucionar su sistema informático de ventas hacia una solución avanzada de Inteligencia de Negocio y automatización comercial.

---

## Hoja Inicial: `Ventas_Brutas`

Nombramos a la hoja del libro **`Ventas_Brutas`**.

### Preparación y Formato Inicial de los Datos:

1. **Papeleo numérico limpio:** Los datos contienen valores numéricos puros (sin símbolos de moneda `€` ni de porcentaje `%` introducidos directamente como texto).
2. **Aplicar formato de celda:**
* Aplica formato **OP-0000** a la columna `Código_Operación`.
* Aplica formato **Fecha corta (`DD/MM/AAAA`)** a la columna `Fecha`.
* Aplica formato **Moneda (€)** a la columna `Precio_Unitario`.
* Aplica formato **Porcentaje (%)** a la columna `Descuento`.


3. **Convertir en Tabla Estructurada:** Selecciona todos los datos (`Ctrl+E`), pulsa **`Ctrl+T`** y nombra la tabla como **`Tbl_MasterVentas`**.
4. **Columna Calculada `Importe`:** Añade la columna **`Importe`** al final de la tabla (Columna K) e introduce la fórmula mediante referencias estructuradas:
```excel
=[@Cantidad] * [@Precio_Unitario] * (1 - [@Descuento])

```

Aplica formato **Moneda (€)** a toda la columna `Importe`, si no lo ha hecho ya la tabla por defecto.

---

## Progresión Pedagógica Diaria

## Fase 1: Análisis interactivo de ventas

### Objetivo general

Transformar los datos transaccionales en un entorno interactivo de exploración mediante la configuración de Tablas Dinámicas específicas para el posterior cuadro de mando, segmentadores y líneas de tiempo.

### Desarrollo

1. Crea una hoja denominada **`Analisis_Interactivo`**.
2. A partir de **`Tbl_MasterVentas`**, crea **cuatro Tablas Dinámicas independientes** (una para cada elemento visual posterior del Dashboard):

* **Tabla 1:** Ventas por Comercial (`Filas`) y `Suma de Importe` (`Valores`). *(Alimentará el Gráfico de Columnas de Comerciales)*.
* **Tabla 2:** Ventas por Canal (`Filas`) y `Suma de Importe` (`Valores`). *(Alimentará el Gráfico de Sectores/Anillo de Canales)*.
* **Tabla 3:** Ventas por `Fecha` agrupada por **Meses** (`Filas`) y `Suma de Importe` (`Valores`). *(Alimentará el Gráfico de Líneas de Evolución Temporal)*.
* **Tabla 4:** Resumen global de operaciones `Suma de Importe` (Facturación Total), `Promedio de Importe` (Importe Medio por Operación) y `Recuento de Código_Operación` (Total Operaciones). *(Alimentará las Tarjetas KPI)*.

3. Inserta **Segmentadores de datos** (*Slicers*) para los campos:

* `Comercial`
* `Provincia`
* `Familia_Producto`

4. Inserta una **Línea de tiempo** (*Timeline*) asociada al campo `Fecha`.
5. Conecta los segmentadores y la línea de tiempo a **las cuatro Tablas Dinámicas** mediante *Conexiones de informe*.
6. Maqueta la hoja `Analisis_Interactivo` organizando los filtros visuales en la zona superior y las tablas alineadas de forma limpia.

---

## Fase 2: Creación del Cuadro de Mando Ejecutivo

### Objetivo general

Diseñar un Dashboard visual e interactivo utilizando gráficos dinámicos y tarjetas de indicadores KPI integrados a partir de las tablas estructuradas en la Fase 1.

### Desarrollo

1. Crea una nueva hoja denominada **`Dashboard`** y desmarca las líneas de cuadrícula para obtener un lienzo limpio.
2. Diseña un panel ejecutivo incorporando los siguientes elementos vinculados directamente a las Tablas Dinámicas de la hoja `Analisis_Interactivo`:

* **Tarjetas / KPI:** Facturación Total, Importe Medio por Operación y Total Operaciones (utilizando celdas puente auxiliares vinculadas a la Tabla 4).
* **Gráfico Dinámico 1 (Columnas/Barras agrupadas):** Ventas por Comercial (basado en la Tabla 1, con botones de campo ocultos y ancho de entrepaño al 90%).
* **Gráfico Dinámico 2 (Sectores o Anillo):** Distribución de ventas por Canal (basado en la Tabla 2).
* **Gráfico Dinámico 3 (Líneas con marcadores):** Evolución temporal de las ventas (basado en la Tabla 3).

3. Corta (o copia) y traslada los segmentadores y la línea de tiempo creados en el Día 6 a la parte superior de la hoja **`Dashboard`** para controlar la visualización de todos los gráficos y KPIs de forma centralizada y sin incidencias.

---


## Día 8 — Fase 3: Modernización del sistema de consultas

### Objetivo general

Sustituir las búsquedas de datos tradicionales por funciones de búsqueda moderna: **BUSCARX** y **COINCIDIRX** (materia explicada en el Día 8).

### Desarrollo

1. En la hoja **`Ventas_Brutas`** o en una sección auxiliar de consulta, crea un buscador operativo por `Código_Operación`.
2. Utiliza **`BUSCARX`** para recuperar automáticamente el `Cliente`, `Comercial` e `Importe` correspondiente a un código introducido.
3. Utiliza **`COINCIDIRX`** para determinar la posición relativa exacta de una provincia o comercial en el cuadro general.
4. Implementa la gestión de errores nativa de `BUSCARX` (`[si_no_se_encuentra]`) para evitar mostrar errores tipo `#N/A`.
5. Incluye una breve nota explicativa en la hoja detallando las ventajas técnicas de `BUSCARX` frente a `BUSCARV`.

Los ejercicios de este día 8 han sido modificados por:

### Objetivo general

Sustituir los métodos de búsqueda tradicionales del sistema por un modelo interactivo, robusto y visual basado en **BUSCARX** y **COINCIDIRX**, integrando la extracción multicolumna, la búsqueda por tramos, la búsqueda inversa y la visualización dinámica mediante gráficos interactivos del Día 07.

### Bloque 1: Sistema de Consulta Principal (`Ventas_Brutas`)

1. **Buscador de Operaciones Multi-columna:**
   * En la hoja **`Ventas_Brutas`** (o pestaña **`Buscador`**), crea un panel interactivo por `Código_Operación`.
   * Utiliza una **única fórmula de `BUSCARX**` que devuelva simultáneamente el `Cliente`, `Comercial`, `Provincia` e `Importe`.
   * Configura el parámetro nativo `[si_no_se_encuentra]` con el mensaje: `"Operación no registrada"`.

2. **Consulta Historica de Última Operación y Tramo:**
   * Utiliza **`BUSCARX` con `modo_busqueda = -1**` para localizar la fecha y monto de la *última transacción* registrada para un comercial determinado.
   * Utiliza **`BUSCARX` en modo de coincidencia aproximada (`-1`)** para calcular automáticamente la tasa de comisión aplicable a cada operación según la tabla oficial de tramos de la empresa.

### Bloque 2: Integración Visual — Mini-Dashboard de Comercial (Conexión Día 07 + Día 08)

3. **Gráfico Dinámico de Rendimiento:**
   * Diseña una sección de consulta por `Comercial` con un desplegable de selección.
   * Emplea `BUSCARX` para extraer la serie de ventas trimestrales del comercial a una tabla auxiliar de apoyo.
   * Vincula a esta tabla de apoyo un **Gráfico Dinámico** (Día 07) que se actualice automáticamente al cambiar la selección.

### Bloque 3: Documentación Técnica y Auditoría con IA

4. **Nota de Arquitectura de Datos y Auditoría IA:**
   * Incluye un cuadro de texto en la hoja explicando las ventajas técnicas de la migración a `BUSCARX`.
   * Audita la fórmula del Mini-Dashboard utilizando un prompt en ChatGPT/Claude y adjunta el informe técnico devuelto por la IA.

### 🚀 Retos de Extensión "PRO" (Para los que acaben pronto 😉)

* **Reto 1 (Título Dinámico en Gráfico):** Haz que el título del gráfico del Mini-Dashboard cambie automáticamente concatenando texto y fórmulas (ej. `="Informe de Rendimiento Comercial: " & B3`).

* **Reto 2 (Búsqueda Bidireccional Matriz 2D):** Implementa una búsqueda cruzada de 2 ejes (`Fila x Columna`) combinando dos funciones `BUSCARX` anidadas para consultar la venta de un `Comercial` en una `Provincia` concreta.

* **Reto 3 (Auditoría con IA):** Consulta a ChatGPT/Claude/Copilot para evaluar la velocidad de cálculo de una búsqueda bidireccional en tablas de más de 100.000 filas.

---

## Fase 4: Informes automáticos con matrices dinámicas

### Objetivo general

Construir reportes automáticos auto-expandibles mediante las funciones de matriz dinámica: **FILTRAR**, **UNICO**, **ORDENAR** y **SECUENCIA** (materia explicada en el Día 9).

### Desarrollo

1. Crea una nueva hoja denominada **`Informes_Automaticos`**.
2. Mediante **`UNICO`**, genera un listado automático y dinámico de los clientes sin duplicados.
3. Mediante **`ORDENAR`** y **`FILTRAR`**, genera una tabla dinámica de consulta que extraiga todas las operaciones de un `Canal` específico elegible, ordenadas de mayor a menor importe.
4. Genera una lista numerada automática para el informe mediante la función **`SECUENCIA`**.

---
