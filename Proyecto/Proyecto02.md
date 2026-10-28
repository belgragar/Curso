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

