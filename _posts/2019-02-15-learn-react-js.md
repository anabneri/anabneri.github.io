---
title: Aprendendo React.js em 5 minutos
tags: [React, JavaScript, Web Development]
style: border
color: warning
description: Uma rápida introdução sobre React.js em 5min.
---

Source: [freecodecamp](https://medium.freecodecamp.org/learn-react-js-in-5-minutes-526472d292f4)

Esse tutorial é inteiramente traduzido e adaptado por mim, então o conteúdo não é inteiramente meu!!! Mas como eu achei muito interessante, resolvi deixar no meu site, porque me ajudou e creio que pode ajudar mais pessoas! ENJOY DUDES

## A configuração

Ao começar a utilizar o REACT, você deve usar a configuração mais simples possível: um arquivo HTML que importa as bibliotecas `React` e `ReactDOM ` usando Tags de script, como esta:

```html
<html>
<head>
<script src="https://unpkg.com/react@15/dist/react.min.js"> </script><script src="https://unpkg.com/react-dom@15/dist/react-dom.min.js">
</script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
</head>
<body>
    <div id="root"></div>
    <script type="text/babel">

    /*
    ADICIONAR UM CÓDIGO DE REACT AQUI :P
    */

    </script>
</body>
</html>
```

Também importamos Babel, já que o React usa algo chamado JSX para escrever marcações. Vamos precisar transformar esse JSX em JavaScript simples, para que o navegador possa entendê-lo.

Há mais duas coisas que vocês precisam observar:

1. a `<div>`  com o ID de `#root`. Este é o ponto de entrada para o nosso aplicativo. Este é o lugar onde todo o nosso aplicativo vai viver.
1. o  `< script type =  "texto/babel " > ` tag no corpo. É aqui que escreveremos o nosso código React. js.

Se você quiser experimentar com o código, confira este playground Scrimba.

## Componentes/ Components

Tudo em REACT é um componente, e estes geralmente tomam a forma de classes JavaScript. Você cria um componente estendendo-se sobre a classe  `react-component`. Vamos criar um componente chamado `Eai rapaziada`.

```javascript
class Hello extends React.Component {
    render() {
        return <h1>Eai rapaziada</h1>;
    }
}
```

Em seguida, você define os métodos para o componente. No nosso exemplo, nós só temos um método, e ele é chamado de `render ()`.

Dentro de `render ()` você retornará uma descrição do que você quer reagir para desenhar na página. No caso acima, nós simplesmente queremos que ele exiba uma tag `H1` com o texto _ Hello World! _ dentro dele.

Para obter o nosso pequeno aplicativo para renderizar na tela, também temos que usar `ReactDOM.render()`:

```javascript
ReactDOM.render(
    <Hello />, 
    document.getElementById("root")
);
```

Então é aqui que conectamos nosso componente  `Hello` com o ponto de entrada para o aplicativo (`<div id="root"></div>`). Isso resulta:

![](https://cdn-images-1.medium.com/max/1000/1*T-bmSzg0KlijyB3dG1M-ow.png)

A sintaxe de HTML'ish que apenas olhou para (`<h1>` e `<Hello/> `) é o código JSX que mencionei anteriormente. Não é realmente HTML, embora o que você escreve lá acaba como Tags HTML no DOM.

O próximo passo é obter o nosso aplicativo para manipular dados.

## Manipulação de dados

Existem dois tipos de dados no React: props e State. A diferença entre os dois é um pouco complicado de entender no início, por isso não se preocupe se você encontrá-lo um pouco confuso. Vai se tornar mais fácil quando você começar a trabalhar com eles.

A principal diferença é que o estado é privado e pode ser alterado de dentro do próprio componente. Os adereços são externos e não são controlados pelo próprio componente. Ele é passado de componentes acima da hierarquia, que também controlam os dados.

{% include elements/highlight.html text =  "um componente pode alterar seu estado interno diretamente. Ele não pode mudar seus adereços diretamente.  "%}

Vamos dar uma olhada mais de perto em props/adereços primeiro.

## Props/ Adereços

Nosso componente `Hello` é muito estático e renderiza a mesma mensagem independentemente. Uma grande parte do REACT é a reutilização, o que significa a capacidade de escrever um componente uma vez e, em seguida, reutilizá-la em casos de uso diferentes — por exemplo, para exibir mensagens diferentes.

Para alcançar esse tipo de reutilização, adicionaremos adereços. É assim que você passa adereços para um componente:

```javascript
ReactDOM.render(
    <Hello message="my friend" />,
    document.getElementById("root")
);
```

Este prop é chamado de  `message` e tem o valor "my friend". Podemos acessar este prop dentro do componente Hello referenciando  `this. props. Message`, assim:

```javascript
class Hello extends React.Component {
    render() {
        return <h1>Hello {this.props.message}!</h1>;
    }
}
```

Como resultado, isso é renderizado na tela:

![](https://cdn-images-1.medium.com/max/1000/1*M0-2Ct0K3SARZLSwIzgdJw.png)

A razão pela qual estamos escrevendo {this. props. Message} com chavetas é porque precisamos informar ao JSX que queremos adicionar uma expressão JavaScript. Isto é chamado * * escapando * *.

Então agora temos um componente reutilizável que pode renderizar qualquer mensagem que quisermos na página. Woohoo!

No entanto, e se quisermos que o componente seja capaz de alterar seus próprios dados? Então temos que usar o estado em vez disso!

## State

A outra maneira de armazenar dados no React está no estado do componente. E ao contrário dos props — que não podem ser alterados diretamente pelo componente — o estado pode.

Portanto, se você quiser que os dados em seu aplicativo mudem — por exemplo, com base nas interações do usuário — ele deve ser armazenado no estado de um componente em algum lugar do aplicativo.

### Inicializando o state

Para inicializar o estado, basta definir `this. State` no método `Constructor ()` da classe. Nosso estado é um objeto que, no nosso caso, só tem uma chave chamada "mensagem".

```javascript
class Hello extends React.Component {

    constructor(){
        super();
        this.state = {
            message: "my friend (from state)!"
        };
    }

    render() {
        return <h1>Hello {this.state.message}!</h1>;
    }
}
```

Antes de definir o estado, temos de chamar `super ()` no construtor. Isso é porque `this` é não inicializado antes `super ()` foi chamado.

Alterando o estado
Para modificar o estado, basta chamar **this. setState ()**, passando o novo objeto de estado como o argumento. Faremos isso dentro de um método que chamaremos de  `updateMessage`.

```javascript
class Hello extends React.Component {

    constructor(){
        super();
        this.state = {
            message: "my friend (from state)!"
        };
        this.updateMessage = this.updateMessage.bind(this);
   }
    updateMessage() {
        this.setState({
            message: "my friend (from changed state)!"
        });
    }
    render() {
        return <h1>Hello {this.state.message}!</h1>;
    }
}
```

> SE LIGA: para fazer isso funcionar, também tivemos que vincular a palavra-chave `this` ao método   `updateMessage`. Caso contrário, não poderíamos ter acessado `this` no método.

A próxima etapa é criar um botão para clicar, para que possamos acionar o método `updateMessage ()`.

Então, vamos adicionar um botão para o método  `render ()`:

```javascript
render() {
  return (
     <div>
       <h1>Hello {this.state.message}!</h1>
       <button onClick={this.updateMessage}>Click me!</button>
     </div>
  )
}
```

Aqui, estamos conectando um ouvinte de eventos no botão, ouvindo o evento **onClick**. Quando isso é acionado, chamamos o método **updateMessage**.

Aqui está o componente inteiro:

```javascript
class Hello extends React.Component {

    constructor(){
        super();
        this.state = {
            message: "my friend (from state)!"
        };
        this.updateMessage = this.updateMessage.bind(this);
    }
    updateMessage() {
        this.setState({
            message: "my friend (from changed state)!"
        });
    }
    render() {
         return (
           <div>
             <h1>Hello {this.state.message}!</h1>
             <button onClick={this.updateMessage}>Click me!</button>
           </div>
        )
    }
}
```

TO **updateMessage** método, em seguida, chama **this. setState ()** que altera o `this.state.message`valor. E quando clicamos no botão, aqui está como isso vai jogar fora:

ENTÃO É ISSO!!!
Se você quiser saber sobre as considerações finais e o quanto fazer esse código me ajudou, vê o artigo completo no meu Dev.to

<p class="text-center">
{% include elements/button.html link="https://dev.to/anabneri_8" text="VER ARTIGO COMPLETO NO DEV.TO" %}
</p>