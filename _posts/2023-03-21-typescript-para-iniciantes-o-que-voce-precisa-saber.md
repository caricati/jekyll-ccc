---
layout: single-article
title: "TypeScript para iniciantes: O que você precisa saber"
date: 2023-03-20 22:28:00 -0300
categories: artigo
description: Se você está começando com o TypeScript, comece por aprender os conceitos básicos de tipagem estática, como criar interfaces e tipos, e como usar esses recursos para criar código mais legível e estruturado...
thumb: /assets/thumbs/20230321.png
tags:
  - typescript
  - javascript
  - programação
  - frontend
  - backend
---

Se você está começando com o TypeScript, comece por aprender os conceitos básicos de tipagem estática, como criar interfaces e tipos, e como usar esses recursos para criar código mais legível e estruturado. Em seguida, continue aprendendo sobre recursos mais avançados, como classes, tipos genéricos e tipos de união e interseção, para criar código mais flexível e reutilizável.

TypeScript é uma linguagem de programação que estende o JavaScript, adicionando recursos de tipagem estática e outros recursos avançados para tornar o código mais fácil de ler, entender e manter. Além disso, é totalmente compatível com o JavaScript, o que significa que você pode usar código JavaScript existente em projetos TypeScript e que o TypeScript pode ser compilado para JavaScript padrão.

O TypeScript usa a sintaxe do JavaScript padrão, com a adição de recursos de tipagem estática. Isso significa que a maior parte do código JavaScript que você já conhece será facilmente transferível para o TypeScript e é usada uma abordagem de tipagem opcional, o que significa que você pode escolher quando e onde adicionar tipos. Isso permite que você gradualmente adicione tipos ao seu código e aproveite os benefícios da tipagem estática, mesmo em projetos existentes.

Além de ter uma grande comunidade de desenvolvedores, com muitos recursos disponíveis, como bibliotecas, frameworks e ferramentas de desenvolvimento, oferece recursos avançados, como classes, interfaces, tipos genéricos, tipos de união e interseção, e muito mais. Isso permite que você crie código mais estruturado e flexível.

Vamos conhecer um pouco mais sobre as mágicas do TypeScript neste artigo.

## Tipos

Podemos assinar os tipos em uma variável, assim que criamos ela, dessa forma:

```typescript
let idade: number;
```

Isso define a variável "idade" como um número. Agora, você pode atribuir um valor numérico a essa variável:

```typescript
idade = 30;
```

Também é possível atribuir um valor à variável ao mesmo tempo em que ela é declarada:

```typescript
let idade: number = 30;

```

O TypeScript também oferece uma série de tipos embutidos, como `string`, `number`, `boolean`, `array`, `object`, entre outros. Para usar esses tipos, basta declarar a variável com o tipo correspondente:

```typescript
let nome: string = "João";
let idade: number = 30;
let isAtivo: boolean = true;
let listaDeNumeros: number[] = [1, 2, 3, 4, 5];
let objeto: { propriedade1: string, propriedade2: number } = { propriedade1: "valor1", propriedade2: 123 };
```

Também podemos utilizar a palavra reservada `type` para atribuir tipos. O `type` é uma palavra-chave que permite definir um novo tipo com base em um tipo existente ou combinando vários tipos. Por exemplo, você pode criar um novo tipo chamado Idade que é um alias para o tipo number da seguinte forma:

```typescript
type Idade = number;
```

Isso significa que sempre que você usar `Idade` em vez de `number`, será a mesma coisa em termos de como a variável ou parâmetro é tratado pelo compilador.

Você também pode usar o `type` para definir tipos mais complexos, como objetos ou tipos de função. Por exemplo, para definir um tipo de objeto para um usuário com nome e idade, você pode escrever o seguinte:

```typescript
type Usuario = {
  nome: string;
  idade: number;
}
```

Isso define um tipo chamado `Usuario` que é um objeto com as propriedades `nome` e `idade`. Você pode usar esse tipo para definir variáveis ou parâmetros que devem ser objetos de usuário.

O `type` também pode ser usado para combinar vários tipos existentes em um novo tipo. Por exemplo, para criar um tipo que pode ser um número ou uma string, você pode escrever o seguinte:

```typescript
type NumeroOuString = number | string;
```

Isso define um tipo chamado `NumeroOuString` que pode ser qualquer coisa que seja um número ou uma string.

Em resumo, o `type` é uma ferramenta poderosa em TypeScript que permite criar tipos personalizados e combinados para tornar seu código mais legível e fácil de manter.

## Interfaces

As interfaces são usadas para definir contratos que um objeto deve cumprir. As interfaces descrevem a forma de um objeto, especificando quais propriedades e métodos ele deve ter. As interfaces são escritas com a palavra-chave `interface`, seguida do nome da interface e do corpo da interface, que contém as definições de propriedades e métodos.

