---
layout: single-article
title: "Fazendo requisições GET, POST, PUT e DELETE em Nodejs"
date: 2022-01-12 00:00:00 -0300
categories: artigo
description: Como fazer requisições GET, POST, PUT e DELETE utilizando Nodejs e Express.
thumb: /assets/thumbs/20220112.png
tags:
  - video aula
  - nodejs
  - backend
  - requests
  - expressjs
---

Com o Express.js, você pode escrever rotas que respondem a diferentes tipos de solicitações HTTP, incluindo GET, POST, PUT e DELETE. Aqui está um exemplo de como escrever rotas para cada um desses métodos de solicitação HTTP:

```javascript
const express = require('express');
const app = express();

// requisição GET 
app.get('/api/users', (req, res) => {
  // Seu código aqui
});

// requisição POST
app.post('/api/users', (req, res) => {
  // Seu código aqui
});

// requisição PUT
app.put('/api/users/:id', (req, res) => {
  // Seu código aqui
});

// requisição DELETE
app.delete('/api/users/:id', (req, res) => {
  // Seu código aqui
});
```

Observe que cada rota tem um caminho diferente (<code>/api/users</code> ou <code>/api/users/:id</code>) e uma função de retorno de chamada que será executada quando essa rota for acessada. A função de retorno de chamada recebe dois parâmetros: o objeto de solicitação <code>req</code> e o objeto de resposta <code>res</code>.

Para enviar dados em uma solicitação POST, você pode usar o método <code>req.body</code>. Para obter dados de uma solicitação PUT ou DELETE, você pode usar o <code>req.params</code> para obter os parâmetros na URL.

Esse é um exemplo de como enviar uma solicitação POST com o corpo JSON:

```javascript
app.post('/api/users', (req, res) => {
  const user = req.body;
  // Seu código aqui
});
```

Esse é um exemplo de como obter um parâmetro na URL de uma solicitação PUT:

```javascript
app.put('/api/users/:id', (req, res) => {
  const id = req.params.id;
  // Seu código aqui
});
```

Esses são apenas alguns exemplos básicos de como escrever rotas HTTP usando o Express.js. Existem muitas outras coisas que você pode fazer com o Express, como validar entrada de usuário, autenticação de usuário, manipulação de erros, etc.
