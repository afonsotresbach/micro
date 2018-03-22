Para todas as questões, considere que as variáveis `f`, `g`, `h`, `i` e `j` são do tipo inteiro (16 bits na arquitetura do MSP430), e que o vetor `A[]` é do tipo inteiro. Estas variáveis estão armazenadas nos seguintes registradores:

- f: R4
- g: R5
- h: R6
- i: R7
- j: R8
- A: R9

Utilize os registradores R11, R12, R13, R14 e R15 para armazenar valores temporários.

1. Traduza as seguintes linhas em C para a linguagem assembly do MSP430. Utilize somente as seguintes instruções: mov.w, add.w, sub.w, clr.w, dec.w, decd.w, inc.w e incd.w.

(a) `f *= 5;`
```
mov.w R4,  R11
add.w R4,  R4
add.w R4,  R4
add.w R11, R4
```

(b) `g *= 6;`
```
add.w R5,  R5
mov.w R5,  R11
add.w R5,  R5
add.w R11, R5
```

(d) `A[2] = 6*A[1] + 5*A[0];`
```
mov.w 1(R9), 2(R9)
add.w 1(R9), 1(R9)
add.w 1(R9), 1(R9)
add.w 1(R9), 2(R9)
add.w 1(R9), 2(R9)
add.w 0(R9), 2(R9)
add.w 2(R9), 2(R9)
add.w 2(R9), 2(R9)
add.w 0(R9), 2(R9)
```


(e) `A[3] = 3*f - 5*h;`
```
mov.w R4, 3(R9)
add.w R4, 3(R9)
add.w R4, 3(R9)
sub.w R6, 3(R9)
sub.w R6, 3(R9)
sub.w R6, 3(R9)
```


(f) `A[5] = 6*(f - 2*h);`
```
mov.w R4, 5(R9)
sub.w R6, 5(R9)
sub.w R6, 5(R9)
add.w 5(R9), 5(R9)
mov.w 5(R9), R11
add.w 5(R9), 5(R9)
add.w R11, 5(R9)
```
