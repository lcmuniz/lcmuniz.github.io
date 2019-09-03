---
layout: post
title: "React Native - Lista de Contatos"
date: 2019-09-02 10:29:11 -0300
categories: react-native
---

Nesta série de posts, implementaremos uma lista de contatos em React Native. Utilizaremos o site 
https://snack.expo.io/ para criar o projeto. 

Ao acessar o site, um projeto inicial é apresentado com uma configuração básica. Do lado esquerdo é mostrada a árvore de diretórios e arquivos. No centro, a área de edição de arquivos e do lado direito, um emulador que mostra a aplicação desenvolvida.

![tela01](/assets/sketch-01.png) 

Vamos simplificar o código gerado removendo o componente AssetExample.js da pasta components e simplificando o código do arquivo App.js como mostrado na figura abaixo. Para ver o resultado, basta clicar no botão 'Tap to play' do emulador.

![tela02](/assets/sketch-02.png) 


### O component Header

Vamos criar o nosso primeiro componente. O componente Header.js, na pasta components, conforme imagem abaixo.

![tela03](/assets/sketch-03.png) 

Observe que criamos estilos para a apresentação do componente. 

Agora basta, colocar o componente <Header /> no arquivo App.js, como mostrado na figura a seguir.

![tela04](/assets/sketch-04.png) 

O componente Header tem o texto 'Pessoas' fixo. Para torná-lo mais genérico, vamos passar o texto a ser mostrado através da propriedade titulo. 

No arquivo Header.js, alteramos o componente Header para 

{% highlight javascript %}
  <View style={styles.conteudo}>
      <Text style={styles.titulo}>{props.titulo}</Text>
  </View>
{% endhighlight %}

Dessa forma, no arquivo App.js, alteramos a chamada do componente Header passando o atributo titulo. 

{% highlight javascript %}
<Header titulo="Pessoa" />
{% endhighlight %}

### O componente PessoaLista 

Para mostrar uma lista de pessoas, vamos criar um componente PessoaLista que recebe como propriedade um array de strings com o nomes das pessoas a ser mostrado.

Antes, vamos criar o arquivo PessoaLista.js com o código a seguir.

![tela05](/assets/sketch-05.png) 

Observe que, neste momento, o componente PessoaLista apenas mostra um texto com o tamanho do array passado como propriedade.

Agora, vamos criar um array de pessoas como um atributo do estado do componente App. Para isso, devemos criar o estado no construtor do componente, no arquivo App.js. Por enquanto nosso array de pessoas conterá 4 nomes fixos. Mais adiante, iremos recuperar esses nomes de uma API JSON pela Internet.

Alteramos o arquivo App.js conforme figura abaixo, para mostrar o componente PessoaLista logo abaixo do título. Observe que o componente PessoaLista recebe na propriedade pessoas, o array de strings do estado.

![tela06](/assets/sketch-06.png) 

O próximo passo é fazer um loop sobre o array para mostrar cada nome em uma linha separada. Para isso usaremos o método map() para transformar cada string do array em uma linha de Views, conforme imagem abaixo.

![tela07](/assets/sketch-07.png) 

### O componente PessoaItem 

Até agora, o componente PessoaLista é responsável por criar a linha que mostra cada pessoa. Vamos criar um componente PessoaItem para encapsular cada linha. Esse componente recebe uma pessoa como propriedade é a apresenta na tela.  

![tela08](/assets/sketch-08.png) 

Por fim, alteramos o componente PessoaLista para usar o componente PessoaItem. Note que adicionamos uma propriedade key no componente PessoaLista. Isso ocorre, porque o React Native exige que cada filho de um componente pai em um array tenha uma chave única. No caso, usamos como chave a própria string passada para o componente (assumindo que ela é única).

![tela09](/assets/sketch-09.png) 


### Conclusão (por enquanto...)

Apresentamos os primeiros passos na criação de um aplicativo de lista de contatos em React Native. Nos próximos posts daremos continuidade ao projeto criando a funcionalidade para obtermos a lista de nomes dinamicamente via uma API JSON.

O código-fonte deste projeto pode ser baixado no repositório [GitHub LCMuniz](https://github.com/lcmuniz/react-native-lista-contatos).