# Processo Seletivo

## Introdução

A ITAbits é uma iniciativa de computação. Computação é um meio de resolver problemas, 
implementar melhorias ou até mesmo criar entretenimento, usando computadores para fazer o trabalho pesado por nós. 
Mas os computadores são máquinas, logo eles são burros. Para ensinar o computador a fazer as ações que desejamos, 
temos que ensinar detalhadamente todos os passos que ele deve executar. Para isso, usamos a programação, 
que é um meio de dizermos ao computador aquilo que queremos que ele faça.

Porém, existem diversas maneiras de se obter um resultado. Chamamos de **algoritmo** o conjunto **finito** de instruções **bem definidas** que temos que executar para realizar uma ação.

Por exemplo, temos um algoritmo simples para abrir uma porta:
```
* Instrução 1 – Verifique se a porta está trancada. Se não estiver, pule para a Instrução 4;
* Instrução 2 – Insira a chave correta na fechadura da porta;
* Instrução 3 – Gire a chave uma vez no sentido horário e volte para a instruooção 1;
* Instrução 4 – Gire a maçaneta no sentido anti-horário até o fim;
* Instrução 5 – Puxe a porta na sua direção;
```

> Poderíamos aumentar o nível de detalhe desse algoritmo o quanto quisermos, mas acho que você já entendeu a ideia.  

## Diferentes algoritmos para o mesmo problema

Existem diferentes maneiras de se resolver um problema. Um bom exemplo disso é o jogo de adivinhação.
Nesse jogo, diz-se que existe um número secreto entre 1 e 1000000, e temos que descobrir qual é o número secreto.
Ao dar um palpite, é nos informado se acertamos nosso palpite, se nosso palpite foi menor que o número secreto ou se ele foi maior que o número secreto.

Vamos agora ver dois algoritmos que resolvem esse desafio:

### Algoritmo 1 - Não tão eficiente assim

```
* Instrução 1 - Palpite o número 1
* Instrução 2 - Verificar se o palpite foi correto. Se for, fim do algoritmo.
* Instrução 3 - Palpite o número que foi palpitado anteriormente somado de 1.
* Instrução 4 - Volte para a Instrução 2.
```

Com esse algoritmo, suponha que o número secreto é 5000. Ele entraria na instrução 1 e palpiratia o número 1 e seguiria para a instrução 2.
Como 1 não é igual a 5000, na instrução 2 não é chamado o fim do algoritmo e seguiríamos para a instrução 3.
Na instrução 3, palpitaríamos o palpite anterior (que é 1), somado de 1, resultando no palpite do número 2. E seguimos para a instrução 4.
Na instrução 4, voltaríamos para a instrução 2 e verificaríamos a veracidade do nosso palpite. Como 2 não é igual a 5000, seguiríamos para a instrução 3 e palpitaríamos agora o número 3.

Perceba que demoraríamos 5000 palpites para acertar o valor do nosso número secreto, e não estamos também usando a informação de que nossos palpites são maiores ou menores que o número secreto pois nesse caso, a gente sempre palpita o menor número possível.
Com esse algoritmo, se o número secreto for 9999999, demoraríamos bastante para ganhar o jogo.

Vamos ver agora um algoritmo mais eficiente.

### Algoritmo 2 - Um pouco mais eficiente

```
* Instrução 1 - Nomear o valor 1 como mínimo e o valor 1000000 como máximo.

``` 



