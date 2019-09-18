---
layout: post
title: "JavaScript - Fluxo de Controle"
date: 2019-09-04 03:39:10 -0300
categories: javascript
---

Quando um programa possui mais de uma instrução, elas são executadas na ordem em que 
aparecem no arquivo de cima para baixo. Ou seja, no programa abaixo, primeiro é executada 
a instrução que declara e inicializa a variável idade e depois a instruçao que mostra
o valor da variável na tela. A função console.log() é uma função de biblioteca da linguagem que utilizamos para mostrar algo na tela. A função mostra na tela o que quer que passemos para ela entre os parênteses. No exemplo abaixo, o valor contido na variável idade.

{% highlight javascript %}
let idade = 49
console.log(idade)
{% endhighlight %}

### A instrução `if`

Nem todo programa segue esse fluxo. O programador pode querer executar determinada instrução
apenas se uma condição específica for verdadeira. Por exemplo, podemos querer imprimir a 
frase 'Idade de adulto' caso o valor da variável idade é maior ou igual a 18 anos.

Para isso, usamos a instrução `if` (se). Veja o exemplo abaixo:

{% highlight javascript %}
let idade = 21

if (idade >= 18) {
  console.log('Idade de adulto.')
}
console.log('Fim do programa!')
{% endhighlight %}

No exemplo acima, após declararmos e inicializarmos a variável idade com o valor 21, testamos se o seu valor é maior ou igual a 18. Como esta condição é verdadeira, as instruções entre parênteses que seguem o `if` são executadas. Caso a condição fosse falsa, o código entre parênteses não seria executado.

A saída deste programa é mostrada abaixo.

{% highlight terminal %}
Idade de adulto.
Fim do programa!
{% endhighlight %}

No caso de querermos que algo seja executado se a condição for falsa, usamos a instrução `else` (senão). Veja o programa abaixo.

{% highlight javascript %}
let idade = 21

if (idade >= 18) {
  console.log('Idade de adulto.')
}
else {
  console.log('Idade de criança ou adolescente.')
}
console.log('Fim do programa!')
{% endhighlight %}

A saída deste programa é igual à saída do programa anterior pois a condição é verdadeira
e a linha dentro do bloco do `if` é executada. A instrução dentro do bloco do `else` não
é executada.

{% highlight terminal %}
Idade de adulto.
Fim do programa!
{% endhighlight %}

Mas, caso alteremos a idade para um valor menor que 18, a saída muda. Veja o exemplo abaixo.

{% highlight javascript %}
let idade = 16

if (idade >= 18) {
  console.log('Idade de adulto.')
}
else {
  console.log('Idade de criança ou adolescente.')
}
console.log('Fim do programa!')
{% endhighlight %}

Nesse caso, o teste idade >= 18 resulta em falso e o bloco do `if` não é executado. No entanto, o bloco `else` é executado e a saída do programa é a mostrada abaixo.

{% highlight terminal %}
Idade de criança ou adolescente.
Fim do programa!
{% endhighlight %}

Se quisermos testar a idade para mostrar frases diferentes caso a idade seja de criança, adolescente, adulto ou idoso, podemos usar um conjunto de instruções como mostrado abaixo.

{% highlight javascript %}
let idade = 16

if (idade <= 12) {
  console.log('Idade de criança.')
}
else if (idade > 12 && idade < 18) {
  console.log('Idade de adolescente.')
}
else if (idade >= 18 && idade < 65) {
  console.log('Idade de adulto.')
}
else {
  console.log('Idade de idoso.')
}
console.log('Fim do programa!')
{% endhighlight %}

No código acima, a idade é inicializada com o valor 16. No primeiro `if`, testamos se 
a idade é menor ou igual a 12. Como esse teste resulta em falso, o programa não
mostra a mensagem 'Idade de criança.' e prossegue para o próximo teste. O segundo teste
é se a idade está entre 12 e 18. Neste caso, o teste resulta em verdadeiro e o programa
executa o bloco deste `if` mostrando a mensagem 'Idade de adolescente.' na tela.
Como o teste foi verdadeiro, o programa não executa nenhum dos elses subsequentes e 
vai para o fim do último `else` e executa a próxima instrução que é mostrar a mensagem
'Fim do programa!'. Portanto, a saída do programa acima é

{% highlight terminal %}
Idade de adolescente.
Fim do programa!
{% endhighlight %}

### A instrução `while`

Considere um programa que imprime os número pares de 0 a 10. Uma maneira de fazer isso é assim

{% highlight terminal %}
console.log(0)
console.log(2)
console.log(4)
console.log(6)
console.log(8)
console.log(10)
{% endhighlight %}

Isso funciona. Mas e se precisarmos imprimir os número de 0 1000? Ou 1000000? Nesse caso, essa abordagem seria muito trabalhosa. Nós precisamos de uma maneira de executar um mesmo bloco de código várias vezes. Essa forma é o que chamamos de laço.

Agora, veja o código abaixo

{% highlight terminal %}
let numero = 0
while (numero <= 10) {
  console.log(numero)
  numero = numero + 2
}
{% endhighlight %}

A instrução `while` cria um laço. A expressão entre parênteses que seque a palavra while é uma condição que será avaliada e, caso verdadeira, fará com que o bloco de código entre { e } seja executado. Após o bloco ser execuado, a condição é reavaliada e, se for verdadeira, o bloco de código é execuado novamente. Esse processo de executar o bloco e avaliar a condição se repete até que a avaliação da condição resulte em falso, quando então o laço termina e o programa prossegue com a execução das linhas após o bloco (que neste caso não existem e, portanto, o programa termina.)

