---
layout: single-article
title: "Autenticação com Nodejs e JWT"
date: 2022-08-28 00:00:00 -0300
categories: artigo
description: Vamos implementar uma autenticação JWT (JSON Web Tokens) com Nodejs, passo a passo. 
thumb: /assets/thumbs/20220828.png
tags:
  - video aula
  - nodejs
  - backend
  - requests
  - expressjs
  - jwt
  - autenticação
---

Para fazer autenticação com o Express utilizando JWT (JSON Web Tokens), você precisa seguir alguns passos.

1) Instale as dependências necessárias:
{% highlight shell %}
npm install express jsonwebtoken bcryptjs body-parser
{% endhighlight %}

2) Configure seu servidor Express para usar o <code>body-parser</code> para analisar o corpo da solicitação e o <code>json</code> como formato de resposta padrão:
{% highlight javascript %}
const express = require('express');
const app = express();
const bodyParser = require('body-parser');

app.use(bodyParser.json());
{% endhighlight %}

3) Crie rotas para o login e o registro de usuários. No exemplo abaixo, o usuário envia seu nome de usuário e senha no corpo da solicitação:
{% highlight javascript %}
const bcrypt = require('bcryptjs');
const jwt = require('jsonwebtoken');

const users = [];

// Rota de registro de usuário
app.post('/register', async (req, res) => {
  try {
    const hashedPassword = await bcrypt.hash(req.body.password, 10);
    const user = { name: req.body.name, password: hashedPassword };
    users.push(user);
    res.status(201).send();
  } catch {
    res.status(500).send();
  }
});

// Rota de login de usuário
app.post('/login', async (req, res) => {
  const user = users.find(user => user.name === req.body.name);
  if (!user) {
    return res.status(400).send('Usuário não encontrado');
  }
  try {
    if (await bcrypt.compare(req.body.password, user.password)) {
      const token = jwt.sign({ name: user.name }, 'secretkey');
      res.status(200).send({ token });
    } else {
      res.status(401).send('Senha incorreta');
    }
  } catch {
    res.status(500).send();
  }
});
{% endhighlight %}

4) Crie uma rota protegida que exige autenticação. Para fazer isso, crie uma função de middleware que verifica se o token JWT é válido e, em seguida, a use na rota que deseja proteger:
{% highlight javascript %}
function authenticateToken(req, res, next) {
  const authHeader = req.headers['authorization'];
  const token = authHeader && authHeader.split(' ')[1];
  if (token == null) return res.status(401).send('Token não encontrado');

  jwt.verify(token, 'secretkey', (err, user) => {
    if (err) return res.status(403).send('Token inválido');
    req.user = user;
    next();
  });
}

// Rota protegida
app.get('/protected', authenticateToken, (req, res) => {
  res.send(`Olá, ${req.user.name}!`);
});
{% endhighlight %}

5) Para testar a rota protegida, faça uma solicitação GET para /protected com um cabeçalho Authorization que contém o token JWT:
{% highlight makefile %}
Authorization: Bearer <token>
{% endhighlight %}

Isso é um exemplo básico de como fazer autenticação com o Express usando JWT. Obviamente, existem muitas outras coisas que você pode fazer para tornar sua autenticação mais segura e robusta, como verificar o nome de usuário e a senha em um banco de dados, usar HTTPS e muito mais.


## O que significa Bearer?

A palavra "Bearer" é usada no contexto de autenticação HTTP com tokens JWT. Na autenticação com tokens JWT, o token é enviado como um cabeçalho HTTP de autorização usando o esquema "Bearer".

O termo "Bearer" em si se refere ao titular ou portador do token. No contexto da autenticação JWT, "Bearer" é usado para indicar que o valor do token enviado no cabeçalho de autorização é um token JWT válido e que o usuário associado a esse token tem permissão para acessar os recursos protegidos pelo servidor.

Por exemplo, um cabeçalho de autorização válido com um token JWT poderia ser o seguinte:

{% highlight makefile %}
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
{% endhighlight %}

Neste exemplo, a palavra "Bearer" indica que o token JWT é válido e que o usuário associado a ele tem permissão para acessar os recursos protegidos pelo servidor.