Para escrever interfaces, você pode seguir a sintaxe básica abaixo:

```typescript
interface NomeDaInterface {
  propriedade1: tipo;
  propriedade2: tipo;
  ...
}
```

Para criar uma interface para um objeto do usuário com as propriedades "nome", "email" e "idade", você pode escrever o seguinte:

```typescript
interface Usuario {
  nome: string;
  email: string;
  idade: number;
}
```

Isso define uma interface chamada "Usuario" com as propriedades "nome", "email" e "idade", onde "nome" e "email" são strings e "idade" é um número.

Você pode usar interfaces para definir a estrutura de objetos e verificar se os objetos atendem a essa estrutura. Por exemplo, você pode criar um objeto do usuário que atenda à interface "Usuario" como este:

```typescript
const usuario: Usuario = {
  nome: 'João',
  email: 'joao@example.com',
  idade: 30
}
```

Isso criará um objeto "usuario" que possui as propriedades "nome", "email" e "idade", que correspondem à estrutura definida na interface "Usuario".

## As diferenças entre `Type` e `Interface`

Tanto as interfaces quanto os tipos (definidos com a palavra-chave type) são recursos do TypeScript para definir tipos personalizados. Embora haja semelhanças entre eles, também existem algumas diferenças importantes.

A principal diferença entre interfaces e tipos é que as interfaces são utilizadas principalmente para definir a estrutura de um objeto, enquanto os tipos podem ser usados para definir qualquer tipo, incluindo objetos, funções e tipos primitivos.

As interfaces também são usadas para definir contratos de implementação, ou seja, elas especificam a estrutura que uma classe ou objeto deve ter para implementar essa interface. Por outro lado, os tipos podem ser usados para criar tipos mais complexos, como tipos de união, interseção e tipos literais.

Além disso, as interfaces têm a capacidade de estender outras interfaces e podem ser usadas para criar tipos genéricos. Por exemplo, você pode definir uma interface genérica para uma lista de usuários da seguinte forma:

```typescript
interface Lista<T> {
  items: T[];
}

interface Usuario {
  nome: string;
  idade: number;
}

const listaDeUsuarios: Lista<Usuario> = {
  items: [
    { nome: 'João', idade: 30 },
    { nome: 'Maria', idade: 25 }
  ]
};
```

Por outro lado, os tipos podem ser usados para criar tipos mais complexos e que não são possíveis com interfaces, como tipos literais ou tipos de união com tipos primitivos.

## Estendendo interfaces

Podemos estender uma interface existente para adicionar novos campos e métodos a ela usando a palavra-chave `extends`. Isso permite que você defina novas interfaces que incluem todos os campos e métodos da interface pai, além de quaisquer novos campos e métodos que você adicionou.

Suponha que você tenha uma interface `Pessoa` que define os campos nome e idade:

```typescript
interface Pessoa {
  nome: string;
  idade: number;
}
```

Agora, suponha que você queira criar uma nova interface chamada `Funcionario` que inclua todos os campos da interface `Pessoa` e também inclua um campo adicional `salario`. Você pode fazer isso usando a palavra-chave `extends`:

```typescript
interface Funcionario extends Pessoa {
  salario: number;
}
```

Nesta definição, a interface `Funcionario` estende a interface `Pessoa`, o que significa que ela inclui todos os campos e métodos da interface `Pessoa`, bem como o novo campo `salario`.

Agora, você pode criar um objeto `Funcionario` que inclua todos os campos da interface `Pessoa` e o campo adicional `salario`:

```typescript
const joao: Funcionario = {
  nome: 'João',
  idade: 35,
  salario: 5000
};
```

Veja que você não precisa incluir os campos nome e idade novamente na definição de `Funcionario`, porque eles já estão incluídos na interface pai `Pessoa`.

### Também é possivel estender de `type`

É possível estender tipos existentes utilizando a técnica de união e interseção de tipos utilizando `&`. Por exemplo, se você possui um tipo `Pessoa` com as propriedades `nome` e `idade`:

```typescript
type Pessoa = {
  nome: string;
  idade: number;
};
```

E você quer estender esse tipo com uma nova propriedade `email`, você pode criar um novo tipo que seja uma interseção entre o tipo `Pessoa` e um objeto com a nova propriedade `email`:

```typescript
type PessoaComEmail = Pessoa & {
  email: string;
};
```

Dessa forma, o novo tipo `PessoaComEmail` terá todas as propriedades de `Pessoa`, mais a nova propriedade `email`. Você pode usar esse novo tipo para definir variáveis e parâmetros de função:

```typescript
const pessoa1: PessoaComEmail = {
  nome: 'Fulano',
  idade: 30,
  email: 'fulano@example.com'
};

function enviarEmail(pessoa: PessoaComEmail) {
  // ...
}
```

