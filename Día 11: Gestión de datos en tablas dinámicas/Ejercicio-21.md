# Ejercicio 21: Gestión de datos en tablas dinámicas

En esta ocasión, trabajaremos con la empresa logística **"AsturExpress Artesanía S.L."**, encargada del transporte y entrega de las piezas artesanales de Asturias. Incorporamos dos campos de tipo fecha (`Fecha_Pedido` y `Fecha_Entrega`) para poder analizar el rendimiento logístico a través de múltiples tablas dinámicas y controles visuales (segmentadores y escalas de tiempo conectados).

---

## 1. Contexto de Negocio

**AsturExpress Artesanía S.L.** gestiona la logística de envíos para talleres de madera, cerámica, azabache y sidra por toda la Península Ibérica. La dirección necesita evaluar:

1. El volumen financiero y de paquetes gestionados por cada **Empresa de Transporte** contratada.
2. La eficiencia de las entregas según la **Provincia de Destino** y el estado final del envío (*Entregado*, *En tránsito*, *Incidencia*).
3. La evolución temporal de las expediciones.

Para ello, debes construir un pequeño **Cuadro de Mando (Dashboard)** compuesto por dos tablas dinámicas independientes conectadas y sincronizadas mediante **Segmentadores de datos** y una **Escala de tiempo**.

---

## 2. Conjunto de Datos (Dataset)

Copia el contenido del cuadro inferior, pégalo en la celda `A1` de una nueva hoja en Excel y conviértelo en una Tabla Oficial de Excel (utilizando el atajo `Ctrl + Q` o `Ctrl + T` según la versión). Asigna a la tabla el nombre **`T_EnviosArtesania`**.

```csv
ID_Envio;Fecha_Pedido;Fecha_Entrega;Taller_Origen;Provincia_Destino;Empresa_Transporte;Tipo_Pieza;Coste_Envio_EUR;Estado_Envio
ENV-201;02/01/2026;05/01/2026;Madera del Sueve;Asturias;Nacex;Talla Madera;12,50;Entregado
ENV-202;05/01/2026;09/01/2026;Alfarería Llamas;Madrid;Seur;Vaca Cerámica;18,20;Entregado
ENV-203;10/01/2026;12/01/2026;Azabaches Villaviciosa;Barcelona;MRW;Collar Azabache;8,50;Entregado
ENV-204;14/01/2026;18/01/2026;Cuchillería Taramundi;Galicia;Nacex;Navaja Tradicional;9,80;Entregado
ENV-205;01/02/2026;05/02/2026;Madera del Sueve;Sevilla;Seur;Madroñera;22,00;Entregado
ENV-206;03/02/2026;04/02/2026;Madreñería Caso;Asturias;MRW;Madreñas;11,00;Entregado
ENV-207;12/02/2026;;Azabaches Villaviciosa;Madrid;Nacex;Pulsera Azabache;14,50;Incidencia
ENV-208;15/02/2026;19/02/2026;Lana de los Ancares;Valencia;Seur;Manta Textil;16,00;Entregado
ENV-209;01/03/2026;03/03/2026;Cuchillería Taramundi;Asturias;MRW;Cuchillo Escultor;7,90;Entregado
ENV-210;05/03/2026;;Alfarería Llamas;Barcelona;Nacex;Vaso Escanciador;19,50;En tránsito
ENV-211;10/03/2026;14/03/2026;Madera del Sueve;Madrid;Seur;Arca Tallada;35,00;Entregado
ENV-212;18/03/2026;22/03/2026;Lana de los Ancares;Galicia;MRW;Chal de Lana;13,40;Entregado

```

---

## 3. Tareas a Resolver

1. **Creación de Vistas Paralelas (Tablas Dinámicas):**
* Crea una nueva hoja llamada **`Dashboard_Logistica`**.


* Inserta **dos Tablas Dinámicas independientes** basadas en la tabla `T_EnviosArtesania`:


* **Tabla Dinámica 1 (Rendimiento por Transporte):** Ubícala en la celda `A3`. Debe mostrar la `Empresa_Transporte` en *Filas* y el valor total (Suma) de `Coste_Envio_EUR` en *Valores*.


* **Tabla Dinámica 2 (Distribución por Estado y Destino):** Ubícala en la celda `D3`. Debe mostrar `Provincia_Destino` en *Filas*, `Estado_Envio` en *Columnas* y la *Cuenta* de `ID_Envio` en *Valores*.




