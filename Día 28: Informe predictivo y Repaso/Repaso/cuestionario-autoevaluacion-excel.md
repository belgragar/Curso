# CUESTIONARIO DE AUTOEVALUACIÓN DE EXCEL (IFCT56)
## REPASO GENERAL: PESTAÑA A PESTAÑA Y HERRAMIENTAS CLAVE

Este cuestionario ha sido diseñado para que evalúes tu nivel de dominio técnico de Microsoft Excel 2021 antes de finalizar la sección de Excel del curso [127, 132]. Consta de **15 preguntas tipo test** estructuradas según el recorrido de la cinta de opciones y las herramientas analíticas estudiadas [71]. 

Al final de cada pregunta encontrarás la solución correcta, la pestaña donde se ubica la herramienta y una explicación detallada para consolidar tu aprendizaje.

---

### 1. PESTAÑA: ARCHIVO Y CONFIGURACIÓN DEL ENTORNO

#### **Pregunta 1**
Estás maquetando un libro de control presupuestario para tu organización y pretendes guardarlo de tal manera que actúe como un molde inicial "virgen". Al hacer doble clic en el archivo desde el Explorador de Windows, quieres que Excel abra de forma predeterminada una copia limpia e independiente (como "Libro1") para proteger el diseño y las fórmulas maestras de modificaciones accidentales. ¿Qué extensión de archivo debes seleccionar al guardar? [670, 680, 685]
*   a) `.xlsx`
*   b) `.xlsm`
*   c) `.xltx`
*   d) `.xlsb`

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **c) `.xltx`** [680, 685]
*   **Pestaña de configuración:** **Archivo > Guardar como** (menú desplegable de tipo de archivo) [671].
*   **Explicación:** La extensión `.xltx` corresponde a una **Plantilla de Excel** [670, 680]. Al abrir una plantilla con doble clic, Excel no abre el archivo original para editarlo directamente, sino que fabrica al vuelo una réplica nueva sin datos reales cargados [670, 685]. Esto garantiza la estandarización y evita la sobreescritura accidental de la plantilla maestra [669, 679].
</details>

---

### 2. PESTAÑA: INICIO, EDICIÓN Y FORMATOS

#### **Pregunta 2**
Deseas aplicar una regla de **Formato Condicional mediante fórmula** para pintar de color amarillo claro la **fila completa** de la tabla cuando el estado del pedido (columna H) sea igual a "Pendiente" [229, 230]. ¿Cómo debes escribir la referencia de celda en la fórmula lógica de la regla? [221, 230, 241]
*   a) `=$H$2="Pendiente"`
*   b) `=H2="Pendiente"`
*   c) `=$H2="Pendiente"`
*   d) `=H$2="Pendiente"`

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **c) `=$H2="Pendiente"`** [230, 241, 242]
*   **Ubicación:** **Inicio > Formato condicional > Nueva regla > Utilice una fórmula...** [219].
*   **Explicación:** Al fijar únicamente la columna mediante el signo del dólar (`$H`), le indicas a Excel que evalúe siempre el valor que se encuentre en la columna H a lo largo de toda la fila [230, 242]. Si no fijas la columna (`H2`), el formato condicional evaluará de forma relativa columna a columna, provocando que las celdas se pinten de manera errática e inconsistente [221].
</details>

#### **Pregunta 3**
¿Cuál es el significado del código de formato personalizado `#.##0,00 €;[Rojo]-#.##0,00 €;"-"` aplicado sobre una celda numérica? [217, 242]
*   a) Fuerza la aparición de decimales en rojo si el valor es positivo, pinta negro si es negativo y oculta los ceros.
*   b) Estructura la representación visual del número en cuatro secciones: Positivos (con dos decimales), Negativos (con signo menos y en color rojo), Ceros (mostrados como un guion corto) y regula el comportamiento del Texto.
*   c) Limita el número de caracteres válidos y cambia el valor real subyacente de la celda de forma operativa.
*   d) Aplica una macro automática para corregir errores de conversión en el valor.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Estructura la representación en secciones: Positivos; Negativos; Ceros; Texto** [217, 242].
*   **Ubicación:** **Inicio > Formato de número (Menú desplegable) > Más formatos de número > Categoría: Personalizada** (o mediante el atajo **Ctrl + 1**) [218].
*   **Explicación:** El formato personalizado avanzado en Excel se divide en un máximo de cuatro secciones separadas obligatoriamente por punto y coma (`;`): `POSITIVOS ; NEGATIVOS ; CEROS ; TEXTO` [217, 242]. El símbolo `#` representa dígitos significativos opcionales, mientras que el `0` fuerza la aparición obligatoria de caracteres o ceros de relleno [217]. Recuerda que el formato personalizado solo altera la visualización cosmética, no el valor numérico interno de cálculo [213, 221].
</details>