O programa acima funciona da seguinte maneira: 

1. a primeira instrução declara uma variável chamada `numero` e a inicializa com o valor zero. 
2. Em seguida, o programa encontra uma instrução `while`. A condição `numero <= 10` é avaliada (0 <= 10, que resulta em verdadeiro) e o programa inicia a execução das instruções entre os parênteses.
3. A instrução `console.log(numero)` é executada, o que mostra o número 0 na tela.
4. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 0 + 2, ou seja, 2.
5. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Agora, a condição `numero <= 10` é avaliada como `2 <= 10`, o que resulta em verdadeiro, fazendo com que o programa prossiga executando as instruções do laço.
6. A instrução `console.log(numero)` é executada, o que mostra o número 2 na tela.
7. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 2 + 2, ou seja, 4.
8. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Agora, a condição `numero <= 10` é avaliada como `4 <= 10`, o que resulta em verdadeiro, fazendo com que o programa prossiga executando as instruções do laço.
9. A instrução `console.log(numero)` é executada, o que mostra o número 4 na tela.
10. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 4 + 2, ou seja, 6.
11. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Agora, a condição `numero <= 10` é avaliada como `6 <= 10`, o que resulta em verdadeiro, fazendo com que o programa prossiga executando as instruções do laço.
12. A instrução `console.log(numero)` é executada, o que mostra o número 6 na tela.
13. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 6 + 2, ou seja, 8.
14. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Agora, a condição `numero <= 10` é avaliada como `8 <= 10`, o que resulta em verdadeiro, fazendo com que o programa prossiga executando as instruções do laço.
15. A instrução `console.log(numero)` é executada, o que mostra o número 8 na tela.
16. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 8 + 2, ou seja, 10.
17. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Agora, a condição `numero <= 10` é avaliada como `10 <= 10`, o que resulta em verdadeiro, fazendo com que o programa prossiga executando as instruções do laço.
6. A instrução `console.log(numero)` é executada, o que mostra o número 10 na tela.
4. A variável `numero` tem seu valor alterado para o valor da expressão `numero + 2`, que é 10 + 2, ou seja, 12.
5. O fluxo do programa volta para a instrução `while` para reavaliar a condição. Neste momento, a condição `numero <= 10` é avaliada como `12 <= 10`, o que resulta em falso. Agora, como a condição do laço retorno falso, o programa não executa as instruções entre os parênteses e salta para a próxima instrução após o bloco de código (a instrução após o }). Como não existem mais instruções após o laço, o programa termina. O resultado é que o programa mostra na tela os números pares entre 0 e 10, inclusive.

O programa abaixo calcula o valor de 2<sup>10</sup> usando um laço. Precisamos de duas variáveis: uma para manter o resultado parcial de cada multiplicação por 2 e outra para usar como contador de quantos números já multiplicamos. 

{% highlight terminal %}
let resultado = 1
let contador = 0
while (contador < 10) {
  resultado = resultado * 2
  contador = contador + 1
}
console.log('2 elevado a 10 é igual a ' + resultado)
{% endhighlight %}

### A instrução `do`

O laço `do` é similar ao laço `while`. A única diferença é que o laço `do` sempre executa o blodo de instruções do laço pelo menos uma vez, pois o teste da condição só é feito ao final. 

{% highlight terminal %}
let nome
do {
  nome = prompt("Digite seu nome: ")
} while (nome == "")
console.log('Olá ' + nome)
{% endhighlight %}

Este programa pede ao usuário que digite seu nome. Caso o usuário pressione ENTER sem digitar nada, o programa continua pedindo pelo nome até que o usuário digite um nome. Ao final, mostra na tela `Olá` seguido do nome digitado. 

### A instrução `for`

Muitos laços seguem o padrão mostrado nos laços while acima. Primeiro um contador é criado para controlar o número de vezes que o laço irá executar. Depois vem o teste de uma condição para saber se as instruções do laço devem ser executas. Ao final da execução das instruções, o contador é atualizado e a condição é testada novamente.

Por este padrão ser muito comum, a linguagem Javascript e muitas outras fornecem uma maneira mais simples de criar estes laços: a instrução `for`.

{% highlight terminal %}
for (let numero = 0; numero <= 10; numero = numero + 2) {
  console.log(numero)
}
{% endhighlight %}

O programa acima faz a mesma coisa do primeiro exemplo de laço while: ele mostra na tela os números pares de 0 a 10 inclusive.

O laço `for` começa declarando e inicializando a variável numero com o valor 0. Depois, a condição é testada e, caso verdadeira, o programa executa as instruções entre { e }. Após executar as instruções, a variável numero é atualizada (no caso, é adicionado 2 ao valor anterior). O teste da condição é feito novamente e o processo é repetido até que a condição retorne falso. Note que a inicializaçã da variável, a condição e a atualização do valor da variável estão na mesma linha entre parênteses e separados por ponto e vírgula.

O programa abaixo calcula 2<sup>10</sup> usando um laço `for`.

{% highlight terminal %}
let resultado = 1
for (let contador = 0; contador < 10; contador = contador + 1) {
  resultado = resultado * 2
}
console.log(resultado)
{% endhighlight %}


### Conclusão

Neste post, aprendemos a usar as instruções de controle mais comuns da linguagem Javascript: a instrução `if` para executar instruções de forma condicionad e os laços `while`, `do` e `for` para executar instruções repetidamente enquanto uma condição for verdadeira.

Este post é baseado no livro _Eloquent JavaScript_ de Marijn Haverbeke.
