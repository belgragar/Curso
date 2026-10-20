# Ejercicio 10: VISUALIZACIÓN Y TABLAS ESTRUCTURADAS

## 🟢 Nivel básico — Creación de una Tabla Estructurada

**Objetivo:** Convertir un rango convencional en una Tabla Estructurada y conocer sus principales características.

1. Crea la siguiente tabla:

```tsv
Código	Producto	Categoría	Precio (€)	Stock
P001	Teclado inalámbrico	Periféricos	35,00	42
P002	Ratón óptico	Periféricos	18,50	65
P003	Monitor 24"	Monitores	189,00	18
P004	Monitor 27"	Monitores	279,00	12
P005	Disco SSD 500 GB	Almacenamiento	59,90	35
P006	Disco SSD 1 TB	Almacenamiento	89,90	28
P007	Disco duro externo 1 TB	Almacenamiento	64,50	22
P008	Memoria USB 64 GB	Almacenamiento	12,90	85
P009	Webcam HD	Periféricos	45,00	31
P010	Altavoces 2.1	Audio	52,00	16
P011	Auriculares inalámbricos	Audio	69,90	27
P012	Micrófono USB	Audio	79,00	14
P013	Portátil básico	Equipos	649,00	9
P014	Portátil profesional	Equipos	1199,00	7
P015	Tablet 10"	Equipos	299,00	21
P016	Tablet 12"	Equipos	449,00	15
P017	Hub USB-C	Accesorios	29,90	38
P018	Mochila para portátil	Accesorios	39,50	44
P019	Base refrigeradora	Accesorios	32,00	19
P020	Alfombrilla gaming	Accesorios	24,90	56
```

2. Convierte el rango en una **Tabla Estructurada**.
3. Comprueba que la opción **"La tabla tiene encabezados"** está activada.
4. Cambia el nombre de la tabla por `Tbl_Productos`
5. Aplica un estilo de tabla distinto al predeterminado.
6. Activa las opciones:
   * Primera columna.
   * Última columna.
   * Filas con bandas.
7. Explica brevemente qué ventajas aporta trabajar con una Tabla Estructurada frente a un rango convencional.

---

## 🟡 Nivel intermedio — Referencias estructuradas y columnas calculadas

**Objetivo:** Utilizar referencias estructuradas para automatizar cálculos.

Sobre la tabla creada en el ejercicio anterior:

1. Añade las siguientes columnas:

* IVA
* Precio_Final
* Valor_Stock

2. Utiliza referencias estructuradas para calcular:

* IVA = 21 % del precio.
* Precio_Final = Precio + IVA.
* Valor_Stock = Precio_Final × Stock.

3. Comprueba que al escribir la primera fórmula Excel crea automáticamente una **columna calculada**.

4. Activa la **Fila de Totales**.

5. Configura la fila para mostrar:

* Suma del Valor_Stock.
* Promedio del Precio_Final.
* Recuento de productos.

6. Añade un nuevo producto al final de la tabla:

```tsv
P021	Cargador USB-C 65W	Accesorios	42,00	33
```
Comprueba que:

* La tabla se amplía automáticamente.
* Las fórmulas aparecen sin copiarlas.
* La fila de totales se actualiza automáticamente.

## 🟠 Nivel avanzado — Referencias estructuradas completas

**Objetivo:** Utilizar los distintos tipos de referencias estructuradas.

Partiendo de la tabla anterior:

1. Escribe una fórmula que obtenga la suma total de la columna **Valor_Stock** utilizando únicamente una referencia estructurada.
2. Crea una columna denominada **Comisión**.
3. Utiliza una fórmula similar a la siguiente para calcular una comisión del 5 % únicamente cuando el stock sea superior a 25 unidades.
        ```excel
        =SI([@Stock]>25;[@Precio_Final]*0,05;0)
        ```
4. Identifica en la fórmula:
   * Qué representa `@`.
   * Qué representa el nombre de la columna entre corchetes.
5. Crea una celda resumen fuera de la tabla que utilice una referencia estructurada para mostrar el total de existencias.
6. Cambia el nombre de la tabla por `Tbl_Inventario2026` y comprueba cómo se actualizan automáticamente todas las fórmulas.

---

## 🔴 Nivel experto — Automatización mediante Tablas

**Objetivo:** Comprobar el comportamiento dinámico de una Tabla Estructurada.

1. Inserta **15 nuevos registros** al final de la tabla:
```tsv
P022	Cámara de seguridad IP	Seguridad	89,00	18
P023	Router Wi-Fi 6	Redes	129,00	24
P024	Switch 8 puertos	Redes	68,50	32
P025	Adaptador USB-C	Accesorios	19,90	47
P026	Cable HDMI 2 m	Accesorios	14,50	72
P027	Cable de red 5 m	Redes	11,90	58
P028	Impresora multifunción	Impresión	159,00	13
P029	Tóner negro	Impresión	54,90	26
P030	Escáner documental	Impresión	219,00	8
P031	SAI 800 VA	Energía	99,00	17
P032	Regleta 6 tomas	Energía	28,50	41
P033	Disco SSD 2 TB	Almacenamiento	159,00	11
P034	Memoria USB 128 GB	Almacenamiento	21,90	63
P035	Teclado mecánico	Periféricos	79,90	29
P036	Ratón gaming	Periféricos	49,90	36
```
2. Comprueba que:
   * El formato se mantiene.
   * Las fórmulas aparecen automáticamente.
   * La fila de totales incorpora los nuevos datos.
3. Inserta una nueva columna denominada **Margen** entre Precio_Final y Valor_Stock.
4. Comprueba que las referencias estructuradas continúan funcionando sin modificar ninguna fórmula.
5. Elimina una columna que no sea necesaria y obserba cómo Excel adapta automáticamente las referencias restantes.
6. Explica por qué este comportamiento reduce los errores en hojas de cálculo empresariales.

---

## 🔴🔴 Reto profesional — Construcción de un Dashboard dinámico

La empresa desea disponer de un cuadro de mando que se actualice automáticamente conforme se registran nuevas operaciones comerciales.

Partiendo de la tabla **Tbl_Inventario2026** del proyecto integrador:

1. Crea una nueva hoja denominada **Dashboard_Síntesis**.
2. Muestra mediante referencias estructuradas los siguientes indicadores:
   * Número de operaciones.
   * Facturación total.
   * Facturación media.
   * Pedido de mayor importe.
   * Pedido de menor importe.
3. Inserta un gráfico de columnas que represente la facturación por categoría.
4. Personaliza el gráfico:
   * Título.
   * Etiquetas de datos.
   * Leyenda.
   * Estilo.
5. Añade **cinco nuevas operaciones** al final de la tabla.
6. Comprueba que:
   * La Tabla Estructurada se amplía automáticamente.
   * Las columnas calculadas continúan funcionando.
   * Los indicadores del Dashboard se actualizan.
   * El gráfico incorpora automáticamente las nuevas operaciones sin modificar su origen de datos.
7. Redacta una breve conclusión explicando por qué una empresa obtiene mayores ventajas utilizando Tablas Estructuradas que rangos tradicionales para construir informes y cuadros de mando.