---

### 3. PESTAÑA: INSERTAR Y ARQUITECTURA DE DATOS

#### **Pregunta 4**
Has convertido una lista convencional de datos en una **Tabla Estructurada de Excel (ListObject)** [293, 296, 307]. ¿Qué ocurre con un gráfico o una fórmula resumen de tipo `=SUMA(Tbl_Ventas[Importe])` cuando el usuario introduce un nuevo registro en la fila inmediatamente inferior a la última de la tabla? [294, 302, 304, 327]
*   a) El gráfico se rompe arrojando un error de rango no válido (`#¡REF!`) y la fórmula deja de calcular.
*   b) La tabla se expande automáticamente incorporando la nueva fila, y el gráfico y la fórmula se actualizan de inmediato al reconocer el nuevo registro transaccional de forma dinámica.
*   c) Debes acceder al menú de diseño y modificar manualmente los rangos de celdas para incluir la nueva fila.
*   d) La tabla dinámica asociada se actualiza inmediatamente sin necesidad de presionar ningún botón de refresco.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) La tabla se expande automáticamente y el gráfico y la fórmula se actualizan de inmediato** [294, 304, 327, 344].
*   **Ubicación:** **Insertar > Tabla** (o mediante la combinación de teclas **Ctrl + Q**) [298].
*   **Explicación:** Al convertir un rango en Tabla Estructurada, Excel pasa de tratar las celdas como posiciones abstractas a procesarlas como un objeto dinámico inteligente [296, 304]. Las fórmulas que utilizan referencias estructuradas (como nombres de columna entre corchetes `[Importe]`) y los gráficos vinculados se adaptan automáticamente al tamaño físico real que vaya tomando la tabla, eliminando el error humano de actualización manual [300, 304, 344].
</details>

---

### 4. PESTAÑA: FÓRMULAS, TEXTO Y MATRICES DINÁMICAS

#### **Pregunta 5**
Estás realizando operaciones matemáticas complejas en **Excel 2021** extrayendo números de códigos internos mediante funciones de texto como `EXTRAE`, `IZQUIERDA` o `DERECHA` [638, 653]. Al intentar operar con dichos resultados, el sistema te devuelve el error `#¡VALOR!` o fallos en las funciones lógicas [645]. ¿A qué se debe esto y cómo se soluciona? [645, 665, 666]
*   a) Se debe a que las funciones de texto siempre devuelven texto; se soluciona envolviendo la extracción en la función `VALOR` para transformarla en un número real operativo.
*   b) Ocurre porque la celda de destino está protegida; se soluciona desmarcando el bloqueo en el editor de VBA.
*   c) El delimitador utilizado no es válido; se soluciona reemplazándolo por comillas simples.
*   d) Es un fallo del motor de matrices; se resuelve pulsando Ctrl + Alt + Supr para forzar el cálculo.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **a) Las funciones de texto devuelven texto; se soluciona envolviendo la extracción en `VALOR`** [645, 665, 666].
*   **Ubicación:** Perteneciente a la biblioteca de funciones de texto en la pestaña **Fórmulas** [645].
*   **Explicación:** Aunque los caracteres extraídos representen dígitos (como `"104"`), las funciones lógicas de texto los devuelven como tipo *String* (texto) [261, 645, 666]. Excel no puede realizar cálculos aritméticos sobre texto directo, arrojando el error `#¡VALOR!` [645, 665]. El uso de `=VALOR(...)` convierte la cadena alfanumérica en un número real apto para sumas, promedios y comparaciones directas [645, 666].
</details>

