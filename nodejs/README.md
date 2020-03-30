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
    "test": "nodemon ./src/index.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
  }
}
```