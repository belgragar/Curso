# EJERCICIO 09: FÓRMULAS Y FUNCIONES DE TEXTO, LÓGICAS Y ASISTENCIA CON IA

## 🟢 Nivel básico — Normalización de una base de clientes

Una empresa ha importado un listado de clientes desde un sistema antiguo. Los datos presentan problemas de formato que deben corregirse antes de incorporarlos al sistema comercial.

Utilizando la tabla proporcionada:

```text
ID	Cliente_Bruto	Código	Facturación (€)
Cli-001	  ANA MARTÍNEZ LÓPEZ  	cli-001	52430
Cli-002	  PEDRO GARCÍA RUIZ	CLI-002	28750
Cli-003	MARTA  SÁNCHEZ  FERNÁNDEZ  	Cli-003	73500
Cli-004	  LUIS PÉREZ MARTÍN	Cli-004	41800
Cli-005	LAURA  GÓMEZ  DÍAZ 	CLI-005	19650
Cli-006	   JAVIER RODRÍGUEZ SOTO	cli-006	68500
Cli-007	ELENA MARTÍN  GARCÍA  	CLI-007	31200
Cli-008	  CARLOS FERNÁNDEZ LÓPEZ	cli-008	82400
Cli-009	  SANDRA  MORENO  VÁZQUEZ  	Cli-009	47250
Cli-010	DANIEL  NAVARRO  ROMERO	CLI-010	25900
Cli-011	  PATRICIA  TORRES GIL  	cli-011	55800
Cli-012	ALBERTO  RAMOS  CASTRO	Cli-012	34900
Cli-013	   ISABEL HERRERA  MOLINA	CLI-013	91500
Cli-014	RAÚL  ORTEGA  PRIETO  	cli-014	29500
Cli-015	  CRISTINA  IGLESIAS REY	Cli-015	62100
```

1. Elimine los espacios sobrantes de la columna **Cliente_Bruto** mediante **ESPACIOS()**.
2. Cree una columna **Cliente** convirtiendo el nombre al formato correcto con **NOMPROPIO()**.
3. Cree una columna **Código_MAY** con el identificador completamente en mayúsculas mediante **MAYUSC()**.
4. Cree una columna **Código_min** con el identificador completamente en minúsculas mediante **MINUSC()**.

**Funciones utilizadas**

* ESPACIOS
* NOMPROPIO
* MAYUSC
* MINUSC

---

## 🟡 Nivel intermedio — Construcción de textos

La empresa necesita generar textos descriptivos para un informe automático.

Cree una columna denominada **Resumen** con el siguiente formato:

```text
Cliente: Ana Martínez López | Facturación: 52.430 €
```

Utilice la función **CONCAT()**.

A continuación, genere exactamente el mismo resultado utilizando **UNIRCADENAS()**.

Compare ambas soluciones e indique cuál considera más legible.

**Funciones utilizadas**

* CONCAT
* UNIRCADENAS

>Va a haber un problema con el separador de miles. Para que el resultado sea el esperado habrá que usar la función **TEXTO()**
>- =CONCAT(
    "Cliente: ", F2,
    " | Facturación: ",
    TEXTO(D2; "#.##0 €")
)
>- =UNIRCADENAS(
    "";
    VERDADERO;
    "Cliente: "; F2;
    " | Facturación: ";
    TEXTO(D2; "#.##0 €")
)

---

## 🔴 Nivel avanzado — Clasificación automática de clientes

Clasifique cada cliente según su facturación utilizando **SI.CONJUNTO()**:

| Facturación | Categoría  |
| ----------- | ---------- |
| ≥ 70.000 €  | Premium    |
| ≥ 50.000 €  | Preferente |
| ≥ 30.000 €  | Estándar   |
| < 30.000 €  | Básico     |

Después, cree una columna denominada **Acción_Comercial** utilizando **SI()**:

* Si el cliente es **Premium**, mostrar:

```text
Llamada del gestor comercial
```

* En cualquier otro caso:

```text
Seguimiento automático
```

**Funciones utilizadas**

* SI
* SI.CONJUNTO

---

## 🔴🔴 Reto profesional — Informe automático

Construya una única frase para cada cliente con el siguiente formato:

```text
El cliente Ana Martínez López ha facturado 52.430 € y pertenece a la categoría Preferente.
```

La frase deberá generarse automáticamente utilizando **UNIRCADENAS()** o **CONCAT()**, aprovechando las columnas calculadas en los ejercicios anteriores.

---

Así, los ejercicios quedan perfectamente alineados con la teoría impartida en el Día 2 y reservan funciones como `IZQUIERDA()`, `DERECHA()`, `EXTRAE()`, `HALLAR()` y `LARGO()` para el tema dedicado específicamente a la extracción y análisis de cadenas de texto.
