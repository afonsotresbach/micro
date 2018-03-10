1. Quais as diferenças entre os barramentos de dados e de endereços?

Os barramentos de dados determinam a capacidade do processador, a quantidade de bits que ele consegue manipular, já o barramento de endereços pode conter mais ou menos bits, dependendo da memória utilizada. Além disso, o barramento de endereços é unidirecional, sendo utilizado pelo processador para selecionar o endereço de memória do qual serão lidos dados, ou no qual serão escritos.

2. Quais são as diferenças entre as memórias RAM e ROM?

A memória ROM é de somente leitura e não-volátil. Nela são armazenados programas (e dados constantes destes programas, como look-up tables). A memória RAM é volátil e serve para armazenar dados, que são tanto lidos quanto escritos.

3. Considere o código abaixo:

```C
#include <stdio.h>
int main(void)
{
	int i;
	printf("Insira um número inteiro: ");
	scanf("%d", &i);
	if(i%2)
		printf("%d eh impar.\n");
	else
		printf("%d eh par.\n");
	return 0;
}
```

Para este código, responda:
(a) A variável `i` é armazenada na memória RAM ou ROM? Por quê? 
A variável `i` é armazenada na memória de dados, que é do tipo RAM. Durante a execução do programa, a memória ROM é de somente leitura.

(b) O programa compilado a partir deste código é armazenado na memória RAM ou ROM? Por quê?
O programa compilado é armazenado na memória de programa, que é do tipo ROM, pois não deve ser volátil, para que o programa permaneça disponível quando o sistema é reiniciado. 

4. Quais são as diferenças, vantagens e desvantagens das arquiteturas Harvard e Von Neumann?

A diferença principal é a separação das memórias de programa e de dados, na arquitetura de Harvard, enquanto a de Von Neumann utiliza uma única memória compartilhada. A vantagem de se compartilhar um único espaço é que a proporção de dados e programa pode ser variada. Todo espaço não utilizado por programa pode ser utilizado para dados. Já na arquitetura de Harvard, a memória de programa que fica ociosa é de certa forma "desperdiçada". Porém, esta arquitetura apresenta a grande vantagem de permitir ao processador acessar tanto dados quanto programa simultaneamente, o que traz muita eficiência.

5. Considere a variável inteira `i`, armazenando o valor `0x8051ABCD`. Se `i` é armazenada na memória a partir do endereço `0x0200`, como ficam este byte e os seguintes, considerando que a memória é:
(a) Little-endian;
0x0200 CD
0x0201 AB
0x0202 51
0x0203 80

(b) Big-endian.
0x0200 80
0x0201 51
0x0202 AB
0x0203 CD

6. Sabendo que o processador do MSP430 tem registradores de 16 bits, como ele soma duas variáveis de 32 bits?

Cada variável de 32 bits, armazenada em ordem Little Endian, ocupa 2 registradores quando a soma é executada. Tomará duas instruções, primeiro somando o byte menos significativo, e depois somando o byte mais significativo com o carry da soma anterior.
