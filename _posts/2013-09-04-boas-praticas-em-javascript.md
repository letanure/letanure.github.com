---
layout: post
title: "Boas praticas em javascript"
description: ""
category: blog
tags: [javascript]
---
{% include JB/setup %}

#Faça compreensível

Use nomes de variáveis e funções auto explicativos e simples. Crie algum padrão e mantenha em todo o projeto

Exemplos:

Variáveis com nomes ruins:

```javascript
// curtos, posicionamento no código e abreviações
var x1;
var input1;
var posLT;

// longos demais
var valorEixoXGraficoConsumo;
var inputTextFirstName;
```

Funções com nomes ruins:

```
// nomes que descrevem o código, nao o objetivo da função
function maiorDeDezoitoAnos(idade){
  return idade >= 18;
}
// é melhor descrever o objetivo
function possuiMaioridade(idade){
  return idade >= 18;
}
```

----

# Evite Globais

