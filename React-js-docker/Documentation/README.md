# Criando e Dockerizando um Projeto React com JavaScript

Este guia irá ajudá-lo a criar um projeto React utilizando JavaScript e dockerizar a aplicação para rodá-la em contêineres.

## Pré-requisitos

- Ter o [Node.js e NVM](https://nodejs.org/pt/download/package-manager) instalados.

## 1. Criando a Aplicação React

### 1.1. Criar o Diretório da Aplicação

No terminal, navegue até o local onde deseja criar o projeto e execute:

```bash
mkdir react-js-docker
cd react-js-docker
```

### 1.2. Use o comando `npx` para criar um projeto Vite.
```bash
 - Ao ser solicitado, selecione:

 - Framework: React
 - Variant: JavaScript
```
 
### 1.3. Instale as dependências do projeto com o seguinte comando:
```bash
npm install
```

### 1.4. Execute a aplicação localmente para garantir que tudo está funcionando corretamente:
```bash
npm run dev
```

### Você verá no terminal algo como:
```bash
VITE v5.x.x  ready in 300 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
```
### Pare a aplicacao com o comando:
```bash
Ctrl + c
```

## 2. Dockerizando o Projeto

### 2.1. Crie na raiz do projeto:
 - `dockerfile`
 - `docker compose`
 - `.env.exemple`
 - Crie uma cópia do arquivo .env.example e renomeie para .env:
```bash
cp .env.example .env
```

### 2.2. Adicione o arquivo .env ao .gitignore para que ele não seja versionado no Git. No arquivo .gitignore, adicione no final do arquivo:
```bash
# env
.env
```

### 2.3. Abra o arquivo package.json e altere a linha do script dev para expor o host, garantindo que o Vite funcione dentro do Docker:
```bash
  "scripts": {
    "dev": "vite --host"
  }
```

### 2.4. Construir a Imagem Docker
Execute o seguinte comando para construir a imagem Docker da aplicação:
```bash
docker compose build
```
### 2.5. Rodar o Contêiner
Depois que a imagem for construída, você pode iniciar o contêiner com o comando:
```bash
docker compose up
```
A aplicação será iniciada e estará acessível em http://localhost:5173.

### 2.6. Parando o Contêiner
Para parar o contêiner, basta usar o comando:
```bash
docker compose stop
```