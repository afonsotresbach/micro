Para as questões 2 a 5, considere que as variáveis `f`, `g`, `h`, `i` e `j` são do tipo inteiro (16 bits na arquitetura do MSP430), e que o vetor `A[]` é do tipo inteiro. Estas variáveis estão armazenadas nos seguintes registradores:
	f: R4
	g: R5
	h: R6
	i: R7
	j: R8
	A: R9
Utilize os registradores R11, R12, R13, R14 e R15 para armazenar valores temporários.

1. Escreva os trechos de código assembly do MSP430 para:

(a) Somente setar o bit menos significativo de R5.

`bis.w #1, R5`

(b) Somente setar dois bits de R6: o menos significativo e o segundo menos significativo.

`bis.w #3, R5`

(c) Somente zerar o terceiro bit menos significativo de R7.

`bic.w #4, R7`

(d) Somente zerar o terceiro e o quarto bits menos significativo de R8.

`bic.w #C, R8`

(e) Somente inverter o bit mais significativo de R9.

`inv.w #8000, R9`

(f) Inverter o nibble mais significativo de R10, e setar o nibble menos significativo de R10. 

```
inv.w #f000, R10
bis.w #000f, R10
```

2. "Traduza" o seguinte trecho de código em C para o assembly do MSP430:

```C
if(i>j) f = g+h+10;
else f = g-h-10;
```

```
mov.w R5, R4
cmp R7, R8
jn i_maior_j
sub.w R6, R4
sub.w #A, R4
jmp continua
i_maior_j:
    add.w R6, R4
    add.w #a, R4
continua:
```
    
3. "Traduza" o seguinte trecho de código em C para o assembly do MSP430:

```C
while(A[i]!=j) i++;
```

```
mov.w R9, R11
while:
    cmp   @R11+, R8
    jn    end
    inc.w R7
    jmp   while
end:
```

4. "Traduza" o seguinte trecho de código em C para o assembly do MSP430:

```C
for(i=0; i<100; i++) A[i] = i*2;
```

```
clr.w R7
mov.w R9, R11
mov.w #64, R12

loop:
    cmp.w R7, R12
    jge   end
    mov.w R7, @R11
    add.w R7, @R11+
    inc.w R7
    jmp   loop
end:
```

5. "Traduza" o seguinte trecho de código em C para o assembly do MSP430:

```C
for(i=99; i>=0; i--) A[i] = i*2;
```

```
mov.w #63, R7
mov.w R9, R11
loop:
    tst   R7
    jn    end
    mov.w R7, @R11
    add.w R7, @R11+
    inc.w R7
    jmp   loop
end:
```
