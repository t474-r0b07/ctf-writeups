```
██████╗  █████╗ ██████╗ ████████╗██╗██████╗  █████╗ ███████╗
██╔══██╗██╔══██╗██╔══██╗╚══██╔══╝██║██╔══██╗██╔══██╗██╔════╝
██████╔╝███████║██████╔╝   ██║   ██║██║  ██║███████║███████╗
██╔═══╝ ██╔══██║██╔══██╗   ██║   ██║██║  ██║██╔══██║╚════██║
██║     ██║  ██║██║  ██║   ██║   ██║██████╔╝██║  ██║███████║
╚═╝     ╚═╝  ╚═╝╚═╝  ╚═╝   ╚═╝   ╚═╝╚═════╝ ╚═╝  ╚═╝╚══════╝
```

```bash
$ whoami
> t474_r0b07

$ pwd
> /writeups/tryhackme
```

---

```bash
$ cat objective.txt
```

```text
this is not a flag collection.

this is a collection of positions.
```

---

## ♟ ¿Qué es esto?

TryHackMe está lleno de writeups.

Esta carpeta también contiene writeups.

Pero las máquinas aquí no se documentan como objetivos.

Se documentan como partidas.

No porque el ajedrez sea una metáfora elegante.

Porque resulta útil.

Cada servicio es una pieza.

Cada decisión modifica la posición.

Cada error deja algo sin defender.

---

```bash
$ cat rules.conf
```

```ini
[game]

flag != objective

root != victory

copy_paste = false

reasoning = required
```

---

## ♞ Metodología

```bash
$ tree methodology/
```

```text
methodology/

├── observation/
├── patterns/
├── hypothesis/
├── attempts/
├── mistakes/
└── checkmate/
```

No siempre aparecen en ese orden.

No todas las partidas recorren el mismo camino.

Pero casi todas pasan por alguno de esos directorios.

---

## ♝ Sobre las flags

```bash
$ cat flag.txt
```

```text
flags are easy to archive.

understanding takes longer.
```

La flag suele marcar el final del laboratorio.

No necesariamente el final de la investigación.

---

## ♜ Sobre los errores

```bash
$ grep learning attempts.log
```

```text
most useful data found in failed attempts
```

Las hipótesis equivocadas se conservan.

Los callejones sin salida también.

Porque muchas veces el aprendizaje aparece justo antes de abandonar una idea.

---

## ♛ Notación

```bash
$ cat notation.txt
```

```text
♟ opening

♞ exposed piece

♝ combination

♜ initiative

♛ exposed king

♚ checkmate
```

No todas las máquinas pierden igual.

No todas las partidas terminan por la misma razón.

---

## ♚ Observación

```bash
$ cat observation.log
```

```text
the king rarely falls
on the move that matters.

by the time you see checkmate,
the position is usually gone.
```

---

## Estado actual

```bash
$ tail -f progress.log
```

```text
🕐 PARTIDA_001    [░░░░░░░░░░]
🕐 PARTIDA_002    [░░░░░░░░░░]
🕐 PARTIDA_003    [░░░░░░░░░░]
🕐 PARTIDA_004    [░░░░░░░░░░]
🕐 PARTIDA_005    [░░░░░░░░░░]
```

---

```bash
$ cat first_move.txt
```

```text
every room looks complicated.

until you find the first move.
```

---

<details>
<summary><code>$ cat .hidden/board.dat</code></summary>

```text
r n b q k b n r
p p p p p p p p
. . . . . . . .
. . . . . . . .
. . . . . . . .
. . . . . . . .
P P P P P P P P
R N B Q K B N R
```

```text
all games start the same way.

they rarely end the same way.
```

</details>

---

```bash
$ exit
```

```text
root was never the story.

it was only the last move.
```
