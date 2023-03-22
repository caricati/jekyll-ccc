---
layout: single-article
title: Você está vacilando se não usa closures
date: 2023-03-22 09:21:00 -0300
categories: artigo
description: A closure é uma função que tem acesso a variáveis ​​em seu escopo léxico, mesmo após a função ter retornado. Isso significa que uma closure pode "lembrar" do ambiente em que foi criada, incluindo variáveis, funções e parâmetros que estavam disponíveis naquele momento.
thumb: /assets/thumbs/20230322.png
tags:
  - javascript
  - funcional
  - design patterns
  - programação
  - closures
---

A closure é uma função que tem acesso a variáveis ​​em seu escopo léxico, mesmo após a função ter retornado. Isso significa que uma closure pode "lembrar" do ambiente em que foi criada, incluindo variáveis, funções e parâmetros que estavam disponíveis naquele momento.

As closures são implementadas de forma simples em JavaScript. Elas podem ser criadas definindo uma função dentro de outra função e retornando essa função interna. A função interna tem acesso ao escopo da função externa e pode acessar variáveis, funções e parâmetros dessa função externa, mesmo após a função externa ter retornado. Veja um exemplo:

```javascript
function exterior(x) {
  function interior(y) {
    return x + y;
  }
  return interior;
}

const minhaFuncao = exterior(5);
console.log(minhaFuncao(10)); // Output: 15
```

No exemplo acima, a função `exterior` retorna a função interna `interior`, que tem acesso à variável `x` da função `exterior`. A variável `x` é lembrada mesmo depois que a função `exterior` terminou de executar, porque a função `interior` é uma closure que "lembra" do ambiente em que foi criada.

É importante notar que closures podem ser usadas para criar funções com comportamentos diferentes e personalizados, porque cada closure mantém seu próprio estado interno. Por exemplo:

```javascript
function contador() {
  let contador = 0;
  return function() {
    contador++;
    console.log(contador);
  }
}

const incrementar = contador();

incrementar(); // Output: 1
incrementar(); // Output: 2
incrementar(); // Output: 3
```

Nesse exemplo, a função `contador` retorna uma closure que "lembra" do valor da variável `contador`. A cada vez que a função interna é chamada, a variável `contador` é incrementada e o valor atual é impresso no console. Como a closure mantém o valor atual de `contador`, cada vez que a função interna é chamada, ela usa o valor incrementado da variável.

É muito comum ver funções sendo criadas e executadas ao mesmo tempo. Para quem já trabalhou com jQuery já viu muitas vezes isso ser utilizado.

```javascript
(function(){
  /// ...
}())
```

Neste exemplo podemos perceber que essa função é criada e executada logo em seguida com `()`. Isso faz com que tudo que for declarado neste escopo fique por lá, criando assim um ambiente mais protegido e evitando declarações globais. Para quem gosta de usar *Static Single Assignment* em JavaScript, utilizar closures é essencial.
