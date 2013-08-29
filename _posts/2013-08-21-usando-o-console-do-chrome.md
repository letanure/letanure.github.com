---
layout: post
title: "Usando o console do chrome"
description: ""
category: blog  
tags: [chrome, javascript, Chrome DevTools]
---
{% include JB/setup %}

## Chrome DevTools Console

Todos conhhecem (ou deveriam conhecer) o console do [Chrome DevTools](https://developers.google.com/chrome-developer-tools/).

O console serve na maioria do tempo para visualizar erros, alertas de javascript e as chamadas AJAX, mas existem também formas de enviar mensagens ao console, e a mais usada é o velhor ```console.log()```que subistitui o irritante e ineficaz ```alert()``` que se usava antigamente (ou atualmente, dependendo do <s>nível do</s> desenvolvedor).

Mas aí está um problema: 99% das pessoas só conhece ou usa o ```.log()```, deixando de usar uma série de funções úteis que existem.

Vou listar elas abaixo e explicar cada uma delas, na ordem que imagino que seja mais comum o uso:

- [``` console.log(object [, object, ...])```](#toc_1)
- [``` console.info(object [, object, ...]) ```](#toc_2)
- [``` console.warn(object [, object, ...]) ```](#toc_4)
- [``` console.error(object [, object, ...]) ```](#toc_5)
- [``` console.dir(object) ```](#toc_6)
- [``` console.clear() ```](#toc_7)
- [``` console.count(label) ```](#toc_8)
- [``` console.assert(expression, object) ```](#toc_10)
- [``` console.group(object[, object, ...]) ```](#toc_12)
- [``` console.groupCollapsed(object[, object, ...]) ```](#toc_12)
- [``` console.groupEnd() ```](#toc_13)
- [``` console.profile([label]) ```](#toc_14)
- [``` console.profileEnd() ```](#toc_15)
- [``` console.timeStamp([label]) ```](#toc_16)
- [``` console.time(label) ```](#toc_17)
- [``` console.timeEnd(label) ```](#toc_18)
- [``` console.debug(object [, object, ...]) ```](#toc_19)
- [``` console.dirxml(object) ```](#toc_20)
- [``` console.trace() ```](#toc_21)

----


#### console.log()

A mais comum, usada para exibir uma mensagem no console. Você passa um ou mais parametros para o método ```.log()``` e todos sao avaliados e concatenados em uma string.

```javascript

  // texto simples
  console.log('texto'); // exibe "texto"
  
  // variáveis
  var teste1 = "texto1";
  var teste2 = "texto2";

  // com um parâmetro
  console.log(teste1); // exibe "texto1"
  
  // com dois parâmetros
  console.log( teste1, teste2); // exibe "texto1 texto2"

  // pelamordedeus não faça isso (o que já cansei de ver por aí):
  // com dois parâmetros, do jeito --comum-- e errado
  console.log( teste1 + " " + teste2); // exibe "texto1 texto2"
  
  // com um parâmetro JSON
  testeJson = { nome1: "luiz", nome2: "tanure" }
  console.log(testeJson); // exibe Object {nome1: "luiz", nome2: "tanure"} com syntax highlight

```

Hoje, o ```.log()``` é mais esperto e caso passe um objeto, ele exibe a forma resumida, em uma linha e ao clicar, exibe todas as propriedades do objeto

Voce pode passar também, parametros de formato para o ```.log()```. Eles são:

##### Tabela de parâmetros de formatação

Formato  | Descrição
---------|------------
%s       | Formata o valor como uma  string.
%d ou %i | Formata o valor como um inteiro.
%f       | Formata o valor como um float.
%o       | Formata o valor como um elemento expansível do DOM( igual ao painel de Elementos).
%O       | Formata o valor como um elemento expansívelde objeto JavaScript.
%c       | Formata o valor como um CSS fornecido.

Exemplos:

- textos e números 

```javascript
  var nome = "Eduardo";
  var pontos = 1560.89;
  console.log("Usuário %s tem %d acertos", nome, pontos);
  // exibe "Usuário Eduardo tem 1560 acertos"
  // note que exibiu a variável pontos como um inteiro, por causa do parametro "%d"
```

- Objetos Javascript e HTML

```javascript
  console.log("%o, %O", document.body, document.body);
```

que vai exibir, sucessivamente (exemplo, adaptado e resumido!):"

```html
<body>
  <header>...</header>
  <div class="conteudo">...</div>
  <footer>...</footer>
</body>
```
e (sim, sei que não tem as "{}", mas só com elas o highlight funciona)

```javascript
{
  body: {
    aLink: "",
    accessKey: "",
    attributes: NamedNodeMap,
    //...
    vLink: "",
    webkitShadowRoot: null,
    webkitdropzone: "",
    __proto__: HTMLBodyElement
  }
}
```

----

#### console.info()

Esse método é identico ao ```.log()```.

----

#### console.warn()

Esse método é identico ao ```.log()```. 
Apenas adiciona um ícone de atenção ao lado esquerdo do resultado.

----

#### console.error()

Esse método é identico ao ```.log()```. 
Apenas adiciona um ícone de erro ao lado esquerdo do resultado e o rastreamento do erro, através do arquivos (stack trace).

----

#### console.dir()

Exibe uma representação Javascript do objeto. Se ela for um elemento HTML, então suas propriedades do DOM são exibidas.

```javascript
console.dir(document.body);
```

exibe

```javascript
{
  body: {
    aLink: "",
    accessKey: "",
    attributes: NamedNodeMap,
    //...
    vLink: "",
    webkitShadowRoot: null,
    webkitdropzone: "",
    __proto__: HTMLBodyElement
  }
}
```

Resumindo, é bem semelhante ao ```.log()``, aceitando inclusive os parâmetros de formato (a [tabela acima](#toc_3) ), a diferença é modo que o resultado é apresentado.

Enquanto ```console.dir(document.body) ``` mostra como um objeto javascript, ```console.log(document.body) ``` mostra como um XML.

----

#### console.clear()

Esse método limpa o console, exibindo a mensagem ```Console was cleared```
Podemos também usar somente ```clear()``` que nao deixa nenhuma mensagem após limpar o console.

----

#### console.count()

Exibe o número de vezes que o ```.count()```foi chamado. Então:

```javascript
for(var i = 1; i <= 50; i++){
   console.count('Total');
}
```
irá exibir:

```
  Total: 1
  Total: 2
  ...
  ...
  Total: 49
  Total: 50
```

É mais útil se passar uma ```string``` com o nome que deseja, para visualizar melhor. Exemplo:

```javascript
for(var i = 1; i <= 70; i++){
   if( i % 5 === 0 ){
      console.count( 'Divisiveis por 5' )
   } else {
      console.count( 'Outros' )
   }
}
```

irá exibir, no final:

```
  Outros: 56
  Divisiveis por 5: 14
```

----

#### console.assert(expression, object)

O ```.assert()```recebe uma expressão para avaliar e um objeto (qualquer coisa, como o ```.log()``) e exibe o segundo parametro, como um erro, se a expressão for falsa. Exemplo:

```javascript
  for(var i = 1; i <= 25; i++){
    console.assert( i % 5 == 0 , i ,  'não é divisivel por 10' )
  }
```

exibe:

```
  Assertion failed: 1 não é divisivel por 10
  Assertion failed: 2 não é divisivel por 10
  ...
  Assertion failed: 19 não é divisivel por 10
  Assertion failed: 21 não é divisivel por 10
```

----

#### console.group()

Este método agrupa um conjunto de mensagens no console, abertas, podendo 'fechar' essa parte, para visualizar melhor, ou entender a sequencia de eventos.  para fechar um grupo, se usa o método ```.groupEnd()```.

Exemplo:

```javascript
  for(var i = 1; i <= 21; i++){
    if( i === 5  ){
      console.group('Numeros entre 5 e 10');
    }
    console.log('Número', i);
    if( i === 10  ){
      console.groupEnd()
    }
  }
```

irá exibir:
 
 ```
  Número 1
  Número 2
  Número 3
  Número 4
  ▼ Numeros entre 5 e 10
      Número 5
      Número 6
      Número 7
      Número 8
      Número 9
      Número 10
  Número 11
  Número 12
```

É possível criar grupos, dentro de outros

----

#### console.groupCollapsed()

É a mesma coisa que o [```.group()```](#toc_11), só que o grupo se inicia fechado, então a função anterior teria o seguinte resultado:


```
  Número 1
  Número 2
  Número 3
  Número 4
  ▶ Numeros entre 5 e 10
  Número 11
  Número 12
```

E ao clicar no grupo ele é exibido.

----

#### console.groupEnd()

Encerra um grupo, o último criado, com ```.group()``` ou ```.groupCollapsed()```.

----

#### console.profile()

Ao iniciar o Chrome DevTools, chamar essa função inicia um profile do javascript, medindo o uso de memória, até que ```.profileEnd()```se ja chamado. Ao terminar ele exibe um link para a tab de Profiles, onde o profile criado está listado, à esquerda. 

```
  console.profile('teste')
  Profile 'teste' started.
  ...
  ...
  console.profileEnd()
  Profile 'teste' finished.
```

Em outro post, explicarei melhor os profiles de javascript e CSS do DevTools.

----

#### console.profileEnd()

Encerra a coleta d edados do profile atual e exibe o link para o resultado no painel Profiles

```
  console.profileEnd()
```

----

#### console.timeStamp([label])

O método adiciona um evento, nomeado, na Timeline do devTools, enquanto grava uma sessão. 

Quando explicar Profiles de CPU, também explicarei a timeline e gravação de sessões do DevTools


----

#### console.time(label)

Inicia um cronometro, associado a um nome, que é encerrado coma função ```.timeEnd()``` e exibe o tempo deccorido entre o início e o fim, em  milisegundos.

Exemplo, para verificar quanto tempo leva para criar um milhão de novos objetos em um array:

```javascript
  console.time("inicia o grande Array");
  var grandeArray= new Array(1000000);
  for (var i = grandeArray.length - 1; i >= 0; i--) {
      grandeArray[i] = new Object();
  };
  console.timeEnd("inicia o grande Array");
```

aqui, resultou em:

```
  inicia o grande Array: 1860.799ms
```

----

#### console.timeEnd(label)

Para o cronometro iniciado com ```.time()```, como mostrado acima.

----

#### console.debug(object [, object, ...])

Esse método é identico ao ```.log()```.

Não ficou junto dos outros identicos, proque é incommun. quem quer escrever ```.debug()``` em vez de ```.log()```?

----

#### console.dirxml(object)

Exibe uma representaçao do parametro no formato XML, como o do aba de elementos. É quase igual ao ```.log()```, aceitando os mesmos parametros de exibiçao da [tabela acima](#toc_3)

----

#### console.trace()

Exibe uma pilha/lista a partir do ponto de onde o ```.trace()``` foi chamado, com as funções, arquivos e linha por onde passou. o núemro indica quantas vezes o ```.trace()```foi chamado.

----

#### console.table()

Exibe os dados informados no parametro, no formato de uma tabela, com os cabeçalhos sendo os índices.

Exemplo:

```javascript
  console.table( [{ nome: "Joao", idade: 25, estado: "SP" }, { nome: "Maria", idade: 22, estado: "RJ" }] );
```

irá exibir uma tabela, no console, como esta:

| nome  | idade | estado |
|-------|-------|--------|
| Joao  | 25    | SP     |
| Maria | 22    | RJ     |

----

#### console.memory

Exibe informações sobre o uso de memória, no formato:

```javascript
  //MemoryInfo 
  {jsHeapSizeLimit: 793000000, usedJSHeapSize: 64000000, totalJSHeapSize: 76600000}
```

----

#### console.markTimeline()

----

#### debugger

Não faz parte do  ```console.```. Ele para a execuçao do script e abre o modo de debug do DevTools, como se fosse um marcador inserido manualmente.

----

### Bônus 1 - 

Inclua esse script no seu projeto e não tenha medo de usar o console ou esquecer um ```console.log```e dar erro no IE

{% gist 2733067 %}

Caso não exista a funçao console nativa, ele cria, com todos os métodos.

### Bônus 2

[Chrome DevTools Cheatsheet](https://github.com/jaredwilli/devtools-cheatsheet): uma lista com atalhos do DevTools

#### Fontes
[developers.google](https://developers.google.com/chrome-developer-tools/)
