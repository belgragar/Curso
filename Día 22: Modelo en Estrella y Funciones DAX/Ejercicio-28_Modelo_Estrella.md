# Ejercicio 28: de Modelado de Datos en Power BI - Modelo en Estrella

## Enunciado
El objetivo de este ejercicio es practicar el modelado de datos en Power BI utilizando un modelo en estrella. Se proporcionará un archivo CSV que contiene una única tabla con múltiples columnas. Se deberán separar estas columnas en varias tablas, creando una tabla de hechos y varias tablas de dimensiones. Además, deberán generar una tabla de fechas.

### Requisitos adicionales:
- Las tablas de dimensiones deben tener una clave primaria.
- La tabla de hechos debe incluir las claves foráneas correspondientes a las tablas de dimensiones.
- Las tablas de dimensiones tendrán el prefijo `Dim_` y la tabla de hechos tendrá el prefijo `Fact_`.

## Archivo CSV de Ejemplo
A continuación se presenta un ejemplo de cómo se vería el archivo CSV. Puedes copiarlo y guardarlo como `ventas.csv`.

```csv
Fecha,Producto,Categoría,Cliente,Región,Cantidad,Ventas
2023-01-15,Producto A,Electrónica,Cliente 1,Norte,10,1000
2023-01-16,Producto B,Electrónica,Cliente 2,Norte,5,500
2023-01-17,Producto A,Electrónica,Cliente 3,Sur,3,300
2023-01-18,Producto C,Hogar,Cliente 1,Norte,7,700
2023-01-19,Producto B,Hogar,Cliente 2,Sur,2,200
2023-01-20,Producto A,Hogar,Cliente 3,Este,4,400
```

## Instrucciones
1. **Carga de Datos**: Importa el archivo `ventas.csv` en Power BI.
2. **Separación de Tablas**:
   - Crea una tabla de hechos llamada `Fact_Ventas` que contenga las columnas `Fecha`, `ProductoID`, `ClienteID`, `Cantidad` y `Ventas`.
   - Crea una tabla de dimensiones llamada `Dim_Producto` que contenga las columnas `ProductoID`, `Producto` y `Categoría`.
   - Crea una tabla de dimensiones llamada `Dim_Cliente` que contenga las columnas `ClienteID`, `Cliente` y `Región`.
   - Crea una tabla de fechas llamada `Dim_Fecha` que contenga todas las fechas del año 2023.
3. **Relaciones**: Establece las relaciones adecuadas entre las tablas:
   - Relaciona `Fact_Ventas` con `Dim_Producto` a través de `ProductoID`.
   - Relaciona `Fact_Ventas` con `Dim_Cliente` a través de `ClienteID`.
   - Relaciona `Fact_Ventas` con `Dim_Fecha` a través de `Fecha`.

## Solución Paso a Paso
1. **Cargar el archivo CSV**:
   - Abre Power BI y selecciona "Obtener datos".
   - Elige "Texto/CSV" y selecciona el archivo `ventas.csv`.
   - Carga los datos.

2. **Crear la tabla de hechos**:
   - Ve a la vista de "Modelado".
   - Crea una nueva tabla llamada `Fact_Ventas` con las siguientes columnas:
     - `Fecha`
     - `ProductoID`
     - `ClienteID`
     - `Cantidad`
     - `Ventas`
   - Llena esta tabla con los datos de las columnas correspondientes del CSV, asegurándote de reemplazar `Producto` y `Cliente` por sus respectivos IDs.

3. **Crear la tabla de dimensiones `Dim_Producto`**:
   - Crea una nueva tabla llamada `Dim_Producto` con las columnas:
     - `ProductoID` (clave primaria)
     - `Producto`
     - `Categoría`
   - Llena esta tabla con los datos únicos de `Producto` y `Categoría` del CSV, generando un `ProductoID` único para cada producto.

4. **Crear la tabla de dimensiones `Dim_Cliente`**:
   - Crea una nueva tabla llamada `Dim_Cliente` con las columnas:
     - `ClienteID` (clave primaria)
     - `Cliente`
     - `Región`
   - Llena esta tabla con los datos únicos de `Cliente` y `Región` del CSV, generando un `ClienteID` único para cada cliente.

5. **Crear la tabla de fechas `Dim_Fecha`**:
   - Crea una nueva tabla llamada `Dim_Fecha` que contenga todas las fechas del año 2023. Puedes usar DAX para generarla:
     ```DAX
     Dim_Fecha = CALENDAR(DATE(2023, 1, 1), DATE(2023, 12, 31))
     ```

6. **Establecer relaciones**:
   - Ve a la vista de "Modelo" y arrastra las líneas para crear las relaciones:
     - `Fact_Ventas[ProductoID]` a `Dim_Producto[ProductoID]`
     - `Fact_Ventas[ClienteID]` a `Dim_Cliente[ClienteID]`
     - `Fact_Ventas[Fecha]` a `Dim_Fecha[Fecha]`

## Conclusión
Al finalizar este ejercicio, se habrá practicado la creación de un modelo en estrella, separando datos en tablas de hechos y dimensiones, estableciendo claves primarias y foráneas, y configurando las relaciones necesarias para un análisis eficaz en Power BI.
