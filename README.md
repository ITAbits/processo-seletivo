# Processo Seletivo - ITAbits

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

Com esse algoritmo, suponha que o número secreto é 62442. Ele entraria na instrução 1, chutaria o número 1 e seguiria para a instrução 2.
Como 1 não é igual a 62442, na instrução 2 não é chamado o fim do algoritmo e seguiríamos para a instrução 3.
Na instrução 3, chutaríamos o palpite anterior (que é 1) somado de 1, resultando no número 2 como novo palpite. E seguimos para a instrução 4.
Na instrução 4, voltaríamos para a instrução 2 e verificaríamos a veracidade do nosso palpite. Como 2 não é igual a 62442, seguiríamos para a instrução 3 e chutaríamos agora o número 3.

Perceba que demoraríamos 62442 palpites para acertar o valor do nosso número secreto e não estamos também usando a informação de que nossos palpites são maiores ou menores que o número secreto pois nesse caso, a gente sempre palpita o menor número possível.
Com esse algoritmo, se o número secreto for 9999999, demoraríamos bastante para ganhar o jogo.

Vamos ver agora um algoritmo mais eficiente.

### Algoritmo 2 - Um pouco mais eficiente

```
* Instrução 1 - Nomear o valor 1 como mínimo e o valor 1000000 como máximo.
* Instrução 2 - Palpitar a média aritmética ente o valor mínimo e o valor máximo (mínimo + máximo)/2, 
arredondar para baixo caso a divisão não seja inteira.
* Instrução 3 - Se o palpite for correto, finalizamos o o algoritmo. Se o nosso palpite for menor
que o número secreto, atualizamos o nosso valor mínimo para o nosso valor do palpite. 
Caso contrário, atualizamos o nosso valor máximo para o valor do palpite.
* Instrução 4 - Pule para a Instrução 2.

``` 
Agora com esse segundo algoritmo, vamos ver o que aconteceria se o número secreto for de novo 62442.
Inicialmente, nosso mínimo vale 1 e nosso máximo vale 1000000. Palpitaríamos inicialmente (1 + 1000000)/2 = 500000 arredondado para baixo. Como 500000 é maior que 62442, na instrução 3 atualizaríamos o nosso máximo para 500000. Voltaríamos para a instrução 2 agora com o valor mínimo sendo 1 e o máximo sendo 500000. Logo, nosso palpite será agora (1 + 500000)/2 = 250000. Como novamente 250000 é maior que 62442, atualizamos novamente o nosso valor máximo para 250000.

Seguindo essa lógica, vamos ver quantos palpites precisaríamos dar para vencer o jogo:


| Rodada        | Mínimo      | Máximo  | Palpite|
| :-----------: |:-------------:| :-----:|:-----:|
| 1 |    1          | 1000000 |500000|
| 2 | 1      |   500000 |250000|
| 3 | 1      |    250000 |125000|
| 4 | 1      |    125000 |62500|
| 5 | 1    |  62500  | 31250 |
|6| 31250| 62500| 46875|
|7| 46875| 62500| 54687|
|8| 54687| 62500| 58593|
| 9|58593| 62500| 60546|
|10| 60546| 62500| 61523|
|11| 61523| 62500| 62011|
|12| 62011| 62500| 62255|
|13| 62255| 62500| 62377|
|14| 62377| 62500| 62438|
|15| 62438| 62500| 62469|
|16| 62438| 62469| 62453|
|17| 62438| 62453| 62445|
|18| 62438| 62445| 62441|
|19| 62441| 62445| 62443|
|20| 62441| 62443| 62442|

WOW! Conseguimos um enorme progresso com esse segundo algoritmo! Em vez de fazer 62442 palpites, agora precisamos de apenas 20 para chegar ao valor correto do nosso número secreto. 

Apesar de ambos os algoritmos resolverem o problema corretamente, o segundo faz isso de uma maneira muito mais ráṕida. Na computação, às vezes precisamos dessa velocidade nos nossos algoritmos, muitas vezes por questão de conveniência (você não gostaria de esperar um minuto pelo resultado da sua pesquisa no google por exemplo) ou até mesmo por questão de segurança!

> O algoritmo que você acabou de ver se chama Busca Binária, caso tenha interesse de procurar mais a respeito e sobre suas aplicações.

## Atividade

Finalmente, depois dessa introdução aos algoritmos, aqui vai a atividade que você deverá fazer na entrevista.

Um dos problemas mais clássicos da computação é o problema da ordenação. Nesse problema, a tarefa é simplesmente ordenar uma certa quantidade de informação. Por exemplo:

```
2, 23, -5, 12, 19, 0 -20, 12   ---->   -20, -5, 0, 2, 12, 12, 19, 23
```

Aqui, tinhamos uma lista de números e a ordenamos em ordem crescente.

Como no exemplo do jogo da adivinhação, existem diferentes algoritmos para ordenação de coisas (usaremos números em ordem nesse texto por simplicidade). Esses algoritmos funcionam de maneiras diferentes e podem resolver o problema com números distintos de ações, como os dois algoritmos do jogo de adivinhação acima.

A sua tarefa será explicar ao entrevistador como ordenar um grupo de cartas de um baralho convencional com as seguintes restrições:
- Você será responsável por ditar as instruções ao entrevistador
- Haverá um total de no máximo 8 cartas para serem ordenadas por vez
- As cartas estarão viradas para baixo e dispostas lado a lado
- O entrevistador só saberá fazer 3 operações:
  1. Comparar duas cartas (virar e ver os seus valores) e usar o resultado da comparação para executar outra operação.
  2. Colocar cartas do baralho em algum lugar da mesa. 
  3. Pegar cartas do baralho de algum lugar da mesa.
- As suas decisões de ordenamento devem seguir um algoritmo predefinido com base no que foi exposto acima e nos seus estudos.
- A sua explicação deve ser reproduzível pelo entrevistador com um conjunto diferente e qualquer de cartas.

Segue um exemplo de como a entrevista funcionaria caso o problema fosse separar cartas de um baralho convencional por cor (a visão e a mão representam o entrevistador; a voz representa o entrevistado): [video-exemplo](https://streamable.com/53g4v). Ou seja, tudo se passará como se o entrevistador fosse o computador que vai seguir as instruções do entrevistado, que faz aqui o papel de programador. No final, espera-se que o entrevistado tenha a capacidade de explicar o procedimento adotado e que o algoritmo descrito seja funcional e eficiente para ordenar as cartas face à quantidade de operações utilizadas.


Abraços,
pessoal legal da ITAbits :)

PS.: Caso você não esteja conseguindo transformar o seu jeito de ordenar as cartas do baralho em um algoritmo que se encaixe nas especificações dadas, ou caso esteja curioso em busca das mais diferentes soluções possíveis pra esse problema, a busca por "sorting algorithms" pode te trazer muitos conhecimentos interessantes.

PPS.: [Presente-de-um-vet-mae](http://lmgtfy.com/?iie=1&q=Sorting+Algorithms)
