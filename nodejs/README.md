# Instalando o Nodejs
## O que é o nodejs?
Nodejs é uma ferramente que incorpora a engine v8 javascript do Chrome, ou seja ele roda aplicações em javascript sem necessáriamente estar no navegador
### E como instalar?
Para instalações windows - por linha de comando -  basta seguir as etapas, clicando aqui https://nodejs.org/en/download/package-manager/#windows

### Iniciando um projeto
Para iniciar um projeto, basta executar o seguinte comando:
```sh
$ mkdir nameproject
$ cd nameproject
$ npm init -y
```

> O Comando acima: npm init -y vai criar o arquivo package.json
```sh
{
  "name": "nameproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

# Instalando o Express para Nodejs
## O que é o express?
É um tipo de estrutura de servidor padrão de fato para o Node.js, utilizado bastante para criação de rotas
### E como instalar?
Para instalar o express, basta executar o seguinte comando:
```sh
$ npm install express
```

> O Comando acima: npm install express vai modificar o package.json, colocando o pacote do express como uma dependência do projeto
> Além disse ele vai criar uma pasta chamada node_modules, é nela que todo pacote e dependência será instalado
```sh
{
  "name": "nameproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
### Para testar o express:
Crie um arquivo chamado index.js e nele adicione o seguinte comando
```sh
const express = require('express');
const app = express();

app.listen(3333);
```

Para testar basta executar o seguinte comando:
```sh
$ node index.js
```

# Instalando o Nodemon para Nodejs
## O que é o nodemon?
Ele reinicia automaticamente o aplicativo do nó quando alterações de arquivo no diretório são detectadas
### E como instalar?
Para instalar o nodemon, basta executar o seguinte comando:
```sh
$ npm install nodemon -D
```

> O Comando acima: npm install nodemon -D vai modificar o package.json, colocando o pacote do nodemon como uma dependência do projeto
> Porém como acrescentamos o "-D" a dependência será instalada como Dev, para que não seja explanado para produção essa dependência de monitoramento
```sh
{
  "name": "nameproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  },
  "devDependencies": {
    "nodemon": "^2.0.2"
  }
}

```

### Para testar o express:
basta adicionar uma flag na tag "scripts"
```sh
{
  "name": "nameproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon ./index.js"
  },...
```

Para testar basta executar o seguinte comando:
```sh
$ npm start
```