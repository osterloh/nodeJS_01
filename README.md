<h1 align="center">
    <img alt="nodeJS" src="https://nodejs.org/static/images/logo.svg" width="50%"/>
    <br>
    Introdução ao nodeJS
</h1>

## Descrição

Este projeto está sendo desenvolvido em [nodeJS](https://nodejs.org/) para fins de capacitação pessoal

## Etapas

- Antes de iniciar o projeto nodeJS, é necessário definir em qual diretório o projeto irá ficar armazendo e executar o comando para criar o arquivo <strong>package.json</strong>, o qual irá conter informações sobre o projeto e bibliotecas adicionadas:

```js
yarn init -y
```

- Para definição de rotas, endereços e retornos, está sendo utilizado o <strong>Express</strong>, que é uma biblioteca que gerencia esse tipo de serviço no projeto.

```js
yarn add express
```

- No projeto, vamos importar o express em uma váriável chamada express e declarar uma variável chamada app a qual irá receber o express importado, podendo assim ser utilizado no projeto. Para poder acessar o projeto pelo navegador, será definido uma porta padrão para o projeto utilizando o localhost, neste caso com a porta 3333, para definir esta porta vamos utilizar o método listen do express. E para apresentar algum conteúdo no navegador será utilizado o método get, o qual recebe dois parâmetros, sendo o primeiro a rota utilizada e o segundo uma função que retornará o conteúdo. Essa função também recebe dois parâmetros sendo o primeiro uma requisição (request) e o segundo uma resposta (response), nesta função iremos retornar uma mensagem ('Hello World') através do response.send(), que é uma função que retorna um texto.

```js
const express = require("express");

const app = express();

app.get("/projects", (request, response) => {
  return response.json("Hello World");
});

app.listen(3333);
```

- Para compilar o projeto:

```js
node src/index.js
```

- Para rodar o projeto sem definir uma rota padrão, basta informar somente a '/' no parâmetro de rota do método get. E para retornar dados em uma estrutura JSON, podemos utilizar o response.json().

```js
const express = require("express");

const app = express();

app.get("/", (request, response) => {
  return response.json({ message: "Hello World" });
});

app.listen(3333);
```

## Tecnologias

- [nodeJS](https://nodejs.org/)
- [yarn](https://yarnpkg.com/)
- [express](https://github.com/expressjs/express)

---

Desenvolvido por [Johnatan Luiz Osterloh](https://www.linkedin.com/in/johnatanosterloh/)
