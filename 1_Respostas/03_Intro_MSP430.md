1. Dada uma variável `a` do tipo `char` (um byte), escreva os trechos de código em C para:

(a) Somente setar o bit menos significativo de `a`.

`a |= BIT0;`

(b) Somente setar dois bits de `a`: o menos significativo e o segundo menos significativo.

`a |= BIT1 | BIT0;`

(c) Somente zerar o terceiro bit menos significativo de `a`.

`a &= ~BIT2;`

(d) Somente zerar o terceiro e o quarto bits menos significativo de `a`.

`a &= ~(BIT3 | BIT2);`

(e) Somente inverter o bit mais significativo de `a`.

`a ^= BIT7;`

(f) Inverter o nibble mais significativo de `a`, e setar o nibble menos significativo de `a`. 

```C
a ^= (BIT7 | BIT6 | BIT5 | BIT4);
a |= (BIT3 | BIT2 | BIT1 | BIT0);
```

2. Considerando a placa Launchpad do MSP430, escreva o código em C para piscar os dois LEDs ininterruptamente.

```C
#include <msp430g2553.h>
#define LEDS (BIT0 | BIT6)

void main(void)
{

    volatile unsigned int i;

    WDTCTL = WDTPW | WDTHOLD;
    P1OUT &= ~LEDS;
    P1DIR |= LEDS;

    while (1) {
        P1OUT ^= LEDS;

        for (i = 0xffff; i > 0; i--);
    }

}
```

3. Considerando a placa Launchpad do MSP430, escreva o código em C para piscar duas vezes os dois LEDs sempre que o usuário pressionar o botão.
```C
#include <msp430g2553.h>
#define LEDS (BIT0 | BIT6)
#define BTN BIT3

void main(void)
{

    volatile unsigned int i, j;

    WDTCTL = WDTPW | WDTHOLD;
    P1DIR |= LEDS;
    P1OUT &= ~LEDS;
    P1DIR &= ~BTN;
    P1REN |= BTN;

    while (1) {
        while (P1IN & BTN);

        for (j = 4; j > 0; j--) {
            P1OUT ^= LEDS;

            for (i = 0xc000; i > 0; i--);
        }
    }

}
```

4. Considerando a placa Launchpad do MSP430, faça uma função em C que pisca os dois LEDs uma vez.
```C
void pisca(unsigned int j)
{

    volatile unsigned int i;

    for (j *= 2; j > 0; j--) {
        P1OUT ^= LEDS;

        for (i = 0xffff; i > 0; i--);
    }
}
```

5. Reescreva o código da questão 2 usando a função da questão 4.
```C
#include <msp430g2553.h>
#define LEDS (BIT0 | BIT6)

void main(void)
{

    volatile unsigned int i;

    WDTCTL = WDTPW | WDTHOLD;
    P1OUT &= ~LEDS;
    P1DIR |= LEDS;

    pisca(1);

}
```

6. Reescreva o código da questão 3 usando a função da questão 4.
```C
#include <msp430g2553.h>
#define LEDS BIT0 | BIT6
#define BTN BIT3

void main(void)
{

    volatile unsigned int i;

    WDTCTL = WDTPW | WDTHOLD;
    P1DIR |= LEDS;
    P1OUT &= ~LEDS;
    P1DIR &= ~BTN;
    P1REN |= BTN;

    while (1) {
        while (P1IN & BTN);
        pisca(2);
        for (i = 0xc000; i > 0; i--);
    }

}
```
