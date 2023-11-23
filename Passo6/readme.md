# 6º Passo: Criar configuração com banco de dados

* Copiar url do repositório no gitHub
* Clonar repositório no computador com o gitBash
* Abrir o projeto no VSCode

<hr>

#### Clonar o repositório na sua máquina

* Abrir o gitBash em um local do computador
* Digitar o comando 'git clone' junto com a URL do seu repositório

```
git clone URL_REPOSITORIO
```

#### Acessar pasta
* Digitar o comando 'cd' e o nome do seu repositório
* cd (change directory): acessar outra pasta
```
cd NOME_REPOSITORIO
```

#### Reinstalar os pacotes da aplicação
```
npm i
```
* Este comando irá recriar a pasta node_modules no projeto

#### Recriar arquivo .env
* Definir as variáveis no arquivo .env a partir das chaves definidas no arquivo .env.example

### Criar a configuração com o banco de dados

#### Instalar o pacote mysql2

```
npm i mysql2
```

#### Dentro da pasta 'src', vamos criar uma pasta de nome 'config'. Dentro desta pasta vamos criar um arquivo com nome 'db.js' e colar o código:

```
// Arquivo responsável pela configuração e conexão com o banco de dados
 
// Importar o pacote do mysql
const mysql = require('mysql2');

// Importar o pacote de acesso aos de variáveis de ambiente
require('dotenv').config();

// Estabelece a criação da conexão com banco 
const connection = mysql.createConnection({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_DATABASE
    port: process.env.DB_PORT
});

// Testa se o banco esta conectado
connection.connect((err) => {
  if (err) {
    console.log(`Erro na conexão com banco: ${err}`);
  } else {
    console.log("Mysql Connected!");
  }
});

module.exports = connection;
```

#### Abrir o arquivo .env e digitar o conteúdo abaixo, conforme os comentários

```
# Definir a porta do servidor. Ex: 3000
PORT = 

# DB_HOST: Domínio do servidor. Ex: 'localhost'
# DB_USER: Usuário do banco de banco de dados. Ex: 'root'
# DB_PASSWORD: Senha do banco de banco de dados. Ex: 'root'
# DB_DATABASE: Nome da base de dados criada. Ex: 'projeto_final'
# DB_PORT: Porta que MySql está instalado. Ex: '3306' ou '3308'

DB_HOST = 
DB_USER = 
DB_PASSWORD =
DB_DATABASE =
DB_PORT =
```

## Conclusão do Passo 6

* Atualizar repositório no gitHub
