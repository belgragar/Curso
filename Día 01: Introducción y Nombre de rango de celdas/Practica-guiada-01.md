# DÍA 1 - GESTIÓN DE ENTORNOS Y FORMATOS

## 9. Práctica guiada: Gestión de pedidos de una empresa comercial

El objetivo es aprender a utilizar nombres de rangos, formatos personalizados y formato condicional sobre datos introducidos directamente en una hoja.

### Datos de partida

Cambia el nombre de la hoja a: `Practica_Dia1`

```tsv
Código	Cliente	Comercial	Categoría	Unidades	Precio Unitario (€)	Descuento (%)	Estado	Stock	Stock Mínimo
1001	Alfa S.L.	Laura	Hardware	15	125,50	5	Pendiente	25	20
1002	Beta S.A.	Carlos	Software	8	320,00	0	Pagado	12	15
1003	Gamma S.L.	Laura	Hardware	35	18,90	10	Pendiente	45	30
1004	Delta S.A.	Ana	Consumibles	120	2,15	0	Pagado	350	200
1005	Épsilon S.L.	Miguel	Software	3	890,00	15	Pendiente	8	10
1006	Zeta S.L.	Carlos	Hardware	22	79,95	5	Enviado	30	25
1007	Eta S.A.	Laura	Consumibles	60	4,80	0	Pendiente	50	60
1008	Theta S.L.	Ana	Software	5	450,00	12	Pagado	16	12
1009	Iota S.L.	Miguel	Hardware	18	149,00	0	Pendiente	15	20
1010	Kappa S.A.	Carlos	Consumibles	95	3,20	8	Enviado	180	150
1011	Lambda S.A.	Laura	Software	6	610,00	5	Pendiente	7	8
1012	Mu S.L.	Ana	Hardware	28	95,75	10	Pagado	32	25
```

---

### Paso 1 — Preparar la hoja

Antes de comenzar los cálculos:

1. Selecciona la fila de encabezados `A1:J1`.
2. Aplica **negrita**.
3. Ajusta el ancho de las columnas para que los encabezados sean visibles.
4. Aplica un formato de fecha o número solo cuando sea necesario.
5. No modifiques los valores originales de la tabla.

---

### Paso 2 — Crear un nombre de rango para el IVA

En una zona libre de la hoja, por ejemplo:

| Celda |   Contenido |
| ----- | ----------: |
| `O1`  | Tipo de IVA |
| `O2`  |        0,21 |

Selecciona la celda `O2`.

En el **Cuadro de nombres**, situado a la izquierda de la barra de fórmulas, escribe:

```text
Tipo_IVA
```

y pulsa **Enter**.

Comprueba que el nombre se ha creado correctamente mediante:

**Fórmulas > Administrador de nombres**.

---

### Paso 3 — Crear nombres para otros valores

Crea también los siguientes nombres:

| Celda | Valor | Nombre      |
| ----- | ----: | ----------- |
| `O4`  |  1500 | Limite_Alto |
| `O5`  |   300 | Limite_Bajo |

De esta forma tendrás tres valores que podrás utilizar en las fórmulas y reglas posteriores:

```text
Tipo_IVA
Limite_Alto
Limite_Bajo
```

---

### Paso 4 — Crear la columna Importe

Añade en `K1` el encabezado:

```text
Importe
```

En `K2`, calcula el importe de la primera operación:

```excel
=E2*F2
```

Utiliza el **controlador de relleno** para copiar la fórmula desde `K2` hasta `K13`.

Comprueba que cada fila calcula correctamente:

```text
Unidades × Precio Unitario
```

---

### Paso 5 — Crear la columna IVA

En `L1` escribe:

```text
IVA
```

En `L2`, utiliza el nombre de rango creado anteriormente:

```excel
=K2*Tipo_IVA
```

Copia la fórmula hasta `L13`.

Observa la diferencia entre:

```excel
=K2*L2
```

y:

```excel
=K2*Tipo_IVA
```

La segunda fórmula resulta más fácil de interpretar porque el nombre `Tipo_IVA` explica qué representa el valor utilizado.

---

### Paso 6 — Crear la columna Total

En `M1` escribe:

```text
Total
```

En `M2`, calcula:

```excel
=K2+M2
```

Copia la fórmula hasta `M13`.

Ahora tendrás:

```text
Importe + IVA = Total
```

---

### Paso 7 — Crear un nombre para el total de ventas

Selecciona el rango:

```text
M2:M13
```

En el **Cuadro de nombres**, escribe:

```text
Ventas_Totales
```