#### **Pregunta 6**
La comercial *Ana Martín* tiene varias operaciones en una tabla transaccional desordenada (las filas son OP-101 por 12.500 € y OP-106 por 18.200 €) [536, 540]. Si deseas realizar una consulta mediante la función moderna `BUSCARX` de Excel para obtener el importe correspondiente a su **última venta registrada**, ¿qué argumento opcional debes configurar y con qué valor? [539, 540, 564]
*   a) El argumento `[modo_coincidencia]` configurado en `2`.
*   b) El argumento `[modo_busqueda]` configurado en `-1` (búsqueda de último a primero).
*   c) El argumento `[si_no_encontrado]` escrito como "Última".
*   d) Es obligatorio usar la combinación clásica de `INDICE` + `COINCIDIRX` en orden inverso.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) El argumento `[modo_busqueda]` configurado en `-1`** [539, 540, 564].
*   **Ubicación:** Pestaña **Fórmulas > Búsqueda y referencia > BUSCARX** [539].
*   **Explicación:** Por defecto, `BUSCARX` rastrea la matriz de arriba hacia abajo (de primero a último, valor `1`) [539]. Al configurar el sexto parámetro de la función (`[modo_busqueda]`) con el valor `-1`, Excel inicia la búsqueda desde la última fila hacia arriba (de abajo a arriba), extrayendo dinámicamente la transacción más reciente sin necesidad de ordenar previamente la base de datos [539, 540, 564].
</details>

#### **Pregunta 7**
Has escrito la fórmula de matriz dinámica `=FILTRAR(Tbl_Ventas; Tbl_Ventas[Provincia]="Madrid")` en la celda **K5** [579, 649]. Deseas calcular de forma automatizada cuántos registros devuelve este informe dinámico, de modo que si el informe crece o se reduce al cambiar el origen de datos, la fórmula se autoajuste instantáneamente [579]. ¿Cuál es la sintaxis correcta a utilizar? [579, 649, 665]
*   a) `=CONTARA(K5)`
*   b) `=CONTARA(K5:K1000)`
*   c) `=CONTARA(K5#)`
*   d) `=CONTARA(K5:N5)`

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **c) `=CONTARA(K5#)`** [579, 649, 665]
*   **Ubicación:** Pestaña **Fórmulas** (u Operador de rango derramado) [649].
*   **Explicación:** El símbolo almohadilla colocado inmediatamente después de la celda de origen (`K5#`) es el **operador de derrame o desbordamiento** [649, 665, 666]. Le indica a Excel que haga referencia no a la celda individual, sino a **toda la matriz derramada** que nace en esa celda [579, 649, 665]. Si la matriz dinámica cambia de tamaño (se expande o reduce), la referencia `#` se redimensiona automáticamente, evitando errores de rangos estáticos [649].
</details>

#### **Pregunta 8**
Escribes una fórmula matricial moderna en la celda J2 y, de repente, Excel bloquea toda la visualización mostrando el error `#¡DESBORDE!` (o `#SPILL!` en inglés) [580, 626, 635]. ¿Cuál es la causa técnica de este problema y cómo se soluciona de forma inmediata? [580, 635, 796, 816]
*   a) Ocurre cuando hay una división por cero en el modelo de cálculo; se soluciona envolviendo la fórmula con la función `SI.ERROR`.
*   b) Se debe a que hay datos escritos, celdas combinadas o texto estático bloqueando físicamente el rango de celdas que la matriz dinámica necesita para expandirse; se soluciona liberando y limpiando de inmediato ese espacio [580, 635, 816].
*   c) Es provocado por un bucle circular de fórmulas que se leen a sí mismas; se corrige activando el cálculo iterativo en opciones.
*   d) Significa que tu ordenador carece de la memoria física suficiente; se soluciona reduciendo el tamaño del archivo original.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Datos o celdas combinadas bloqueando el rango de expansión; se soluciona liberando el espacio** [580, 635, 816].
*   **Ubicación:** Cualquier celda del lienzo que reciba una matriz dinámica derramada [579, 580].
*   **Explicación:** Las matrices dinámicas modernas generan múltiples resultados que se expanden automáticamente por las celdas vecinas (derrame) [573, 626, 627]. Por seguridad para no sobrescribir información del usuario, si hay algún elemento escrito en las celdas de desborde, Excel detiene el cálculo y arroja el error `#¡DESBORDE!` [580, 626]. Al limpiar el área marcada por el borde tenue, el informe se dibuja al instante [580, 635].
</details>

