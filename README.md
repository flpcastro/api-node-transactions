# API NODE - TRANSACTIONS

## O que é necessário para testar essa aplicação?

- Ter o [Node.js](https://nodejs.org/en) instalado acima da versão 16.13.1;
- Algum Rest Client: [Insomnia](https://insomnia.rest/download), [Postman](https://www.postman.com/), [cURL](https://curl.se/), [Thunder](https://www.thunderclient.com/);

## Tecnologias utilizadas

- [Node.js](https://nodejs.org/en)
- [TypeScript](https://www.typescriptlang.org/)
- [Fastify](https://www.fastify.io/)
- [Knex](https://knexjs.org/)
- [SQLite3](https://www.sqlite.org/index.html)
- [Vitest](https://vitest.dev/)
- [Supertest](https://www.npmjs.com/package/supertest)
- [Zod](https://github.com/colinhacks/zod)

## Variáveis de Ambiente

Para rodar esse projeto, você vai precisar adicionar as seguintes variáveis de ambiente no seu .env

**API**

`PORT`

`NODE_ENV`

`DATABASE_URL`

**TEST**

`DATABASE_URL`

## Rodando localmente

Clone o projeto

```bash
  git clone https://github.com/flpcastro/api-node-transactions.git
```

Entre no diretório do projeto

```bash
  cd api-node-transactions
```

Instale as dependências

```bash
  yarn
```

Inicie o servidor

```bash
  yarn dev
```

## Funcionalidades

### Requisitos Funcionais

- [x] O usuário dever poder criar uma nova transação;
- [x] O usuário deve poder obter um resumo da sua conta;
- [x] O usuário deve poder listar todas transações que já ocorreram;
- [x] O usuário deve poder visualizar uma transação única;

### Regras de Negócios

- [x] A transação pode ser do tipo crédito que somará ao valor total, ou débito que irá substrair;
- [x] Deve ser possível identificarmos o usuário entre as requisições;
- [x] O usuário só pode visualizar transações o qual ele criou;

### Transação

**Criação**

```http
  POST '/transactions'
```

| Parâmetro | Tipo     | Descrição               |
| :-------- | :------- | :---------------------- |
| `title`   | `string` | Titulo da Transação.    |
| `amount`  | `number` | Valor da Transação.     |
| `type`    | `string` | Se é crédito ou débito. |

**Buscar todas**

```http
  GET /transactions
```

**Buscar pelo ID**

```http
  GET /transactions/{id}
```

**Buscar o resumo das transações apenas daquele usuário (uso de cookies)**

```http
  GET /transactions/summary
```

- Exemplo de Payload:

```json
{
  "title": "Freelancer",
  "amount": 5000,
  "type": "credit"
}
```

```json
{
  "title": "Hambúrguer",
  "amount": 50,
  "type": "debit"
}
```

- Exemplo de Requisição:

```sh
  curl -X POST \
  http://localhost:3333/transactions/ \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "Freelancer",
  "amount": 5000,
  "type": "credit",
  }'
```