Pulsa **Enter**.

En una celda libre, por ejemplo `O8`, escribe:

```excel
=SUMA(Ventas_Totales)
```

Comprueba que Excel calcula el total de todas las operaciones.

### Paso 8 — Aplicar formatos personalizados

Ahora vas a modificar únicamente la **forma en que se muestran los datos**, sin cambiar sus valores.

#### Código

Selecciona `A2:A13`.

Pulsa:

**Ctrl + 1 > Número > Personalizada**

Utiliza:

```text
00000
```

Comprueba que, por ejemplo:

```text
1001
```

se muestra como:

```text
01001
```

---

#### Precio, Importe, IVA y Total

Selecciona los rangos:

```text
F2:F13
K2:K13
L2:L13
M2:M13
```

Aplica el formato personalizado:

```text
#.##0,00 €;[Rojo]-#.##0,00 €;"-"
```

Comprueba especialmente qué ocurre cuando el valor es positivo, negativo o cero.

> **Recuerda:** aplicar este formato no cambia el valor almacenado en la celda.

---

#### Descuento

Selecciona `G2:G13`.

Aplica un formato adecuado para mostrar los descuentos como porcentajes:

```text
0%
```

---

### Paso 9 — Formato condicional para pedidos pendientes

Ahora vas a utilizar el formato condicional para crear una alerta visual.

Selecciona todo el rango:

```text
A2:M13
```

Ve a:

**Inicio > Formato condicional > Nueva regla > Utilice una fórmula para determinar las celdas para aplicar formato.**

Escribe:

```excel
=$H2="Pendiente"
```

Aplica un **relleno amarillo claro**.

Comprueba que las filas correspondientes a pedidos pendientes se resaltan automáticamente.

> Observa la referencia `$H2`:
>
> * `$H` mantiene fija la columna Estado.
> * `2` permite que Excel cambie la fila al evaluar cada registro.

---

### Paso 10 — Detectar productos con stock insuficiente

Selecciona:

```text
A2:M13
```

Crea una nueva regla de formato condicional mediante fórmula:

```excel
=$I2<$J2
```

Aplica:

* Fuente roja.
* Negrita.

La regla debe comprobar:

```text
Stock < Stock Mínimo
```

---

### Paso 11 — Destacar importes elevados

Selecciona:

```text
K2:K13
```

Crea una nueva regla de formato condicional mediante fórmula:

```excel
=K2>Limite_Alto
```

Aplica un **relleno verde claro**.

De esta forma, cualquier importe superior al límite definido en `Limite_Alto` quedará identificado visualmente.

---

### Paso 12 — Destacar importes bajos

Selecciona:

```text
K2:K13
```

Crea otra regla mediante fórmula:

```excel
=K2<Limite_Bajo
```

Aplica un **relleno rojo claro**.

Ahora la hoja permite identificar visualmente:

* Operaciones de importe elevado.
* Operaciones de importe bajo.
* Pedidos pendientes.
* Productos cuyo stock está por debajo del mínimo.

---



### Paso 13 — Comprobar la diferencia entre valor y formato

Selecciona una de las celdas de la columna `Total`.

Observa el valor que aparece en la **barra de fórmulas** y compáralo con la forma en que se muestra en la hoja.

Por ejemplo, un valor almacenado como:

```text
1520,5
```

puede mostrarse como:

```text
1.520,50 €
```

El formato ha cambiado la **apariencia**, pero no el valor utilizado internamente por Excel.

---

### Paso 14 — Comprobación final

Antes de finalizar, comprueba que tu hoja contiene:

* [ ] El nombre `Tipo_IVA`.
* [ ] El nombre `Limite_Alto`.
* [ ] El nombre `Limite_Bajo`.
* [ ] El nombre `Ventas_Totales`.
* [ ] La columna `Importe`.
* [ ] La columna `IVA`.
* [ ] La columna `Total`.
* [ ] Códigos con formato `00000`.
* [ ] Importes con formato monetario personalizado.
* [ ] Descuentos mostrados correctamente.
* [ ] Filas de pedidos pendientes resaltadas.
* [ ] Filas con stock insuficiente identificadas.
* [ ] Importes elevados resaltados.
* [ ] Importes bajos resaltados.
* [ ] Una suma final utilizando `=SUMA(Ventas_Totales)`.

> **Resultado esperado:** Al finalizar la práctica tendrás una hoja de cálculo convencional, con nombres de rangos, formatos personalizados y reglas de formato condicional que permiten convertir unos datos básicos en una herramienta de trabajo mucho más clara y automatizada.

