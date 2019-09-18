---
layout: post
title: "JavaScript - Variáveis"
date: 2019-08-24 00:39:10 -0300
categories: javascript
---

Um programa em JavaScript mantém seu estado interno através do uso de variáveis.
Para definir uma variável utiliza-se a palavra-chave `let` seguida do nome da variável. Opcionalmente, podemos atribuir imediatamente um valor utilizando o sinal de atribuição `=` e o valor inicial.

{% highlight javascript %}
let idade = 49
{% endhighlight %}

Caso não seja atribuido um valor inicial, a variável será inicializada com o valor especial `undefined`.

O valor depois do sinal de atribuição, pode ser qualquer expressão válida em JavaScript. Por exemplo:

{% highlight javascript %}
let dias = 12 * 30
let nome = "João" + " da " + "Silva"
let adulto = idade >= 18
{% endhighlight %}

Note que a última instrução, utiliza a variável `idade`, declarada anteriormente, para definir o valor lógico (no caso, `true` pois 49 é maior oou igual a 18) que será atribuído então à variável `adulto`.

Após a declaração de uma variável com a palavra-chave `let`, podemos alterar seu valor apenas utilizando o seu nome e atribuindo outra expressão.

{% highlight javascript %}
dias = dias + 1
nome = 'Maria'
adulto = false
{% endhighlight %}

Na primeira instrução acima, utilizamos a própria variável na expressão para calcular o novo valor a lhe ser atribuído. No caso, se `dias` tem o valor `360`, a expressão `dias + 1` é avaliada como `361` e este será o novo valor da variável `dias`. 

### Constantes

Uma outra forma de declarar uma variável é utilizando a palavra-chave `const`. Neste caso, o valor da variável não poderá ser alterado após a sua inicialização. Chamamos a este tipo de variável, uma contante.

{% highlight javascript %}
const pi = 3.14
const saudacao = "Oi"
{% endhighlight %}

Caso tentemos atribuir um novo valor a uma constante, o interpretador JavaScript irá gerar uma mensagem de erro.

{% highlight javascript %}
const x = 10
x = 20
TypeError: Assignment to constant variable.
{% endhighlight %}

Em JavaScript uma variável pode armazenar valores de qualquer tipo. Nada impede que em determinado momento o valor de uma variável seja uma `string` e depois, em outro momento, seja alterado para um 'number'.

{% highlight javascript %}
let valor = 100.        // valor armazena um número real
valor = "Rua do Sol"    // agora armazena uma string
valor = 5 % 2           // agora armaena um inteiro
{% endhighlight %}

### A palavra-chave `var`

Você poderá ver código JavaScript onde as variáveis são declaradas utilizando-se a palavra-chave `var` ao invés de `let`. A definição com `let` surgiu a partir da versão 6 do JavaScript. Ela resolve alguns problemas de `var` e, portanto, deve-se utilizar `let` preferencialmente. Em outro post, falaremos mais sobre as diferenças entre `var` e `let`.  

### Conclusão

Apresentamos o conceito de variável e constante. Uma variável é uma posição de memória identificada por um nome no qual podemos armazenar valores. Se declarada com a palavra-chave `let`, podemos alterar o valor armazenado na variável durante a execução do programa. Caso seja declarada com a palavra-chave `const`, o valor armazenado na variável não poderá ser alterado após sua atribuição.

Este post é baseado no livro _Eloquent JavaScript_ de Marijn Haverbeke.
