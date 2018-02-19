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

Com esse algoritmo, suponha que o número secreto é 62442. Ele entraria na instrução 1 e palpiratia o número 1 e seguiria para a instrução 2.
Como 1 não é igual a 62442, na instrução 2 não é chamado o fim do algoritmo e seguiríamos para a instrução 3.
Na instrução 3, palpitaríamos o palpite anterior (que é 1), somado de 1, resultando no palpite do número 2. E seguimos para a instrução 4.
Na instrução 4, voltaríamos para a instrução 2 e verificaríamos a veracidade do nosso palpite. Como 2 não é igual a 62442, seguiríamos para a instrução 3 e palpitaríamos agora o número 3.

Perceba que demoraríamos 62442 palpites para acertar o valor do nosso número secreto, e não estamos também usando a informação de que nossos palpites são maiores ou menores que o número secreto pois nesse caso, a gente sempre palpita o menor número possível.
Com esse algoritmo, se o número secreto for 9999999, demoraríamos bastante para ganhar o jogo.

Vamos ver agora um algoritmo mais eficiente.

### Algoritmo 2 - Um pouco mais eficiente

```
* Instrução 1 - Nomear o valor 1 como mínimo e o valor 1000000 como máximo.
* Instrução 2 - Palpitar a média aritmética ente o valor mínimo e o valor máximo (mínimo + máximo)/2, 
arredondar para baixo casoa divisão não seja inteira.
* Instrução 3 - Se o palpite for correto, finalizamoso o algoritmo. Se o nosso palpite for menor
que o número secreto, atualizamos o nosso valor mínimo para o nosso valor do palpite. 
Caso contrário, atualizamos o nosso valor máximo para o valor do palpite.
* Instrução 4 - Pule para a Instrução 2.

``` 
Agora com esse segundo algoritmo, vamos ver o que aconteceria se o número secreto for de novo 62442.
Inicialmente nosso mínimo vale 1 e nosso máximo vale 1000000. Palpitaríamos inicialmente (1 + 1000000)/2 = 500000 arredondado para baixo. Como 500000 é maior que 5000, na instrução 3 atualizaríamos o nosso máximo para 500000. Voltaríamos para a instrução 2 agora com o valor mínimo sendo 1 e o máximo sendo 50000. Logo, nosso palpite será agora (1 + 500000)/2 = 250000. Como novamente 25000 é maior que 5000, atualizamos novamente o nosso valor máximo para 250000.

Seguindo essa lógica, vamos ver quantos palpites precisaríamos dar para vencer o jogo:


| Rodada        | Mínimo      | Máximo  | Palpite|
| ------------- |:-------------:| -----:|-----:|
| 1 |    1          | 1000000 |500000|
| 2 | 1      |   500000 |250000|
| 3 | 1      |    250000 |125000|
| 4 | 1      |    125000 |62500|
| 5 | 62500     |  12500  | 31250 |
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

Apesar de ambos os algoritmos resolverem o problema corretamente, o segundo faz isso de uma maneira muito mais ráṕida. Na computação, as vezes precisamos dessa velocidade nos nossos algoritmos muitas vezes por questes de conveniência (você não gostaria de esperar um minuto pelo resultado da sua pesquisa no google por exemplo) ou até mesmo por questo de segurança!

O algoritmo que você acabou de ver se chama Busca binária, caso tenha interesse de procurar mais a respeito e sobre suas aplicações.

## Atividade

Finalmente, depois dessa introdução aos algoritmos, aqui vai a atividade que você deverá fazer na entrevista.

Um dos problemas mais clássicos da computação é o problema da ordenação. Nesse problema, a tarefa é simplesmente ordenar uma certa quantidade de informação. Por exemplo:

```
2, 23, -5, 12, 19, 0 -20, 12   ---->   -5, 0, 2, 12, 12, 19, 20, 23
```

Aqui, tinhamos uma lista de números e a ordenamos em ordem crescente.

Como no exemplo do jogo da adivinhação, existem diferentes algoritmos para ordenação de coisas (usaremos números em ordem nesse texto por simplicidade). Esses algoritmos funcionam de maneiras diferentes e podem resolver o problema com números distintos de ações, como os dois algoritmos do jogo de adivinhação acima.

A sua tarefa será ordenar um grupo de cartas de baralho, com a menor quantidade de operações possível, seguindo as regras abaixo:
1. Todas as cartas estarão viradas para baixo sobre a mesa, dispostas da esquerda para a direita
2. Você poderá virar duas cartas para cima e decidir se deve trocá-las ou não de lugar na mesa
3. Cada vez que virar duas cartas para cima, será considerado que você executou uma operação
4. Trocar cartas de lugar não é considerado uma operação

Como sou um veterano muito mãe, vou listar abaixo alguns algoritmos de ordenação pra vocês. Então o seu trabalho será apenas pesquisá-los no Google, entendê-los, e escolher o que achar melhor para a tarefa. Na entrevista, deverá explicar a sua escolha e executá-lo para ordenar as nossas cartinhas.

Aqui vai a lista com o nome dos algoritmos mais comuns. Escolha bem o seu:
* Bubble sort
* Selection sort
* Insertion sort
* Merge Sort
* Quick Sort

Caso tenha alguma dúvida sobre a tarefa, sobre algum algoritmo, sobre qualquer coisa escrita aqui ou queira bater um papo mesmo, basta procurar qualquer membro da bits. Estamos ansiosos para conhecer vocês e bostejar um pouco também. :)

Abraços, Guima T-19.
