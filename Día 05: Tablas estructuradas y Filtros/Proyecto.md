# Sistema Integral de Gestión Comercial y Análisis de Ventas para una PYME

## Objetivo general

Iniciar el desarrollo de un libro de trabajo que evolucionará a lo largo de las cinco primeras sesiones del módulo hasta convertirse en una herramienta profesional de gestión, análisis y simulación comercial.

## Datos iniciales

Descarga el archivo **Datos_Proyecto.xlsx** incluido en el repositorio y guárdalo con el nombre:

```text
Sistema_Gestion_Comercial.xlsx
```

Este será el mismo libro de trabajo que utilizarás durante todo el proyecto.

La hoja **Base_Datos** contiene el registro inicial de operaciones comerciales realizadas por una empresa de distribución tecnológica.

## Desarrollo

Sobre la hoja **Base_Datos**:

1. Define los siguientes nombres de rango:

   * `Precio_Unitario`
   * `Cantidad`
   
2. Aplica un formato personalizado a la columna **Código_Operación** para mostrar los códigos con la estructura `OP-0000`.

3. Configura las siguientes reglas de formato condicional:

   * Resaltar en verde los importes superiores a **1.500 €**.
   * Resaltar en rojo los importes inferiores a **300 €**.
   * Resaltar toda la fila cuando el descuento aplicado sea superior al **10 %**.

4. Comprueba que el formato se aplica automáticamente al añadir nuevos registros.

Al finalizar esta fase dispondrás de una hoja `Base_Datos` limpia, legible y preparada para automatizar cálculos y realizar análisis.

---

# Automatización y depuración de la información comercial

## Objetivo general

Transformar los datos originales en información comercial estructurada mediante funciones lógicas y funciones de texto.

## Desarrollo

Trabajando sobre la misma hoja **Base_Datos**, añada las siguientes columnas al final de la tabla:

| Columna               | Descripción                                                                         |
| --------------------- | ----------------------------------------------------------------------------------- |
| Cliente_Normalizado   | Nombre del cliente sin espacios innecesarios y con formato correcto.                |
| SKU                   | Código generado automáticamente a partir de la categoría y del código de operación. |
| Precio_Final          | Precio tras aplicar el descuento correspondiente según el tipo de cliente.          |
| Descripción_Comercial | Texto descriptivo generado automáticamente con la información de la operación.      |
| Clasificación         | Clasificación del pedido mediante `SI.CONJUNTO` según el importe final.             |

Posteriormente:

1. Verifique alguna de las fórmulas utilizando ChatGPT o Claude.
2. Documente brevemente el *prompt* utilizado y la respuesta obtenida.

Al finalizar esta sesión la tabla contendrá información enriquecida generada automáticamente mediante fórmulas.

---

