1. O que são sistemas embarcados?

São sistemas que utilizam processadores para fins específicos, em contraste com os computadores para fins gerais.

2. O que são sistemas microprocesssados?

São sistemas que contêm microprocessadores, juntamente com outros componentes como circuitos a depender da aplicação.

3. Apresente aplicações de sistemas embarcados: 

(a) para a indústria automotiva;
Computador de bordo, multimídia, controle de freios, sistema de alarme, sistema de navegação

(b) para eletrodomésticos;
Cálculo de água necessária e tempo de lavagem em máquinas de lavar roupas, controle de microondas, e para aparelhos em geral: programação de ativação/standby, comunicação por redes como bluetooth, wifi, etc.

(c) para automação industrial.
c) Braços robóticos, controle de esteiras, sistemas de segurança, 

4. Cite arquiteturas possíveis e as diferenças entre elas.

As duas arquiteturas clássicas para computadores são a de Von Neumann e de Harvard. A primeira propõe uma única unidade de memória, que se comunica com a CPU (utilizando um barramento de endereço e um de dados), para armazenar tanto programa quanto dados. A segunda propõe uma memória para dados e uma para programa, utilizando barramentos separados, de forma que a CPU pode se comunicar com ambas simultaneamente, trazendo mais eficiência.

5. Por que usamos o MSP430 na disciplina, ao invés de outro microcontrolador?

Esta plataforma é ideal para um estudante que está começando aprender sobre microprocessadores e microcontroladores por ter uma arquitetura razoavelmente simples, mas com alguns recursos muito convenientes, como circuito de alimentação e comunicação USB tanto para gravação, quanto para comunicação serial, um número razoável de portas de E/S e um conversor Análógico-Digital, o que possibilita o fácil interfaceamento com sensores e atuadores. Ele tem 3 timers, e pode realizar conversão Digital-Analógica, fornecendo saídas PWM. As 4 alternativas de clock possibilitam que ele seja utilizado tanto em modos de baixo consumo como em aplicações que exigem seu máximo poder de processamento. E o mais importante, todos seus recursos, como seus registradores internos, por exemplo, são facilmente acessados e controlados pelo programador, sem abstrações que, visando facilitar ao máximo seu uso por leigos, poderiam tornar mais difícil o uso por profissionais ou estudantes.
