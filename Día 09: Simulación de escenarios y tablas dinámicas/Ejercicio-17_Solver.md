# Ejercicio 16: Solver

## 1. Contexto de Negocio

Una cooperativa agraria proyecta el margen de beneficio de la cosecha de aceite de oliva bajo diferentes escenarios de mercado y climáticos. Además de simular previsiones mediante el Administrador de escenarios, la dirección financiera necesita aplicar técnicas avanzadas de análisis de sensibilidad: calcular mediante **Búsqueda de Objetivos** la producción exacta necesaria para alcanzar una meta ambiciosa de beneficio, y construir una **Tabla de Datos** de una variable para evaluar cómo fluctúa dicho beneficio ante distintos precios de venta por kilogramo.

---

## 2. Conjunto de Datos (Dataset)

Copia y pega los siguientes datos directamente en una hoja de Excel (desde la celda `A1` hasta la celda `B8`), utilizando el punto y coma (`;`) como separador de columnas:

```csv
Concepto;Valor / Fórmula
Producción (kg);500.000
Precio de Venta (€/kg);3,80
Coste Energético (€);120.000
Coste de Riego (€);50.000
Ingresos Totales;=B2*B3
Costes Totales;=B4+B5
Margen de Beneficio;=B6-B7

```

---

## 3. Tareas a Resolver

1. **Estructuración y Fórmulas:** Introduce los datos en Excel, configura las fórmulas en las celdas `B6`, `B7` y `B8` empleando el punto y coma (`;`) como separador de argumentos.
2. **Administrador de Escenarios:** Configura los tres escenarios clásicos (*Base*, *Optimista* con `650.000` kg y `4,20` €/kg, y *Sequía* reduciendo la producción a la mitad y elevando el coste de riego un 40%) tomando como celdas cambiantes el rango `B2:B5`, y genera el informe resumen de la celda `B8`.


3. **Búsqueda de Objetivos:** Utiliza la herramienta de cálculo inverso para averiguar qué volumen exacto de **Producción (kg)** (`B2`) necesita la cooperativa para alcanzar un **Margen de Beneficio** (`B8`) de `1.000.000 €` en el escenario base.


4. **Tabla de Datos de una Variable:** Diseña una tabla de sensibilidad vertical a partir de la celda `D2` evaluando distintos precios de venta (desde `3,00` € hasta `5,00` € con incrementos de `0,20` €) para comprobar su impacto automático en el margen de beneficio.



---

## 4. Guía de Solución Paso a Paso

### Paso 1: Preparación del modelo base

* En la celda `B6`, calcula los ingresos totales: `=B2*B3`.
* En la celda `B7`, calcula los costes totales: `=B4+B5`.
* En la celda `B8`, calcula el margen de beneficio neto: `=B6-B7`.

### Paso 2: Aplicación del Administrador de Escenarios

1. Dirígete a la pestaña **Datos** > **Análisis de hipótesis** > **Administrador de escenarios...**

2. Haz clic en **Agregar...** y crea los escenarios:


* **Base:** Celdas cambiantes `B2:B5` (valores actuales).
* **Optimista:** Celdas cambiantes `B2:B5` con los valores `650.000` (B2), `4,20` (B3), `100.000` (B4) y `40.000` (B5).
* **Sequia:** Celdas cambiantes `B2:B5` con los valores `250.000` (B2), `4,50` (B3), `140.000` (B4) y `70.000` (B5).


3. Haz clic en **Resumen...**, selecciona *Resumen de escenario* y fija la celda de resultado en `B8`. Pulsa **Aceptar** para generar la hoja consolidada.



### Paso 3: Aplicación de Búsqueda de Objetivos

Supongamos que la junta directiva establece una meta de beneficio estricta y queremos averiguar los kilos necesarios sin alterar manualmente las celdas:

1. Vuelve a la hoja principal y haz clic en **Datos** > **Análisis de hipótesis** > **Buscar objetivo...**

2. Configura los parámetros de la ventana emergente:


* **Definir la celda:** `B8` (Celda del Margen de Beneficio, que contiene fórmula).
* **Con el valor:** `1000000` (1.000.000).
* **Para cambiar la celda:** `B2` (Celda de Producción en kg).


3. Haz clic en **Aceptar**. Excel iterará de forma automática hasta mostrar que se requieren `289.473,68` kg (aproximadamente) para alcanzar exactamente dicho objetivo de beneficio.



### Paso 4: Creación de la Tabla de Datos de una Variable

Para evaluar la sensibilidad del beneficio ante distintos precios de venta:

1. En la celda `D3`, introduce el primer precio de prueba: `3,00`. Rellena hacia abajo en la columna `D` (desde `D3` hasta `D13`) los valores sucesivos hasta `5,00` con incrementos de `0,20` (`3,20`, `3,40`, `3,60`, etc.).
2. En la celda superior derecha adyacente (`E2`), introduce la fórmula de enlace que apunta al beneficio: `=B8`.
3. Selecciona todo el rango de la tabla de simulación (`D2:E13`).
4. Ve a la pestaña **Datos** > **Análisis de hipótesis** > **Tabla de datos...**
5. Como los valores de prueba están dispuestos en columnas, haz clic en el campo **Celda de entrada de columna** y selecciona la celda original del precio de venta: `B3`.
6. Pulsa **Aceptar**. Excel rellenará automáticamente toda la matriz calculando el margen de beneficio para cada nivel de precio.


