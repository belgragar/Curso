# Proyecto Integrador — Módulo 1
# Sistema Integral de Gestión Comercial y Análisis de Ventas para una PYME


# Día 1 — Proyecto Integrador (Fase 1): Preparación y control visual de la información comercial

### Objetivo

Preparar la hoja de datos para trabajar de forma profesional con nombres de rango, formatos personalizados y formato condicional.

### Datos iniciales

Descarga **Datos_Proyecto_Dia1.xlsx** del repositorio y guárdalo como:

```text
Sistema_Gestion_Comercial.xlsx
```

Trabajarás sobre la hoja:

```text
Base_Datos
```

### Tareas

1. Comprueba que los datos están correctamente distribuidos en columnas y que los encabezados son claros.

2. Crea un nombre de rango para la columna de precios:

```text
Precio_Unitario
```

3. Crea un nombre de rango para la columna de cantidades:

```text
Cantidad
```

4. **No crees todavía un nombre `Importe` para toda la columna.** El campo `Importe` ya contiene datos calculados y, en las siguientes fases, se trabajará con él como campo de la base de datos y posteriormente como columna de una Tabla Estructurada.

5. Aplica a `Código_Operación` un formato personalizado que permita visualizar los códigos con la estructura:

```text
OP-0000
```

6. Aplica formato de moneda a `Precio_Unitario` e `Importe`.

7. Crea una regla de formato condicional para destacar los importes superiores a **1.500 €**.

8. Crea otra regla para destacar los importes inferiores a **300 €**.

9. Crea una regla mediante fórmula para resaltar toda la fila cuando el descuento sea superior al **10 %**.

10. Añade un registro de prueba al final del listado y comprueba cómo se comportan los formatos.

> **Importante:** en esta fase los datos todavía no se convierten en Tabla Estructurada. Por tanto, no se exige que el formato se extienda automáticamente a nuevos registros. La automatización de la expansión de los datos se trabajará en el **Día 3**, cuando se convierta el listado en una Tabla Estructurada.

### Resultado esperado

Al finalizar el Día 1 tendrás una hoja `Base_Datos` limpia, legible y preparada para continuar el proyecto.

---

# Día 2 — Proyecto Integrador (Fase 2): Automatización y enriquecimiento de la información comercial

### Objetivo

Añadir información calculada a partir de los datos existentes utilizando funciones de texto, lógicas y referencias.

### Tareas

Trabaja sobre la hoja `Base_Datos` y añade al final de los datos las siguientes columnas:

| Nueva columna | Objetivo |
| --- | --- |
| `Cliente_Normalizado` | Eliminar espacios innecesarios y normalizar el nombre del cliente. |
| `SKU` | Generar un código combinando la familia de producto y el código de operación. |
| `Precio_Final` | Calcular el precio unitario después de aplicar el descuento. |
| `Descripción_Comercial` | Crear una descripción automática de la operación. |
| `Clasificación` | Clasificar la operación según su importe. |

### Requisitos

1. En `Cliente_Normalizado`, utiliza funciones de texto para eliminar espacios innecesarios.

2. En `SKU`, genera un código que combine `Familia_Producto` y `Código_Operación`.

3. En `Precio_Final`, calcula:

```text
Precio_Unitario × (1 - Descuento / 100)
```

4. En `Descripción_Comercial`, crea un texto que incluya, como mínimo:

```text
Cliente + Familia de Producto + Cantidad + Importe
```

5. En `Clasificación`, utiliza una función lógica como `SI.CONJUNTO` para clasificar las operaciones:

| Importe | Clasificación |
| ---: | --- |
| Menor de 500 € | Baja |
| De 500 € a menos de 2.000 € | Media |
| 2.000 € o más | Alta |

6. Comprueba algunas de las fórmulas con un asistente de IA.

7. Documenta en un comentario o en una hoja llamada `Notas_IA`:

   - La fórmula consultada.
   - El prompt utilizado.
   - La respuesta obtenida.
   - Si aceptaste o modificaste la propuesta de la IA.

### Resultado esperado

La hoja `Base_Datos` contendrá ahora información original y columnas calculadas que enriquecen el análisis comercial.

---

# Día 3 — Proyecto Integrador (Fase 3): Conversión en Base de Datos Profesional

### Objetivo

Convertir el listado en una Tabla Estructurada de Excel para facilitar el crecimiento automático de los datos y el uso de referencias estructuradas.

### Tareas

1. Selecciona todo el conjunto de datos de `Base_Datos`, incluyendo las columnas originales y las nuevas columnas calculadas.

2. Convierte el rango en una **Tabla Estructurada** mediante:

```text
Ctrl + T
```

3. Marca la opción:

```text
La tabla tiene encabezados
```

4. Asigna a la tabla el nombre:

```text
Tbl_MasterVentas
```

5. Comprueba que las nuevas columnas calculadas utilizan referencias estructuradas cuando sea apropiado.

6. Añade una nueva operación al final de la tabla y comprueba que:

   - La tabla se amplía automáticamente.
   - Las fórmulas calculadas se propagan.
   - El formato se mantiene.

### Hoja `Dashboard_Síntesis`

Crea una nueva hoja denominada:

```text
Dashboard_Síntesis
```

Utiliza referencias estructuradas y funciones apropiadas para mostrar:

- Número total de operaciones.
- Facturación total.
- Facturación media por operación.
- Número de clientes diferentes.
- Número de comerciales diferentes.
- Facturación de las operaciones realizadas mediante canal `Online`.
- Facturación de las operaciones realizadas mediante `Tienda Física`.

### Gráfico

Crea un gráfico que represente la evolución de la facturación por fecha.

### Comprobación

Añade una nueva operación a `Tbl_MasterVentas` y verifica que los cálculos y el gráfico se actualizan correctamente.

> **Objetivo de esta fase:** ahora sí puedes aprovechar las ventajas de una Tabla Estructurada. Los nombres de rango utilizados en el Día 1 no deben confundirse con una Tabla Estructurada ni sustituirla.


