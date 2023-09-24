# 2º Passo: Criar configuração da API e testar

* Configurar pacotes instalados
* Criar comando para rodar o servidor
* Testar funções para retornar mensagens através do servidor

#### Criar arquivo .env na raiz do projeto
```
nano .env
```
* Este arquivo é utilizada para armazenar as variáveis que serão reutilizadas na aplicação
* Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo

#### Adicionar no arquivo .env
```
PORT = 3000
```
* Variável que contém a porta que o servidor estará rodando
* Esta arquivo .env não enviamos pro gitHub, pois contém informações sensíveis do sistema

#### Adicionar no arquivo .gitignore
```
.env
```

#### Criar arquivo de exemplo para para as variáveis necessárias da aplicação
```
nano .env.example
```
* Como não enviamos o arquivo .env para o gitHub, precisamos criar o exemplo das variáveis necessárias da aplicação
* Este arquivo conterá apenas as variáveis, sem os valores correspondentes

#### Adicionar no arquivo .env.example
```
PORT = 
```

<img src="">

#### Abrir o arquivo app.js e digitar o código

```
const express = require('express');
```
* Importar o pacote express (servidor)

```
const dotenv = require('dotenv').config();
```
* Importar o pacote dotenv, gerenciador de variáveis de ambiente


```
const app = express();
```
* Instanciar o express na variável app

```
app.set('port', process.env.PORT || 3333);
```
* Setar a porta do servidor a parir do arquivo .env
* O operador condicional '||' significa 'OU', caso não tenha a variável PORT, será utilizado o valor '3333'

```
module.exports = app;
```
* Exportar as configurações na variável app

<img src="">


#### Abrir o arquivo server.js e digitar o código
```
const app = require('./app');
```
* Importar o arquivo app
```
const port = app.get('port');
```
* Importar a porta do servidor
```
app.listen(port, () => console.log(`Run on port ${port}!`));
```
* Testar API com a função listen, passando a porta que definimos no arquivo .env

<img src="">

## Depois de configurar os pacotes e o teste do servidor, vamos criar o comando para executar

#### Abrir o arquivo package.json e alterar a chave 'scripts'
```
"start":"nodemon src/server.js"
```
* Substituir o comando 'test' pelo comando 'start' na linha 7

#### Rodar o comando no termial com gitBash
```
nom run start
```

<img src="">