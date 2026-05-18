<div align="center">

# N4RN14_0 // SYSTEM_BREACH

```txt
AUTH_REQUIRED: t474_r0b07
STATUS: CONNECTED
```

> "El sistema no cae por magia.
> Cae porque alguien asumió que 20 bytes eran suficientes."

</div>

---

## `[ ACCESS LOG ]`

```txt
TARGET: NARNIA0
PORT: 2226
VECTOR: BUFFER OVERFLOW
STATUS: BREACHED
CLASSIFICATION: EDUCATIONAL / MEMORY CORRUPTION
```

---

# `[ INTRO ]`

> “Otra vez buscando el walkthrough fácil.
> Otra vez esperando una flag masticada para sentirte hacker durante cinco minutos.

> El sistema está lleno de gente así.

> Copian payloads.
> Repiten comandos.
> Nunca entienden qué ocurrió realmente.

> Y después se preguntan por qué los explotan.”

---

# `[ RECON // EL BOCÓN ]`

```bash
ltrace ./narnia0
```

El binario habló demasiado.

```txt
Secret value: 0xdeadbeef
```

0xdeadbeef.

No es un valor aleatorio.

Si no sabes por qué existe,
investiga quién fue Jerry Saltzer.
Después vuelve.

---

<div align="center">

![RECON](./assets/recon_terminal.png)

</div>

---

# `[ BUFFER OVERFLOW // FÍSICA DE MEMORIA ]`

```c
char buf[20];
```

20 bytes.

Ese era el límite.

Pero el programador permitió 24.

La memoria no elimina el exceso.
Lo desplaza.

Los 4 bytes sobrantes caen directamente sobre `val`.

No es magia.
No es hacking cinematográfico.

Es física.

---

<details>
<summary>Ver modelo conceptual</summary>

<br>

<div align="center">

![OVERFLOW_MODEL](./assets/buffer_physics.png)

</div>

</details>

---

# `[ EXPLOIT // SIN INTERMEDIARIOS ]`

```bash
(python3 -c 'import sys; sys.stdout.buffer.write(b"A"*20 + b"\xef\xbe\xad\xde")'; cat) | ./narnia0
```

No copies el comando todavía.

Léelo.

Cada byte tiene un propósito.

---

## `sys.stdout.buffer.write`

Python intenta interpretar.

Nosotros no queremos interpretación.

Queremos bytes crudos.

Control directo sobre memoria.

---

## `b"A"*20`

20 bytes.

Ni uno menos.
Ni uno más.

---

## `b"\xef\xbe\xad\xde"`

0xdeadbeef.

Invertido.

Little Endian.

Si no entiendes por qué los procesadores almacenan los bytes en ese orden,
sigues observando la terminal desde afuera.

---

## `; cat`

Soporte vital.

Sin eso,
la shell muere antes de que puedas tocarla.

La puerta abre.

Y se cierra inmediatamente.

---

<div align="center">

![EXPLOIT](./assets/exploit_terminal.png)

</div>

---

# `[ ROOT // CONSECUENCIAS ]`

La flag no importa.

Nunca importó.

Lo importante es entender que un desborde de 4 bytes puede destruir:

- un proceso
- un sistema
- una misión espacial

Ariane 5.
1996.

Un desbordamiento.
Una conversión inválida.
370 millones de dólares cayendo del cielo.

La memoria no perdona errores optimistas.

---

<details>
<summary>¿Qué ocurrió realmente en Ariane 5?</summary>

<br>

Un valor de 64 bits fue forzado dentro de una variable de 16 bits.

El sistema heredó código del Ariane 4 bajo la suposición de que ciertos límites nunca serían superados.

La realidad no respetó esa suposición.

El sistema de navegación colapsó.

El cohete se autodestruyó 37 segundos después del lanzamiento.

</details>

---

# `[ FINAL SIGNAL ]`

```txt
[ SIGNAL LOST ]
0x52 0x4f 0x4f 0x54
```

> “La mayoría quiere herramientas.

> Pocos quieren comprender sistemas.

> Ahí es donde comienza la diferencia.”

---

<div align="center">

![CASEFILE](./assets/narnia_casefile.png)

</div>

---

# `[ STATUS ]`

```txt
ROOT ACCESS: GRANTED
SESSION: CLOSED
```