---

### 5. PESTAÑA: DATOS, PROCESOS ETL Y SIMULACIÓN

#### **Pregunta 9**
¿Cuál es una ventaja operativa crítica de realizar la importación y limpieza de un archivo de facturación en formato CSV a través de **Power Query** en lugar de realizarla manualmente con fórmulas tradicionales de Excel? [745, 748, 815]
*   a) Power Query modifica directamente el archivo físico de origen en el disco duro para corregir las erratas tipográficas.
*   b) Power Query funciona en modo de solo lectura sobre el archivo original y registra cada acción de limpieza en un historial de "Pasos Aplicados" en código M, permitiendo procesar lotes nuevos de miles de filas con un solo clic en "Actualizar" [731, 735, 745, 748, 815].
*   c) Power Query inserta de forma invisible una macro en VBA para ocultar los errores al usuario final.
*   d) Power Query desactiva de forma automática la protección de la hoja para que puedas editar los datos en vivo.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Solo lectura, registra pasos aplicados en código M y se actualiza con un solo clic** [731, 735, 745, 748, 815].
*   **Ubicación:** **Datos > Obtener y transformar datos > Obtener datos > Desde un archivo > Desde texto/CSV** [737].
*   **Explicación:** Power Query actúa como una barrera de saneamiento no destructiva que nunca altera el archivo original [735, 788]. Cada transformación se graba en un flujo ETL (Pasos Aplicados) en lenguaje M [731, 744, 745]. Al recibir un lote de datos nuevos de otra semana, el docente o usuario no repite el trabajo manual: Excel ejecuta toda la secuencia de limpieza en milisegundos con pulsar el botón "Actualizar" [733, 736, 745, 815].
</details>

#### **Pregunta 10**
Deseas evaluar el beneficio final estimado de un proyecto inmobiliario variando simultáneamente el Tipo de Interés del préstamo (por ejemplo, del 2% al 4,5% en filas) y el Plazo de amortización en meses (de 40 a 65 meses en columnas) para analizar toda una **matriz de alternativas** de un solo vistazo [695, 696]. ¿Qué herramienta de análisis de hipótesis de Excel es la idónea para este requerimiento? [687, 695, 696, 705]
*   a) Búsqueda de objetivos.
*   b) Tabla de datos de doble entrada.
*   c) El complemento Solver.
*   d) Controles de Formulario vinculados a la función `ELEGIR`.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Tabla de datos de doble entrada** [696, 705].
*   **Ubicación:** **Datos > Análisis de hipótesis > Tabla de datos...** [696].
*   **Explicación:** A diferencia de la Búsqueda de objetivos (que calcula de forma inversa una sola variable cambiante para una meta fija), la Tabla de datos de doble entrada (2D) es una herramienta de simulación y sensibilidad que calcula de golpe el impacto conjunto de dos variables cruzadas (fila x columna) sobre una fórmula clave [693, 695, 696, 705].
</details>

#### **Pregunta 11**
Has diseñado un cuadro para la optimización de los envíos logísticos de tu empresa agroalimentaria [423, 459]. El modelo cuenta con múltiples variables cambiantes (unidades a enviar) y restricciones estrictas (presupuesto máximo, capacidades de almacenamiento y no negatividad) [414, 423]. Has configurado el complemento **Solver** para resolverlo de forma lineal con el método *Simplex LP* [422, 429]. El directivo comercial te pide que guardes la solución óptima obtenida de forma persistente para poder compararla después con otras hipótesis en un informe consolidado [700, 725]. ¿Cuál es la mejor vía técnica para hacerlo? [700, 718, 725]
*   a) Copiar los números óptimos de Solver, pegarlos como valores estáticos en otra pestaña y rehacer el gráfico.
*   b) Guardar el archivo como formato binario de Excel `.xlsb`.
*   c) Hacer clic en el botón "Guardar escenario" dentro del cuadro final de resultados de Solver para registrar la solución óptima en el Administrador de escenarios [700, 718, 725].
*   d) Programar una macro en VBA que detenga el recálculo dinámico de la celda objetivo.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **c) Guardar la solución óptima de Solver directamente como un escenario** [700, 718, 725].
*   **Ubicación:** Pestaña **Datos > Análisis de hipótesis > Administrador de escenarios** (integrado directamente con el panel final de **Solver**) [421, 422, 698].
*   **Explicación:** Solver y el Administrador de escenarios cuentan con un vínculo técnico directo [700, 718]. Dado que Solver sobrescribe físicamente las celdas numéricas de la hoja al dar una solución, la opción "Guardar escenario" permite almacenar esa foto fija (por ejemplo, como `Solver1`) [700, 718]. Esto permite realizar nuevas búsquedas posteriores con otros parámetros y consolidar todas las soluciones óptimas lado a lado en un único "Informe Resumen" [700, 718].
</details>

