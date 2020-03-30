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

# Instalando o Knex para Nodejs
## O que é o knex?
Ele reinicia automaticamente o aplicativo do nó quando alterações de arquivo no diretório são detectadas
### E como instalar?
Para instalar o knex, basta executar o seguinte comando:
```sh
$ npm install knex

$ npm install pg
$ npm install sqlite3
$ npm install mysql
$ npm install mysql2
$ npm install oracledb
$ npm install mssql
```

> O Comando acima: npm install knexvai modificar o package.json, colocando o pacote do knex como uma dependência do projeto
> Acima listo algumas instalaçãoes especificas de bancos para utilizar o mariaDB, basta utilizar a instalação do mysql

### Iniciando um knex
Para iniciar o knex, basta executar o seguinte comando:
```sh
$ npx knex init
```

> O Comando acima: npx knex init vai criar um arquivo de configuração chamado knexfile.js

```sh
module.exports = {

  development: {
    client: 'sqlite3',
    connection: {
      filename: './dev.sqlite3'
    }
  }
}
```

### Criando migrations no knex
basta adicionar uma flag na tag "development"
```sh
module.exports = {

  development: {
    client: 'sqlite3',
    connection: {
      filename: './dev.sqlite3'
    },
    migations:{
        directory: './migration'
    }
  }

}
```

Migration é tipo um controlador de versão do banco de dados
Para iniciar um migrate, basta executar o seguinte código
```sh
$ npx knex migrate:make create_users
```

> O Comando acima: npx knex migrate:make create_users vai criar um arquivo de versão dentro da pasta "migration", abaixo segue um exemplo do arquivo
```sh
exports.up = function(knex) {
  return knex.schema.createTable('users', function(table){
    table.increments();
    table.string('name');
    table.timestamps();
  })
};

exports.down = function(knex) {
    return knex.schema.dropTable('users');
};
```

Para executar um migrate, basta executar o seguinte código
```sh
$ npx knex migrate:latest create_users
```

> O Comando acima: npx knex migrate:latest create_users vai executar o arquivo de da migarete referente ao name, no caso "create_users"
> O mesmo vai criar o banco de dados, conforme informado na flag "development.connection.filename"

Para criar uma conexão, basta criar um arquivo e colocar o seguinte código

```sh
const knex = require('knex');
const configuration = require('./knexfile');

const connection = knex(configuration.development);

module.exports = connection;
```