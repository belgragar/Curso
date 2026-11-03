# Ejercicio 24: Funciones matemáticas avanzadas - Auditoría Logística y Facturación de Portes

## 1. Contexto de Negocio

Trabajas como analista de logística y costes en una empresa de distribución de suministros industriales con sede en Gijón. La dirección comercial te ha entregado el registro de los envíos interurbanos de la última semana.

Para profesionalizar el control de costes y facturación, debes convertir el registro inicial en una **Tabla Estructurada de Excel** denominada `Tbl_EnviosLogistica`. Tu objetivo es:

1. Auditar los pesos de las expediciones y aplicar las reglas del transportista (cobro por tramos de tonelada/kilo completo al alza).


2. Calcular los costes brutos mediante multiplicación matricial directa sin columnas intermedias.


3. Garantizar la consolidación de importes ignorando incidencias de carga de datos (`#¡VALOR!`).


4. Evaluar las bonificaciones por volumen mediante agregación condicional multidimensional.


5. Comparar los comportamientos de truncamiento sobre penalizaciones por retraso en entregas (diferenciando `ENTERO` de `REDONDEAR.MENOS` con valores negativos).


6. Automatizar un patrón de lectura alterno (cebreado) mediante lógica divisional de filas que no se desconfigure al filtrar o reorganizar datos.



---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente contenido en formato CSV (adaptado a la configuración regional de España con `;` como separador de columnas y `,` como separador decimal) y pégalo directamente en la celda **A1** de una hoja nueva de Excel:

```csv
ID_Envio;Zona_Destino;Peso_Toneladas;Tarifa_Tonelada;Transporte_Nocturno;Seguro_Riesgo;Penalizacion_Retraso
ENV-801;Norte;3,15;85,00;SI;150,25;-12,40
ENV-802;Centro;5,80;72,50;NO;60,00;-8,10
ENV-803;Norte;2,05;90,00;SI;#¡VALOR!;-15,75
ENV-804;Sur;4,10;68,00;NO;0,00;0,00
ENV-805;Norte;6,90;80,00;NO;110,50;-22,30
ENV-806;Centro;8,35;70,00;NO;40,00;-3,80
ENV-807;Norte;1,20;95,00;SI;210,00;-5,60

```

---

## 3. Tareas a Resolver

1. **Conversión a Tabla Estructurada:** Convierte el rango `A1:G8` en una Tabla Estructurada de Excel y asígnale el nombre **`Tbl_EnviosLogistica`**.


2. **Agregación Multidimensional (`SUMAR.SI.CONJUNTO`):** En una celda fuera de la tabla, calcula el total de `Peso_Toneladas` para la `"Zona_Destino"` igual a `"Norte"` que además se hayan realizado con `"Transporte_Nocturno"` igual a `"SI"` utilizando referencias estructuradas.


3. **Multiplicación Matricial Directa (`SUMAPRODUCTO`):** En otra celda externa, calcula el coste global base del transporte multiplicando la columna `Peso_Toneladas` por `Tarifa_Tonelada` en un solo paso y sin crear columnas auxiliares.


4. **Subtotales Dinámicos (`SUBTOTALES`):** Activa la **Fila de Totales** de la tabla estructurada y configura el sumatorio dinámico de la columna `Peso_Toneladas` mediante la función `SUBTOTALES` (código `109`) para que responda a los filtros de interfaz.


5. **Consolidación Robusta ante Errores (`AGREGAR`):** Calcula fuera de la tabla la suma total de la columna `Seguro_Riesgo` omitiendo automáticamente el valor de error `#¡VALOR!`.


6. **Control de Precisión y Reglas de Facturación (`REDONDEAR.MAS` y `REDONDEAR.MENOS`):**
* Añade una columna calculada llamada **`Toneladas_Facturables`**: La agencia de transportes factura por cada fracción de tonelada iniciada como una tonelada completa (`REDONDEAR.MAS` a `0` decimales).


* Añade una columna calculada llamada **`Toneladas_Base`**: Muestra únicamente las toneladas enteras completas para la liquidación de incentivos (`REDONDEAR.MENOS` a `0` decimales).




7. **Comparativa de Truncamiento en Negativos (`ENTERO` vs `REDONDEAR.MENOS`):**
* Añade una columna calculada llamada **`Penalizacion_Entero`**: Evalúa el entero de la columna `Penalizacion_Retraso` mediante `=ENTERO([@[Penalizacion_Retraso]])`.


* Añade una columna calculada llamada **`Penalizacion_Menos`**: Evalúa el truncamiento hacia cero con `=REDONDEAR.MENOS([@[Penalizacion_Retraso]]; 0)`.




8. **Automatización Visual por Filas (`RESIDUO`):** Aplica un Formato Condicional mediante fórmula utilizando `RESIDUO` y `FILA` para colorear en un tono gris o azul claro tenue únicamente las filas pares de la tabla.