---

### 6. PESTAÑA: PROGRAMADOR, CONTROLES DE FORMULARIO Y MACROS

#### **Pregunta 12**
Estás diseñando un formulario interactivo de consulta para que los comerciales de tu PYME emitan facturas de forma rápida [669, 681]. Has insertado un control de tipo **Cuadro combinado (menú desplegable)** para que seleccionen el cliente [674]. Si vinculas este control a la celda auxiliar **$B$2** de tu hoja de soporte, ¿qué tipo de valor escribirá Excel automáticamente en esa celda de vínculo al seleccionar la opción que ocupa la tercera posición de la lista? [674, 684]
*   a) Escribirá el nombre de texto plano del cliente seleccionado.
*   b) Escribirá el número entero `3` (que representa la posición física de la opción elegida en el rango de entrada) [674, 684].
*   c) Devolverá el valor booleano `VERDADERO`.
*   d) Arrojará el error `#¡VALOR!` al no tratarse de una celda con fórmula.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Escribirá el número entero `3` (posición física en la lista)** [674, 684].
*   **Ubicación:** **Programador > Insertar > Controles de formulario > Cuadro combinado** [673, 674].
*   **Explicación:** A diferencia de una validación de datos común que escribe texto, el Cuadro combinado de formulario almacena en la celda de vínculo la posición ordinal (índice 1, 2, 3...) del elemento seleccionado [674]. Para "traducir" ese número al nombre del cliente real, los analistas profesionales de tu PYME combinan la celda de vínculo con funciones lógicas y de referencia como `INDICE` o `ELEGIR` [668, 681, 682].
</details>

#### **Pregunta 13**
¿Qué diferencia de comportamiento técnico existe entre una **Casilla de verificación (Checkbox)** y un **Botón de opción (Radio Button)** al configurar celdas de vínculo en un formulario de Excel? [675]
*   a) La Casilla de verificación devuelve un número entero y el Botón de opción devuelve texto plano.
*   b) La Casilla de verificación actúa de forma independiente devolviendo valores booleanos (`VERDADERO` o `FALSO`), mientras que los Botones de opción son de selección exclusiva y devuelven el número de orden de la opción marcada dentro de su grupo [675].
*   c) No existe ninguna diferencia; ambos controles requieren macros habilitadas en VBA para poder escribir datos.
*   d) El botón de opción solo funciona si se vincula a una base de datos externa de Microsoft Access.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) La Casilla es independiente (VERDADERO/FALSO) y los Botones son excluyentes por grupo (número ordinal)** [675].
*   **Ubicación:** **Programador > Insertar > Controles de formulario** [673, 675].
*   **Explicación:** Las casillas de verificación son controles binarios individuales (puedes marcar varias a la vez en una lista) [675]. Los botones de opción representan alternativas mutuamente excluyentes (si marcas una opción, se desmarca el resto de ese bloque) [675]. Para aislar bloques de botones de opción en un mismo formulario, se deben dibujar previamente recuadros de **Cuadro de grupo (Marco)** [675, 676].
</details>

