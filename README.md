<h1 align="center"><a href="https://nodejs.org/" target="_blank" style="text-decoration: none">
    <img alt="nodeJS" src="https://camo.githubusercontent.com/9c24355bb3afbff914503b663ade7beb341079fa/68747470733a2f2f6e6f64656a732e6f72672f7374617469632f696d616765732f6c6f676f2d6c696768742e737667" width="50%"/>
    <br>
    Introdução ao nodeJS
</a></h1>

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

- Métodos HTTP: GET, POST, PUT/PATCH e DELETE:

```bash
* GET: Buscar informações do back-end;
* POST: Criar uma informação no back-end;
* PUT/PATCH: Alterar uma informação no back-end;
* DELETE: Deletar uma informação no back-end;
```

```js
app.get("/projects", (request, response) => {
  return response.json(["Projeto 1", "Projeto 2"]);
});

app.post("/projects", (request, response) => {
  return response.json(["Projeto 1", "Projeto 2", "Projeto 3"]);
});

app.put("/projects/:id", (request, response) => {
  return response.json(["Projeto 4", "Projeto 2", "Projeto 3"]);
});

app.delete("/projects/:id", (request, response) => {
  return response.json(["Projeto 4", "Projeto 3"]);
});
```

- Tipos de parâmetros: Query Params, Route Params, Request Body. São formas do front-end enviar algum tipo de informação

```bash
* Query Params: Utilizado principalmente para Filtros e paginação. É o conteúdo que vem após o ? na rota: http://localhost:3333/projects?title=React&owner=Johnatan;
* Route Params: Utilizado para identificar recursos para Atualizar ou Deletar. É o identificador, :id, informado após a rota: http://localhost:3333/projects/1;
* Request Body: Utilizado para o conteúdo na hora de criar ou editar um recurso, vindo através de um JSON. Porém para que o Express consiga interpretar o formato de JSON, é necessário informar o express.json() no método use(): app.use(express.json()) que deve ser declarado antes das rotas;
```

- Para retornar todos os dados dos parâmetros, Query Params:

```js
app.get("/projects", (request, response) => {
  const query = request.query;
  console.log(query);
  return response.json(["Projeto 1", "Projeto 2"]);
});
```

- Para desestruturar os parâmetros em variáveis isoladas, Query Params:

```js
app.get("/projects", (request, response) => {
  const { title, owner } = request.query;

  console.log(title);
  console.log(owner);

  return response.json(["Projeto 1", "Projeto 2"]);
});
```

- Para retornar todos os dados dos parâmetros, Route Params:

```js
app.put("/projects/:id", (request, response) => {
  const params = request.params;
  console.log(params);
  return response.json(["Projeto 4", "Projeto 2", "Projeto 3"]);
});
```

- Para desestruturar os parâmetros em variáveis isoladas, Route Params:

```js
app.put("/projects/:id", (request, response) => {
  const { id } = request.params;
  console.log(id);
  return response.json(["Projeto 4", "Projeto 2", "Projeto 3"]);
});
```

- Para retornar todos os dados dos parâmetros, Request Body;

```js
app.post("/projects", (request, response) => {
  const body = request.body;
  console.log(body);
  return response.json(["Projeto 1", "Projeto 2", "Projeto 3"]);
});
```

- Para desestruturar os parâmetros em variáveis isoladas, Request Body;

```js
app.post("/projects", (request, response) => {
  const { title, owner } = request.body;
  console.log(title);
  console.log(owner);
  return response.json(["Projeto 1", "Projeto 2", "Projeto 3"]);
});
```

- Declaração do <b>use()</b>:

```js
const app = express();
app.use(express.json());
```

- Para tornar a aplicação funcional, vamos criar uma variável, antes das rotas, do tipo vetor para receber os dados que serão adiconados no projeto.

```js
const projects = [];
```

- Para a rota GET, vamos retornar o array com os dados cadastrados.

```js
app.get("/projects", (request, response) => {
  return response.json(projects);
});
```

- Para a rota POST/PUT/DELETE, é necessário os dados possuirem uma key própria, para poder ser alterado ou deletado a informação cujo ID corresponda com o informado, para isso vamos instalar e importar em nosso projeto a biblioteca <b>[UUIDV4](https://github.com/thenativeweb/uuidv4)</b>.

```bash
yarn add uuidv4
```

```js
const { uuid } = require("uuidv4");
```

- Na rota POST, vamos criar um objeto que vai receber um ID do tipo UUID, com os demais dados que estamos utilizando e adicionar esse objeto no final do array utilizando o método <b>push()</b>, por fim retornar o objeto criado.

```js
app.post("/projects", (request, response) => {
  const { title, owner } = request.body;
  const project = { id: uuidv4(), title, owner };
  projects.push(project);
  return response.json(project);
});
```

- Para a rota PUT, atualizar um dado no projeto, vamos utilizar o método <b>findIndex()</b> para encontrar o index do dado que será alterado no array, caso o index não seja encontrado será retornado <i>status code 400</i> com uma mensagem de erro, caso o index seja será criado um novo objeto com as informações alteradas e esse objeto será adicionado no array na posição do index encotrado, substituido assim os dados armazenados naquela posição do array e por fim retornado o objeto criado.

```js
app.put("/projects/:id", (request, response) => {
  const { id } = request.params;
  const { title, owner } = request.body;
  const projectIndex = projects.findIndex((project) => project.id === id);
  if (projectIndex < 0) {
    return response.status(400).json({ error: "Project not found." });
  }
  const project = {
    id,
    title,
    owner,
  };
  projects[projectIndex] = project;
  return response.json(project);
});
```

- Na rota DELETE, vamos utilizar a mesma ideia da rota PUT para localizar o index do dado a ser removido do array e para remover a informação utilizaremos o método <b>splice()</b> informando a quantia de elementos que deve ser removido apartir daquele index, neste caso somente 1 elemento e em seguida apresentar um <i>status code 204</i> que significa um conteúdo vazio.

```js
app.delete("/projects/:id", (request, response) => {
  const { id } = request.params;
  const projectIndex = projects.findIndex((project) => project.id === id);
  if (projectIndex < 0) {
    return response.status(400).json({ error: "Project not found." });
  }
  projects.splice(projectIndex, 1);
  return response.status(204).send();
});
```

- Na rota GET, podemos aplicar um filtro para retornar somente dados específicos e não todos, para isso podemos criar uma variável com um if ternário que irá verificar com o método <b>filter()</b> se o dado que está sendo filtrado contém no array, caso o dado esteja contido no array o retorno será somente dos dados filtrados, caso contrário o retorno será de todos os dados aramazenados no array.

```js
app.get("/projects", (request, response) => {
  const { title } = request.query;
  const results = title
    ? projects.filter((project) => project.title.includes(title))
    : projects;
  return response.json(results);
});
```

## Tecnologias

- [nodeJS](https://nodejs.org/)
- [yarn](https://yarnpkg.com/)
- [express](https://github.com/expressjs/express)
- [nodemon](https://github.com/remy/nodemon)
- [uuidv4](https://github.com/thenativeweb/uuidv4)

---

Desenvolvido por [Johnatan Luiz Osterloh](https://www.linkedin.com/in/johnatanosterloh/)
