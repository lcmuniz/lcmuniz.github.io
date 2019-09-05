---
layout: post
title: "React Native - Lista de Contatos - Parte 2"
date: 2019-09-04 10:11:11 -0300
categories: react-native
---

Nesta série de posts, estamos implementando uma lista de contatos em React Native. Utilizamos o site 
https://snack.expo.io/ para criar o projeto. 

No [post anterior](http://lcmuniz.github.io/react-native/2019/09/02/react-native-snack.html), criamos a listagem das pessoas usando um array fixo contendo os nomes a serem apresentados. Agora, iremos buscar estes dados de uma API REST na Internet.

Primeiramente, devemos adicionar a biblioteca axios ao projeto. Para fazer isso, normalmente utilizamos o comando `npm install axios --save`. Este comando, digitado na linha de comando na pasta do projeto, irá fazer o download da biblioteca axios para a pasta node_modules e adicionara uma referência à biblioteca no arquivo package.json. Como estamos utilizando o snack.expo.io como editor online, não temos acesso ao terminal e ao npm para realizar a instalação. Então, editaremos o arquivo package.json diretamente e adicionaremos a referência ao axios conforme listagem a seguir: 

{% highlight json %}
{
  "dependencies": {
    "axios": "^0.19.0",
    "react-native-paper": "2.16.0"
  }
}
{% endhighlight %}

Agora que a biblioteca está adicionada ao arquivo package.json. Podemos utilizá-la no projeto.

### A API JSON

Utilizaremos o site randomuser.me para obter os dados de usuários online. Este site nos fornece uma API para recuperar dados em JSON que iremos utilizar para apresentar nomes na nossa lista de Pessoas. Você pode acessar o site e ler a documentação para ver como a API funciona.

Para nossa aplicação, utilizaremos a url `https://randomuser.me/api/?results=5`. Esta chamada irá nos retornar 5 usuários aleatórios em JSON. Para ver o formato dos dados retornados, você pode digitar essa url em um navegador web.

Para a nossa aplicação, basta sabermos que os usuários são retornados em um array cuja chave é a string results. Neste array, cada usuário tem diversos campos sendo que um deles é o campo name. Este campo name, por sua vez, é um objeto que possui três campos (title, first e last) representado o título (mr ou ms), o primeiro e o último nome, respectivamente.

Veja um exemplo de consulta a esta API usando o aplicativo Postman.

![tela10](/assets/sketch-10.png) 

Agora, vamos alterar a classe App para usar esta API. Primeiramente, removemos os nomes de pessoas fixos que estão no construtor da classe. Deixaremos apenas um array vazio no lugar.

Depois, importamos a biblioteca axios no início do arquivo e, finalmente, criamos o método `componentDidMount()`. Este método é executado sempre que o componente é montado. Então, dentro deste método, fazemos a chamada à API REST utilizando a biblioteca axios. Veja o código na imagem abaixo.

![tela11](/assets/sketch-11.png) 


O método get do axios faz a chamada à API. O resultado então é retornado no objeto response e tratado no primeiro then. O axios disponibiliza os dados retornados da API na variável data do objeto response. A variável data é então tratada no segundo then. No caso da API do site randomuser.me, o objeto data do axios contém o objeto JSON retornado pelo site. O campo results desse objeto data contém o array de usuários que então atribuimos à variável pessoas do estado do componente.

O componente `PessoaLista` recebe, agora, não um array de strings mas um array de objetos usuários. O componente PessoaLista precisa ser alterar porque, durante seu map para criar os componentes `PessoaItem`, ele precisa atribuir a sua propriedade key com um valor único mas esta propriedade não aceita objetos. Por isso, alteramos a propriedade key para fazer referência ao campo name.last de cada objeto do array results. Veja o código na imagem abaixo.

![tela12](/assets/sketch-12.png) 

Por fim, alteramos o objeto `PessoaItem` pois este agora deve mostrar o campo name do objeto que lhe é passado. Na verdade, agora o componente deve mostrar os campos name.title, name.first e name.last. A imagem abaixo mostra o componente alterado.

![tela13](/assets/sketch-13.png) 

Os nomes das pessoas, neste momento, está sendo recuperado do site randomuser.me. Mas a apresentação dos nomes não está boa porque os nomes estão em letras minúsculas. Vamos criar uma função para capitalizar os nomes.

Para isso, vamos criar uma pasta utils e, dentro desta pasta, um arquivo index.js com o conteúdo mostrado na imagem abaixo.

![tela14](/assets/sketch-14.png) 

A função `capitalize()` recebe uma string como parâmetro e altera para maiúscula sua primeira letra.

Vamos agora alterar o componente PessoaItem para utilizar a função capitalize(). Para isso, precisamos importar a função capitalize() que está no arquivo utils/index.js e, depois, utilizá-la para mostrar as pessoas na tela. Veja a imagem a seguir.

![tela15](/assets/sketch-15.png) 

### Conclusão (por enquanto...)

Nesta parte, adicionamos a funcionalidade de recuperar a lista de pessoas da Internet utilizando a biblioteca axios. No próximo post, adicionaremos imagens à lista.

O código-fonte deste projeto pode ser baixado no repositório [GitHub LCMuniz](https://github.com/lcmuniz/react-native-lista-contatos).