#### **Pregunta 14**
Escribes un prompt para que una Inteligencia Artificial te redacte el código de una macro avanzada de depuración y limpieza masiva en Excel [763, 764, 773]. ¿Por qué es fundamental que solicites a la IA que incluya la instrucción `Application.ScreenUpdating = False` al inicio de la macro? [710, 781, 782]
*   a) Porque detiene el cálculo de la hoja para que las fórmulas se conviertan en texto plano de forma permanente.
*   b) Porque congela temporalmente la pantalla de Excel durante la ejecución de la macro, eliminando el molesto parpadeo visual y acelerando la velocidad de procesamiento del ordenador hasta un 500% [781, 782].
*   c) Impide que usuarios sin contraseña puedan acceder al código fuente guardado en el Editor de VBA.
*   d) Es la orden obligatoria de VBA para guardar el archivo con la extensión segura `.xlsm`.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Elimina el parpadeo visual y acelera significativamente la velocidad de procesamiento** [781, 782].
*   **Ubicación:** Editor de VBA (**ALT + F11**) [768].
*   **Explicación:** Por defecto, cada vez que una macro modifica el valor de una celda, Excel redibuja visualmente la pantalla [781]. En macros de limpieza masiva que recorren miles de filas, este constante redibujado causa un parpadeo constante y ralentiza enormemente el ordenador [782]. Desactivar el refresco visual con `ScreenUpdating = False` acelera drásticamente el proceso al realizar la transformación en la memoria interna del sistema [781, 782].
</details>

#### **Pregunta 15**
Has grabado y programado con ayuda de la IA varias macros excelentes para automatizar tu trabajo diario de administración [764, 774]. Al guardar tu libro de Excel, seleccionas por inercia el formato convencional de hoja de cálculo de toda la vida (`.xlsx`) [765, 782]. ¿Qué ocurrirá con tus macros al cerrar y volver a abrir el archivo? [765, 782, 784]
*   a) Las macros se comprimen en una base de datos segura y se reactivan automáticamente al pulsar F5.
*   b) Excel eliminará de forma irreversible y permanente todo el código de programación y las macros grabadas sin dar ninguna posibilidad de recuperarlas [765, 782, 784].
*   c) El archivo cambia de icono y requiere abrirse a través de la pestaña de Power Query para funcionar.
*   d) Excel te obligará a registrar una cuenta de programador de pago de Microsoft.

<details>
<summary><b>Ver Solución, Pestaña y Explicación</b></summary>

*   **Respuesta correcta:** **b) Se elimina todo el código y las macros de forma irreversible y permanente** [765, 782, 784].
*   **Pestaña de guardado:** **Archivo > Guardar como** [772].
*   **Explicación:** Los archivos tradicionales con extensión `.xlsx` no tienen soporte técnico para almacenar scripts de código ejecutable [765, 780]. Si se intenta guardar un libro con macros bajo este formato, Excel avisará de la pérdida de compatibilidad; si el usuario acepta y cierra, todo el trabajo de programación se perderá para siempre [765, 782, 784]. Para conservar el código, es estrictamente obligatorio seleccionar el formato **Libro de Excel habilitado para macros (`.xlsm`)** [765, 772, 781].
</details>

---

## 📈 Tabla de Diagnóstico de Competencias
Suma tus aciertos y comprueba qué bloques temáticos dominas mejor y cuáles te conviene repasar antes de cerrar la asignatura:

*   **De 13 a 15 aciertos (Nivel Experto):** Dominas a la perfección tanto la cinta de opciones clásica como las herramientas dinámicas modernas de Excel 2021/365. Estás plenamente capacitado para ejercer como analista y automatizador de datos en entornos corporativos.
*   **De 9 a 12 aciertos (Nivel Avanzado):** Tienes un conocimiento muy sólido de Excel. Te sugerimos revisar las explicaciones de las preguntas falladas (especialmente en la lógica de desborde `#` o en la parametrización de las celdas de vínculo de formularios) para pulir detalles técnicos.
*   **Menos de 9 aciertos (Nivel en Desarrollo):** Conoces el funcionamiento general de las hojas de cálculo, pero necesitas asentar la diferencia conceptual entre herramientas tradicionales e interactivas de base de datos y simulación. Te recomendamos abrir tu libro de prácticas de laboratorio y volver a ejecutar paso a paso las guías del Día 10 y Día 13 para ganar seguridad.

---
*Este cuestionario ha sido desarrollado siguiendo estrictamente las directrices del manual oficial IFCT56 del SEPE para la evaluación del alumnado en la especialidad de Excel Avanzado y Power BI [127, 130].*