2. **Inserción de Controles Visuales Interactivos:**
* Añade un **Segmentador de datos** (*Slicer*) para el campo `Estado_Envio`.


* Añade una **Escala de tiempo** (*Timeline*) vinculada al campo **`Fecha_Pedido`**.




3. **Personalización y Formato del Segmentador:**
* Cambia el formato del segmentador `Estado_Envio` para que muestre los botones en **3 columnas horizontales**.




4. **Sincronización mediante Conexiones de Informes:**
* Vincula el segmentador `Estado_Envio` y la escala de tiempo `Fecha_Pedido` a **ambas tablas dinámicas** para que al filtrar cualquier control, las dos tablas se actualicen al mismo tiempo.




5. **Verificación e Interacción:**
* Filtra la escala de tiempo para analizar los envíos correspondientes al mes de **Febrero 2026**.


* Selecciona el estado **"Entregado"** en el segmentador y comprueba la reactividad cruzada de ambas tablas.





---

## 4. Guía de Solución Paso a Paso

* **Paso 1: Crear las dos Tablas Dinámicas**
1. Selecciona cualquier celda de la tabla original `T_EnviosArtesania`.
2. Pestaña **Insertar > Tabla dinámica**. Elige ponerla en una *Nueva hoja de cálculo* y renombra esa pestaña como `Dashboard_Logistica`.


3. **Configurar Tabla Dinámica 1 (`A3`):**
* Arrastra `Empresa_Transporte` a **Filas**.


* Arrastra `Coste_Envio_EUR` a **Valores**. Asegúrate de cambiar la *Configuración de campo de valor* a **Suma** y aplica formato de Moneda con separador decimal `,` y separador de miles `.`.




4. Vuelve a la hoja de datos origen `T_EnviosArtesania`, pulsa **Insertar > Tabla dinámica**, pero esta vez selecciona *Hoja de cálculo existente*, especificando la celda `D3` de la hoja `Dashboard_Logistica`.
5. **Configurar Tabla Dinámica 2 (`D3`):**
* Arrastra `Provincia_Destino` a **Filas**.
* Arrastra `Estado_Envio` a **Columnas**.
* Arrastra `ID_Envio` a **Valores** (se configurará automáticamente como *Recuento de ID_Envio*).




* **Paso 2 y 3: Insertar y Formatear los Controles Visuales**
1. Haz clic en la **Tabla Dinámica 1** (celda `A3`).
2. Ve a la pestaña **Analizar tabla dinámica > Insertar segmentación de datos**. Selecciona la casilla `Estado_Envio` y pulsa *Aceptar*.


3. Haz clic de nuevo en la **Tabla Dinámica 1**, ve a **Analizar tabla dinámica > Insertar escala de tiempo** y marca `Fecha_Pedido`.


4. Haz clic sobre el panel flotante del segmentador de `Estado_Envio`. Ve a la pestaña contextual **Segmentación** de la cinta superior, busca la sección *Botones* y cambia el número de **Columnas a 3**. Ajusta el tamaño de la ventana horizontalmente para que quede limpia y legible.




* **Paso 4: Establecer Conexiones de Informes (Sincronización)**
1. Haz clic derecho sobre la cabecera del segmentador `Estado_Envio` y pulsa en **Conexiones de informes...**


2. En el cuadro desplegable, **marca las casillas de verificación de ambas tablas dinámicas** (Tabla dinámica 1 y Tabla dinámica 2) y pulsa *Aceptar*.


3. Haz clic derecho sobre la cabecera de la **Escala de tiempo** de `Fecha_Pedido`, entra en **Conexiones de informes...** y marca también las casillas de **ambas tablas dinámicas**.




* **Paso 5: Validación de Interactividad**
1. En el control de Escala de tiempo, selecciona el nivel de visualización en **MESES** y haz clic sobre **"FEB"** (Febrero de 2026).


2. En el segmentador horizontal de `Estado_Envio`, haz clic en **"Entregado"**.


3. Comprueba cómo la **Tabla 1** recalcula al instante la facturación de envíos entregados en febrero (MRW, Nacex, Seur) y la **Tabla 2** muestra exactamente qué provincias recibieron esos paquetes (Asturias, Galicia, Sevilla, Valencia).

