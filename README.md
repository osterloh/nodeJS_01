<h1 align="center" style="background-color: #100112;">
    <img alt="nodeJS" src="https://nodejs.org/static/images/logo.svg" width="50%"/>
    <br>
    Introdução ao nodeJS
</h1>

## Descrição

Este projeto está sendo desenvolvido em <strong>[nodeJS](https://nodejs.org/)</strong> para fins de capacitação pessoal

## Etapas

- Antes de iniciar o projeto nodeJS, é necessário definir em qual diretório o projeto irá ficar armazendo e executar o comando para criar o arquivo <strong>package.json</strong>, o qual irá conter informações sobre o projeto e bibliotecas adicionadas:

```js
yarn init -y
```

- Para definição de rotas, endereços e retornos, está sendo utilizado o <strong>Express</strong>, que é uma biblioteca que gerencia esse tipo de serviço no projeto.

```js
yarn add express
```

- No projeto, vamos importar o <strong>express</strong> em uma váriável chamada <i>express</i> e declarar uma variável chamada <i>app</i> a qual irá receber o express importado, podendo assim ser utilizado no projeto. Para poder acessar o projeto pelo navegador, será definido uma porta padrão para o projeto utilizando o localhost, neste caso a porta <strong>3333</strong>, para definir esta porta vamos utilizar o método <strong>.listen()</strong> do express. E para apresentar algum conteúdo no navegador será utilizado o método <strong>.get()</strong>, o qual recebe dois parâmetros, sendo o primeiro a <u>rota</u> utilizada e o segundo uma <u>função</u> que retornará o conteúdo. Essa função também recebe dois parâmetros sendo o primeiro uma <u>requisição (request)</u> e o segundo uma <u>resposta (response)</u>, nesta função iremos retornar uma mensagem ('Hello World') através do <strong>response.send()</strong>, que é uma função que retorna um texto.

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

- Para rodar o projeto sem definir uma rota padrão, basta informar somente a '<strong>/</strong>' no parâmetro de rota do método <strong>.get()</strong>. E para retornar dados em uma estrutura <i>JSON</i>, podemos utilizar o <strong>response.json()</strong>.

```js
const express = require("express");

const app = express();

app.get("/", (request, response) => {
  return response.json({ message: "Hello World" });
});

app.listen(3333);
```

- Para manter o projeto atualizado no navegador, sem ser necessário reiniciar o servidor a cada alteração realizada no código, podemos utilizar a biblioteca <strong>Nodemon</strong>, sendo instalada como uma dependência de <b>D</b>esenvolvedor.

```js
yarn add nodemon -D
```

- Com o Nodemon instalado, podemos startar o projeto com o comando abaixo, informando o diretório e o nome do projeto. Com o nodemon, basta realizar as alterações nos códigos, salvar as alterações e atualizar o navegador que o projeto será atualizado:

```js
yarn nodemon src/index.js
```

- Para possuir algum retorno no terminal, referente ao estado do servidor, no método <strong>.listen()</strong> é possível passar uma função que retorne alguma mensagem.

```js
app.listen(3333, () => {
  console.log("🚀️Back-end started!");
});
```

## Tecnologias

- [nodeJS](https://nodejs.org/)
- [yarn](https://yarnpkg.com/)
- [express](https://github.com/expressjs/express)
- [nodemon](https://github.com/remy/nodemon)

---

Desenvolvido por [Johnatan Luiz Osterloh](https://www.linkedin.com/in/johnatanosterloh/)