Para estender um tipo com um conjunto de tipos adicionais, você pode usar a técnica de união de tipos (`|`). Por exemplo, se você tem um tipo Cor com três valores possíveis:

```typescript
type Cor = 'vermelho' | 'verde' | 'azul';
```

E você quer estender esse tipo com mais uma cor, você pode criar um novo tipo que seja uma união entre o tipo `Cor` e um novo valor `'amarelo'`:

```typescript
type CorComAmarelo = Cor | 'amarelo';
```

Dessa forma, o novo tipo `CorComAmarelo` terá todos os valores possíveis de `Cor`, mais o novo valor `'amarelo'`. Você pode usar esse novo tipo para definir variáveis e parâmetros de função:

```typescript
const cor1: CorComAmarelo = 'verde';
const cor2: CorComAmarelo = 'amarelo';

function pintar(cor: CorComAmarelo) {
  // ...
}
```

Essas são algumas das técnicas que você pode usar para estender tipos existentes em TypeScript.

## Criando tipos genéricos

Você pode criar tipos genéricos usando a sintaxe de tipo genérico `<>`. Isso permite que você crie tipos que funcionam com diferentes tipos de dados, permitindo que seu código seja mais reutilizável. Para criar um tipo genérico, você precisa especificar um ou mais parâmetros de tipo entre os caracteres `<` e `>`. Esses parâmetros podem ser qualquer nome de variável, mas é comum usar letras maiúsculas para distingui-los dos tipos normais. Em seguida, você pode usar esses parâmetros de tipo em vez de tipos reais em sua definição de tipo.

Por exemplo, suponha que você queira criar uma função que receba uma matriz de valores e retorne o valor máximo. Você pode criar uma função genérica com um parâmetro de tipo `T` da seguinte forma:

```typescript
function maximo<T>(valores: T[]): T | undefined {
  if (valores.length === 0) {
    return undefined;
  }
  let maximo = valores[0];
  for (let i = 1; i < valores.length; i++) {
    if (valores[i] > maximo) {
      maximo = valores[i];
    }
  }
  return maximo;
}
```

Nesta função, o parâmetro de tipo `T` é usado para definir o tipo da matriz de entrada e o tipo de retorno. Ao usar `<T>` na definição da função, você está criando um tipo genérico que pode ser usado com qualquer tipo de dados.

Agora, você pode chamar essa função com qualquer tipo de matriz, como uma matriz de números ou uma matriz de strings:

```typescript
const numeros = [1, 5, 3, 2, 4];
const maiorNumero = maximo(numeros); // retorna 5

const strings = ['banana', 'maçã', 'laranja'];
const maiorString = maximo(strings); // retorna 'maçã'
```

Essa é apenas uma introdução básica sobre como criar tipos genéricos, você pode usar parâmetros de tipo adicionais, especificar restrições de tipo e muitas outras coisas para criar tipos genéricos mais complexos e flexíveis.

## Conclusão

TypeScript é uma linguagem de programação que adiciona tipagem estática opcional, recursos de orientação a objetos, interfaces e outros recursos avançados ao JavaScript.

Aqui vão alguns motivos para você adotar o TypeScript de uma vez por todas em seus projetos que utilizam JavaScript:

1. **Detecção de erros em tempo de compilação:** o TypeScript permite que você defina tipos para variáveis, parâmetros de função, propriedades de objeto e outros elementos do seu código. Com isso, o TypeScript pode detectar muitos erros de programação em tempo de compilação, em vez de deixá-los para serem encontrados em tempo de execução.

2. **Melhoria da produtividade:** o TypeScript permite que você trabalhe com um código mais seguro e confiável, o que pode ajudar a evitar erros e bugs em seu código. Além disso, recursos como autocompletar, refatoração e documentação incorporada podem melhorar a produtividade e a qualidade do seu código.

3. **Compatibilidade com JavaScript:** o TypeScript é uma superset do JavaScript, o que significa que todo código JavaScript existente é válido em TypeScript. Isso significa que você pode adotar o TypeScript gradualmente em seu projeto, adicionando tipagem estática e outros recursos à medida que sua equipe se familiariza com a linguagem.

4. **Facilidade de manutenção:** o TypeScript torna o código mais legível e compreensível, permitindo que os desenvolvedores entendam melhor a intenção do código. Além disso, as interfaces permitem definir contratos claros entre componentes, tornando mais fácil manter e refatorar o código.

5. **Comunidade e ecossistema crescentes:** o TypeScript é uma linguagem de programação popular e em rápido crescimento, com uma comunidade ativa e um ecossistema cada vez mais robusto de bibliotecas e ferramentas.

O TypeScript pode ajudar a melhorar a qualidade e a produtividade do seu código, tornando-o mais seguro, legível e fácil de manter. Além disso, o fato de ser uma superset do JavaScript significa que você pode adotá-lo gradualmente em seu projeto, sem precisar reescrever todo o código existente.