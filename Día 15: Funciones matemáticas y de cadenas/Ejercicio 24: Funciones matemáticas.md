# Ejercicio 24: Funciones matemáticas avanzadas

En este ejercicio utilizaremos una **Tabla Estructurada** nombrada `Tbl_ParteTrabajo` y combinaremos:

1. **`SUMAR.SI.CONJUNTO`**: Agregación multidimensional con varios criterios.


2. **`SUMAPRODUCTO`**: Multiplicación matricial sin columnas auxiliares.


3. **`SUBTOTALES`**: Subtotal dinámico que respeta los filtros aplicados.


4. **`AGREGAR`**: Subtotal avanzado que omite errores estructurales (`#¡VALOR!`) y filtros.


5. **`REDONDEAR.MAS`**: Redondeo al alza alejado de cero (para reglas de facturación).


6. **`REDONDEAR.MENOS`**: Redondeo hacia el cero (para conteo estricto de horas completadas).


7. **`ENTERO`**: Truncamiento al entero inferior más próximo (incluyendo la diferencia de comportamiento con valores negativos).


8. **`RESIDUO`**: Lógica de división e interruptor binario para automatización visual con formato condicional.



---

## 1. Contexto de Negocio

Trabajas como analista de operaciones en una empresa de servicios industriales y tecnológicos en Asturias. La dirección necesita auditar el parte semanal de trabajo de los técnicos para preparar la facturación a clientes, controlar los costes de producción interna y ajustar las desviaciones presupuestarias acumuladas.

Para asegurar la escalabilidad del modelo, trabajarás sobre una **Tabla Estructurada de Excel**. Deberás procesar horas de servicio con decimales, evaluar reglas estrictas de precisión financiera, asegurar los sumatorios globales ante registros que contienen errores, realizar comparativas de truncamiento de penalizaciones negativas y aplicar una lectura visual alternada (cebreado) totalmente dinámica.

---

## 2. Conjunto de Datos (Dataset)

Copia el siguiente bloque de texto en formato CSV (delimitado por punto y coma `;` adaptado a la configuración regional de España) y pégalo directamente en la celda **A1** de una hoja nueva de Excel:

```csv
ID_Parte;Servicio;Horas_Reales;Tarifa_Hora;Turno_Noche;Importe_Material;Ajuste_Presupuesto
PAR-101;Mantenimiento;10,25;50,00;SI;120,50;-2,20
PAR-102;Soporte;8,50;60,00;NO;45,00;-1,80
PAR-103;Mantenimiento;12,75;55,00;SI;#¡VALOR!;-3,50
PAR-104;Ventas;7,10;45,00;NO;0,00;0,00
PAR-105;Mantenimiento;9,00;52,00;NO;85,25;-4,10
PAR-106;Soporte;11,80;48,00;NO;15,00;-0,50
PAR-107;Mantenimiento;6,40;58,00;SI;300,00;-1,20

```

---

## 3. Tareas a Resolver

1. **Estructuración de Datos:** Convierte el rango `A1:G8` en una Tabla Estructurada con el nombre **`Tbl_ParteTrabajo`**.


2. **Agregación Multidimensional (`SUMAR.SI.CONJUNTO`):** Calcula el total de horas reales acumuladas para el servicio de `"Mantenimiento"` realizadas en `"Turno_Noche = SI"` utilizando referencias estructuradas.


3. **Multiplicación Matricial Directa (`SUMAPRODUCTO`):** Calcula el coste total bruto de mano de obra en un solo paso multiplicando la columna `Horas_Reales` por `Tarifa_Hora` sin añadir columnas intermedias.


4. **Subtotales ante Filtros e Interfaz (`SUBTOTALES`):** Añade la **Fila de Totales** a la tabla y configura la celda de la columna `Horas_Reales` con la función `SUBTOTALES` (código `109`) para que el sumatorio responda visualmente a los filtros aplicados.


5. **Integridad ante Errores (`AGREGAR`):** Calcula fuera de la tabla el importe total de la columna `Importe_Material` mediante la función `AGREGAR` para omitir automáticamente el valor `#¡VALOR!` de la fila 4.


6. **Control de Precisión y Reglas de Facturación (`REDONDEAR.MAS` y `REDONDEAR.MENOS`):**
* Añade la columna **`Horas_Facturables`**: Aplica la regla comercial donde las fracciones de hora se cobren como hora completa (`REDONDEAR.MAS` a `0` decimales).


* Añade la columna **`Horas_Enteras`**: Calcula solo las horas completas trabajadas para el cómputo estricto de producción (`REDONDEAR.MENOS` a `0` decimales).




7. **Comparativa de Truncamiento y Negativos (`ENTERO` vs `REDONDEAR.MENOS`):**
* Añade la columna **`Ajuste_Entero`**: Trunca la columna `Ajuste_Presupuesto` utilizando `=ENTERO([@[Ajuste_Presupuesto]])`.


* Añade la columna **`Ajuste_Menos`**: Trunca la misma columna utilizando `=REDONDEAR.MENOS([@[Ajuste_Presupuesto]]; 0)`.


* *Analiza la diferencia entre ambos resultados con números negativos*.




8. **Automatización Visual por Filas (`RESIDUO`):** Aplica una regla de Formato Condicional con `RESIDUO` y `FILA` para colorear en un verde claro tenue únicamente las filas pares de la tabla.

