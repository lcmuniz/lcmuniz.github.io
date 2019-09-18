---
layout: post
title: "JavaScript - HTML"
date: 2019-09-17 12:52:59 -0300
categories: javascript
---

Vamos fazer uma calculadora de somar muito simples.

Crie dois arquivos em um editor de texto: adicao.html e adicao.js.

No arquivo adicao.html, digite o código abaixo:

{% highlight html %}
<html>
  <head>
    <title>Calculadora</title>
    <script src="adicao.js"></script>
    <meta charset="utf-8"/>
  </head>
  <body>
    <h2>Calculadora de Somar</h2>
    <p></p>
    <p>Digite o primeiro número: <input id="numero1" /></p>
    <p>Digite o segundo número: <input id="numero2" /></p>
    <p><button onclick="somarNumeros()">Somar</button></p>
    <p>A soma dos números é <output id="soma"></output>.</p>
  </body>
</html>
{% endhighlight %}

No arquivo adicao.js, digite o código abaixo:

{% highlight javascript %}
function somarNumeros() {
	
	const n1 = document.getElementById('numero1').value
	const n2 = document.getElementById('numero2').value

	const resultado = Number(n1) + Number(n2)

	document.getElementById('soma').value = resultado
}
{% endhighlight %}

Agora, basta abrir o arquivo adicao.html no navegador, digitar as informações solicitadas e clicar no botão Somar. Os números serão somados e o resultado será apresentado na tela.

