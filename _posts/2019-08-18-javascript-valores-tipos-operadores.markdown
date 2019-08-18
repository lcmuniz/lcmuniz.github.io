---
layout: post
title: "JavasCript - Valores, Tipos e Operadores"
date: 2019-08-18 12:52:59 -0300
categories: javascript
---

Em JavaScript, valores representam informações utilizadas pelos programas durante sua execução. Por exemplo, em um programa processe informações acadêmicas, temos valores como "João da Silva", que pode representar o nome de um aluno, ou ainda 7.5, que pode ser a nota de um aluno em um teste.

Os valores básicos de JavaScript são classificados segundo o seu tipo em números, textos e valores lógicos.

### Números (numbers)

Os valores do tipo `number` representam números (claro). Por exemplo:

{% highlight javascript %}
14
21
49.56
{% endhighlight %}

são exemplos de números em JavaScript.

Os dois primeiros são numeros inteiros e o terceiro é um número real.

Os números podem ser usados em expressões matemáticas. As operações com números usam os operadores comuns que já conhecemos. Os operadores + e - referem-se à adição e subtração.
O operador de multiplicação é \* (asterísco) e o de divisão é / (barra).

{% highlight javascript %}
3 - 4 + 5   // resultado: 4
// podemos usar parênteses para alterar a prioridade dos operadores
3 - (4 + 5) // resultado: -6 
3 * 6 / 2   // resultado: 9
// os operadores * e / têm prioridade em relação aos operadores + e -
4 + 2 * 3   // resultado: 10 
(4 + 2) * 3 // resultado: 18
{% endhighlight %}

Além das quatro operações, temos o operador % que nos retorna o resto da divisão dos seus operadores.

{% highlight javascript %}
15 % 4   // resultado: 3, pois 15 / 4 é igual 3 e 'sobra' 3
12 % 2   // resultado: 0, pois 12 / 2 é igual a 6 e não 'sobra' nada
7 % 2    // resultado: 1, pois 7 / 2 é igual 3 e 'sobra' 1
{% endhighlight %}

### Textos (strings)

Os valores do tipo `string` representam textos. São escritos entre aspas (simples ou duplas) ou entre ` (o sinal de crase).

{% highlight javascript %}
"João da Silva"
'Rua do Sol, 123'
`Isto  é uma frase.`
{% endhighlight %}

Ao escrevermos strings temos que tomar cuidado com textos que contenham aspas em seu interior. Para ilustrar o problema, suponha que queiramos escrever a string __Te encontro no Bob's mais tarde__. Se representarmos assim

{% highlight javascript %}
`'Te encontro no Bob's mais tarde'`
{% endhighlight %}

A linguagem JavaScript vai entender que a frase começa em Te e termina em Bob (o texto entre as aspas simples). Como o texto restante não começa com aspa, o JavaScript vai emitir uma mensagem de erro.

Para solucionar este tipo de situação, fazemos o seguinte: caso o texto tenha aspas simples em seu interior, o delimitamos com aspas duplas e caso tenha aspas duplas, o delimitamos com aspas simples. Por exemplo:

{% highlight javascript %}
"Te encontro no Bob's mais tarde"
'Ele disse "Olá" assim que entrou.'
{% endhighlight %}

As strings delimitadas pelo sinal da crase permitem que coloquemos expressões em seu interior que serão avaliadas quando o programa for executado. As expressões devem ser colocadas dentro dos sinais ${}. Por exemplo:

{% highlight javascript %}
`40 graus Celsius é igual a ${40 * 9 / 5 + 32} graus Fahrenheit.`
{% endhighlight %}

Esta string será convertida eno texto __40 graus Celsius é igual a 53.6 graus Fahrenheit.__ quando o programa for executado.

### Valores lógicos (booleans)

Existem dois valores do tipo `boolean` (true e false) que representam os estados verdadeiro e falso, respectivamente. 

Os valores booleans são obtidos a partir da avaliação de condições que são criadas através dos operadores de comparação maior que (>), menor que (<), maior ou igual a (>=), menor ou igual a (<=), igual (==) e diferente (!=).

{% highlight javascript %}
3 > 2       // resultado: true, pois 3 é maior que 2
3 <= 1      // resultado: false, pois 3 não é maior ou igual a 1
4 + 5 == 9  // resultado: true, pois 4 + 5 é igual a 9
3 + 2 != 5  // resultado: false, pois 3 + 2 não é diferente de 5
{% endhighlight %}

As expressões lógicas podem ser combinadas usando-se os operadores lógicos e (&&), ou (||) e negação (!).

O operador && (lê-se e)retorna verdadeiro quando seus dois operadores são verdadeiros ao mesmo tempo.

{% highlight javascript %}
3 > 2 && 2 < 3       // resultado: false, pois 3 é maior que 2 mas 2 não é menor que 3 
4 + 5 == 9 && 3 > 1  // resultado: true, pois 4 + 5 é igual a 9 e 3 é maior que 1
{% endhighlight %}

O operador || (lê-se ou) retorna verdadeiro quando qualquer um dos seus dois operadores é verdadeiro.

{% highlight javascript %}
3 > 2 || 2 < 3       // resultado: true, pois 3 é maior que 2  
4 + 5 > 10 || 3 < 1  // resultado: false, pois 4 + 5 não é maior que 9 nem 3 é menor que 1
{% endhighlight %}

O operador ! (lê-se não) retorna verdadeiro se seu operador é falso e retorna false se seu operador é verdadeiro. Ou seja, ele nega seu operador.

{% highlight javascript %}
! 3 > 2           // resultado: false, pois 3 é maior que 2 (true)  
! (4 + 4 == 7)    // resultado: true, pois 4 + 4 não é igual a 7 (false)
{% endhighlight %}

### Valores especiais 

JavaScript tem algumas palavras-chave que representam valores especiais. São eles:

{% highlight javascript %}
Infinity
-Infinity
NaN
undefined
null
{% endhighlight %}

Estes valores são resultados de determinadas operações. Por exemplo, a expressão

{% highlight javascript %}
` 2 / 0 `
{% endhighlight %}

retorna o valor `Infinity`. Em outras linguagens essa expressão resultaria em um erro, pois não podemos dividir um número por 0, mas em JavaScript ela é avaliada e o resultado retornado é Infinity. 

Já o valor `NaN` significa Not a Number (não é um número) e é resultado de uma expressão que não pode ser avaliada. Por exemplo:

{% highlight javascript %}
` 3 / 'branco'`
{% endhighlight %}

é uma expressão que tenta dividir 3 por um texto.  O resultado dessa expressão é `NaN`.

Os valores `undefined` e `null` representam ausência de valor e serão tratados quando falarmos de variáveis em outro artigo. 