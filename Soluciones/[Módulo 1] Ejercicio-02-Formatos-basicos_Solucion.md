# Ejercicio - Formato de datos básico

## 1. Contexto de Negocio

La empresa **"Global Logistics & Supplies, S.A."** está auditando sus registros de operaciones comerciales e inventario. El departamento administrativo necesita estructurar una tabla de control donde los datos numéricos, de fecha, hora, moneda y porcentajes se muestren de forma rigurosa y profesional utilizando exclusivamente los **formatos de números nativos de Excel** (sin recurrir a formatos personalizados). Tu objetivo es corregir y formatear el informe para que la gerencia pueda interpretarlo sin errores de legibilidad.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de texto delimitado por punto y coma (`;`) y pégalo directamente en la celda **A1** de una nueva hoja de Excel:

```csv
Codigo_Envio;Producto;Fecha_Recepcion;Hora_Entrega;Cantidad_Unidades;Precio_Coste;Margen_Beneficio;Peso_Kg;Porcentaje_Impuesto
ENV-001;Laptop Pro 15;15/09/2026;09:30;12;850,50;0,25;2,450;0,21
ENV-002;Monitor UltraWide;16/09/2026;11:15;8;310,00;0,30;6,200;0,21
ENV-003;Teclado Mecánico;16/09/2026;14:45;25;45,75;0,40;0,850;0,21
ENV-004;Ratón Ergónomico;17/09/2026;08:20;40;18,20;0,45;0,120;0,21
ENV-005;Silla de Oficina;18/09/2026;16:00;5;175,00;0,35;14,500;0,21
ENV-006;Hub USB-C 7 en 1;19/09/2026;10:10;30;25,90;0,50;0,150;0,21

```

---

## 3. Tareas a Resolver

Aplica los siguientes cambios seleccionando los rangos adecuados y utilizando el cuadro de diálogo **Formato de celdas** (`Ctrl + 1`):

1. **Columna `Codigo_Envio`:** Aplica la categoría **Texto** (o asegúrate de que se interprete de forma literal) para que los guiones y ceros iniciales se mantengan intactos.
2. **Columna `Fecha_Recepcion`:** Aplica el formato de tipo **Fecha** eligiendo un formato estándar (por ejemplo, `14/03/2012`).
3. **Columna `Hora_Entrega`:** Aplica el formato de tipo **Hora** (por ejemplo, `13:30`).
4. **Columna `Cantidad_Unidades`:** Aplica el formato de tipo **Número** mostrando separador de miles y **cero decimales**.
5. **Columnas `Precio_Coste` y cálculo de `Precio_Venta` (añade esta última columna aplicando la fórmula `=Precio_Coste * (1 + Margen_Beneficio)`):** Aplica el formato de tipo **Moneda** con símbolo de Euro (`€`) y **dos decimales**.
6. **Columnas `Margen_Beneficio` y `Porcentaje_Impuesto`:** Aplica el formato de tipo **Porcentaje** con **dos decimales**.
7. **Columna `Peso_Kg`:** Aplica el formato de tipo **Número** mostrando exactamente **tres decimales**.

---

## 4. Guía de Solución Paso a Paso

### Paso 1: Preparación inicial y conversión de tipos

1. Selecciona el rango de la columna **`Codigo_Envio`** (desde `A2` hasta `A7`). Pulsa `Ctrl + 1`, ve a la categoría **Texto** y pulsa **Aceptar**. Esto evita que Excel interprete los datos de forma imprevista.
2. Añade una nueva columna en la celda **`J1`** con el título **`Precio_Venta`**. En la celda `J2` introduce la fórmula:
`=F2 * (1 + G2)`
*(Arrastra la fórmula hacia abajo hasta la fila 7).*

### Paso 2: Aplicar formatos numéricos nativos (Sin personalizados)

Selecciona cada bloque de columnas y utiliza la combinación `Ctrl + 1` para configurar los formatos oficiales de la categoría **Número**:

* **Fechas (`C2:C7`):**
1. Pulsa `Ctrl + 1` y selecciona la categoría **Fecha**.
2. Elige el tipo estándar correspondiente a `14/03/2012` y haz clic en **Aceptar**.


* **Horas (`D2:D7`):**
1. Pulsa `Ctrl + 1` y selecciona la categoría **Hora**.
2. Elige el tipo que muestra horas y minutos (ej. `13:30`) y pulsa **Aceptar**.


* **Unidades (`E2:E7`):**
1. Pulsa `Ctrl + 1` y selecciona **Número**.
2. Establece posiciones decimales en `0` y activa la casilla de verificación de separador de miles si lo deseas. Haz clic en **Aceptar**.


* **Monedas (`F2:F7` y `J2:J7`):**
1. Selecciona los precios de coste y de venta. Pulsa `Ctrl + 1` y selecciona la categoría **Moneda**.
2. Configura los decimales a `2` y asegúrate de seleccionar el símbolo de **Euro (€)** adaptado a la configuración regional española. Pulsa **Aceptar**.


* **Porcentajes (`G2:G7` e `I2:I7`):**
1. Selecciona los márgenes y los impuestos. Pulsa `Ctrl + 1` y selecciona la categoría **Porcentaje**.
2. Configura las posiciones decimales en `2` y pulsa **Aceptar**.


* **Peso en Kg (`H2:H7`):**
1. Selecciona la columna de pesos. Pulsa `Ctrl + 1` y selecciona **Número**.
2. Modifica el número de posiciones decimales exactamente a **`3`** para reflejar la precisión en gramos y pulsa **Aceptar**.

