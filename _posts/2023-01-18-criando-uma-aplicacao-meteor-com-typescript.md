---
layout: single-article
title: "Criando uma aplicação com MeteorJS e Typescript"
date: 2023-01-18 18:35:00 -0300
categories: artigo
description: Vamos aprender passo a passo de como configurar e executar o MeteorJS com Typescript.
thumb: /assets/thumbs/20230118.png
tags:
  - meteorjs
  - nodejs
  - typescript
  - programação
  - backend
  - javascript
---

Meteor é uma plataforma de desenvolvimento web em tempo real que permite criar aplicativos da web usando JavaScript, enquanto o TypeScript é um superset de JavaScript que adiciona recursos de tipagem estática ao JavaScript. Juntos, eles oferecem uma experiência de desenvolvimento mais produtiva e robusta.

Para começar a criar uma aplicação com MeteorJS e TypeScript, você pode seguir os seguintes passos:

1) nstale o MeteorJS e o TypeScript
Certifique-se de ter o MeteorJS instalado em seu computador. Você também precisará instalar o TypeScript. Você pode instalar o TypeScript usando o npm (gerenciador de pacotes do Node.js) com o seguinte comando:
{% highlight shell %}
npm install -g typescript
{% endhighlight %}

2) Crie um novo projeto MeteorJS, use o comando `meteor create` para criar um novo projeto MeteorJS. Por exemplo:
{% highlight shell %}
meteor create my-app
{% endhighlight %}

3) Adicione suporte para TypeScript, execute o seguinte comando para adicionar suporte para TypeScript ao projeto MeteorJS:
{% highlight shell %}
meteor npm install --save typescript @types/meteor
{% endhighlight %}

4) Configure o TypeScript, crie um arquivo tsconfig.json na raiz do seu projeto e adicione as configurações do TypeScript. Aqui está um exemplo:
{% highlight json %}
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es2015",
    "sourceMap": true,
    "outDir": ".meteor/local/build/programs/server",
    "baseUrl": ".",
    "paths": {
      "*": ["typings/*"]
    }
  },
  "exclude": [
    "node_modules",
    ".meteor",
    "typings/main",
    "typings/main.d.ts"
  ]
}
{% endhighlight %}

5) Crie seus arquivos TypeScript, crie seus arquivos TypeScript na pasta `imports` do seu projeto. Por exemplo, você pode criar um arquivo `main.ts` na pasta `imports/server` com o seguinte conteúdo:
{% highlight javascript %}
import { Meteor } from 'meteor/meteor';

Meteor.startup(() => {
  console.log('Hello, world!');
});
{% endhighlight %}

6) Execute o comando `meteor` para iniciar o servidor MeteorJS e navegue para `http://localhost:3000` em seu navegador para ver o aplicativo em execução.

Pronto! Agora sua aplicação MeteorJS está rodando com TypeScript.
