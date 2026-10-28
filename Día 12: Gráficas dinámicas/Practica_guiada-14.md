# Práctica guiada 14: BÚSQUEDAS MODERNAS VS. BÚSQUEDAS TRADICIONALES Y CUADROS DE MANDO DINÁMICOS

## 🟢 PASO 1 DE LA PRÁCTICA GUIADA: BÚSQUEDAS AVANZADAS Y PARÁMETROS POCO EXPLORADOS

> **Instrucciones para el alumno:**
> 1. **Búsqueda hacia la izquierda:** En la celda **H2**, escribe el cliente `LogisSpain`. En **I2**, recupera su `ID_Operacion` (columna A) situando la columna de búsqueda a la derecha de la de devolución:
>    `=BUSCARX(H2; D2:D7; A2:A7; "No existe")`
> 2. **Extracción multicolumna en una sola fórmula:** En la celda **H5**, escribe `OP-103`. En **I5**, extrae de forma simultánea el `Comercial`, `Provincia`, `Cliente` e `Importe` seleccionando un rango amplio en la matriz de devolución:
>    `=BUSCARX(H5; A2:A7; B2:E7; "No existe")`
> 3. **Búsqueda en orden inverso (`modo_busqueda = -1`):** La comercial *"Ana Martín"* tiene dos operaciones (`OP-101` y `OP-106`).
>    * En **I7** (Primera venta): `=BUSCARX("Ana Martín"; B2:B7; E2:E7; 0; 0; 1)` *(Devuelve 12.500 €)*.
>    * En **I8** (Última venta actualizada): `=BUSCARX("Ana Martín"; B2:B7; E2:E7; 0; 0; -1)` *(Devuelve 18.200 €)*.
> 4. **Búsqueda con comodines (`modo_coincidencia = 2`):** En **H11**, escribe `Norte*`. En **I11**, extrae el importe correspondiente a cualquier cliente que empiece por "Norte":
>    `=BUSCARX(H11; D2:D7; E2:E7; "No hallado"; 2)`

---

## 🟡 PASO 2 DE LA PRÁCTICA GUIADA: TRAMOS, POSICIÓN Y BÚSQUEDA BIDIRECCIONAL 2 EJES

> **Instrucciones para el alumno:**
> 1. **Cálculo de Comisión por Tramo (`-1`):** En **H14**, escribe la cifra `10.000 €`. En **I14**, calcula la tasa de comisión buscando en la tabla auxiliar de tramos (`K2:K4` e `L2:L4`):
>    `=BUSCARX(H11; K11:K13; L11:L13; "Sin tramo"; -1)` *(Devolverá 5%)*.
> 2. **Obtención de posición con `COINCIDIRX`:** En **I17**, determina en qué fila se encuentra la provincia `"Burgos"` dentro del rango `C2:C7`:
>    `=COINCIDIRX("Burgos"; C2:C7; 0)` *(Devolverá 3)*.
> 3. **Búsqueda Bidireccional 2 Ejes (Fila x Columna):**
>    Crea en el rango **N1:Q4** la siguiente matriz de ventas trimestrales:
>    
>    | | Trimestre 1 | Trimestre 2 | Trimestre 3 |
>    | --- | --- | --- | --- |
>    | **NorteTech** | 12.000 € | 15.000 € | 18.000 € |
>    | **DataCorp** | 4.500 € | 6.000 € | 8.000 € |
>    | **LogisSpain** | 20.000 € | 22.000 € | 25.000 € |
> 
>    En **O6** selecciona el cliente (`DataCorp`) y en **O7** selecciona el trimestre (`Trimestre 2`).
>    En **O8**, calcula la cifra de venta cruzada combinando dos `BUSCARX`:
>    `=BUSCARX(O7; O1:Q1; BUSCARX(O6; N2:N4; O2:Q4))` *(Devolverá 6.000 €)*.

---


## 🟠 PASO 3 DE LA PRÁCTICA GUIADA: CONSTRUCCIÓN DEL MINI-DASHBOARD DINÁMICO

> **Instrucciones para el alumno:**
> 1. En la celda **L17**, crea una **Lista desplegable** (Menú *Datos > Validación de datos > Lista*) con el origen `=B2:B6` (Lista de Comerciales).
> 2. En el rango **L19:M19**, crea una pequeña tabla de apoyo con los encabezados: `Concepto` y `Valor`.
> 3. En **L20**, escribe `Importe Venta`. En **M20**, introduce la fórmula de búsqueda vinculada al desplegable:
> `=BUSCARX(L17; B2:B6; E2:E6; 0)`
> 4. Selecciona el rango **L4:M5**, ve a la pestaña *Insertar* y crea un **Gráfico de Barras 2D** aplicando las pautas de diseño visual del Día 07 (título claro, eliminación de líneas de cuadrícula innecesarias, color corporativo).
> 5. **Prueba final:** Cambia el comercial en el desplegable de la celda **L2**. Verás cómo la fórmula actualiza el valor y el gráfico cambia de forma interactiva en tiempo real.

---

## 🔴 PASO 4 DE LA PRÁCTICA GUIADA: AUDITORÍA Y OPTIMIZACIÓN DE FÓRMULAS CON IA

> **Instrucciones para el alumno:**
> 1. Copia tu fórmula de búsqueda bidireccional de 2 ejes: `=BUSCARX(O7;O1:Q1;BUSCARX(O6;N2:N4;O2:Q4))`.
> 2. Abre una herramienta de Inteligencia Artificial (ChatGPT, Claude o Copilot).
> 3. Pega el siguiente *prompt* de auditoría:
>    > *"Analiza la siguiente fórmula de Excel: `=BUSCARX(O7;O1:Q1;BUSCARX(O6;N2:N4;O2:Q4))`. Explica paso a paso cómo evalúa la matriz interna y la matriz externa, verifica si las referencias requieren fijación con `$` para ser arrastrada y evalúa su rendimiento frente a una combinación `INDICE/COINCIDIR`."*
> 4. Copia las conclusiones analíticas devueltas por la IA en un cuadro de texto dentro de tu hoja.
