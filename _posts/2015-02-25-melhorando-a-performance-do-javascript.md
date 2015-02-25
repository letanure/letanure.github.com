---
layout: post
title: "Melhorando a performance do Javascript"
description: ""
category: javascript 
tags: [performance, dicas]
---
{% include JB/setup %}

Javascript está em todos os lugares hoje, nas mais variadas formas, com ou sem frameworks, em desktops, sites, apps. E é fácil ver que temos problemas com performance, ainda mais em dispositivos móveis e em sistemas mal programados ou com muitos recursos visuais, animações e dados.

O Javascript em si não é tão rápido como deveria, mas a cada dia a performance melhora. Vale dar uma olhada nesse site [arewefastyet](http://arewefastyet.com/) que mostra uma comparação entre as engines existentes, no geral e por sistema operacional.

Existem algumas iniciativas para melhorar a performance do Javascript, como o [asmjs](http://asmjs.org/), [emscripten](http://kripken.github.io/emscripten-site/), que nada mais é do que um subset do javascript, compilado num código bem difícil de entender, mas não é nada prático para projetos diários, então seguem algumas dicas práticas para adotar no nosso dia a dia com Javascript que melhoram a performance:

### Defina os tipos de váriaveis e mantenha-os assim

No Javascript as váriaveis são dinâmicas, então uma hora elas podem ser um inteiro, depois virar uma string ou qualquer outra coisa. Evite isso, declarando o tipo e nunca mudando ele, nem misturando tipos em um objeto.

```js
// evite misturar tipos em arrays e objetos
var arr = [1, "teste", {}, []];
var obj = { um: 1, dois: '2', tres: [3, 4] }
```

> Vale conferir esse teste de performance no [jsperf](http://jsperf.com/casting-type/15)

### Não reestruture objetos

Reestruturar objetos é lento, então, para maior rapidez:

- Evite usar o operador [```delete```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete), é mais rápido definir a váriavel como ```null``. Mas não significa que não deva usar, apenas use com parcimônia.
    + veja esse teste de [delete comparado à null](http://jsperf.com/object-structure-change). delete é chega a ser 99% mais lento!
- Não adicione propriedades dinâmicamente. Defina seu objeto inteiro no início, mesmo que vazio, e depois defina os valores quando for o caso.
    + [aqui](http://jsperf.com/object-dynamic-properties) dá para ver que definir o objeto antes é até 70% mais rápido.

### Cuidado com concatenação de strings

Existem várias maneiras de concatenar strings e alguns mitos sobre a melhor forma, além de diferenças de performance, por método, entre navegadores diferentes.

Segundo [este teste](http://jsperf.com/string-concat-fast/9) usar os operadores ```+```, ```+=```, tão comuns, não são a melhor abordagem. 

Na maioria dos navegadores, usar [```Array.join```](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/join) e [```String.concat```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat) são máis rápidos.

### Escolha o método correto para RegExp

Temos maneiras diferentes de fazer algo usando [](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/RegExp), então conheça a diferença entre eles e saiba qual é o mais performático para seu problema.

> Compare os métodos [```Regex.exec```, ```Regex.test```, ```String.match``` e ```String.search```](http://jsperf.com/regex-methods-x-1)

Então se não precisa saber a posição de uma _substring_ em outra, prefira ```String.indexOf``` em vez de ```Regex.test```, por exemplo.

### Cuide do escopo

Evite declarar váriaveis e funções no escopo global.

Porquê? o escopo global já possui muita coisa ( tente ```console.log(window)``` no console para ver) e quando se declara algo globalmente, a cada vez que acessamos a váriavel ou função a engine tem que procurar no meio de tudo que já está lá, o que piora a performance.

Então use escopos locais, como em [Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) e não tenha receio de criar escopos e subescopos, criando sua funções dentro de um único objeto.

> veja uma [comparação entre escopo global e interno ](http://jsperf.com/closures-js)

### O velho e óbvio "Você não precisa de jQuery"

Existem vários artigos falando sobre não usar jQuery ( ou outros frameworks), não vou entrar nesse ponto na profundidade que eles abordam, mas em um pequeno detalhe:

>Não é porque seu projeto TEM jQuery que você PRECISA usar jQuery

Entendem a diferença? um exemplo:

```js
$('.meu_select').on('change', function(){
    var valor = '';
    // Para que usar
    valor = $(this).val();
    // em vez do nativo
    valor = this.value;
});
```

Veja uma [comparação de performance aqui](http://jsperf.com/jquery-vanilla-val).

Aprenda sobre os seletores nativos, propriedades, etc, pois usando eles irá escrever um código mais performático.

Vale a dica de sempre olhar no console como é o objeto, um simples ```console.log(meuobjeto)``` ou ```console.log(this)``` economiza muito tempo as vezes.

### Já é hora de usar os Web Workers

Conhece [Web Workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/basic_usage)? Se não, deveria.

Basicamente é uma maneira de executar algum processo em _background_, assíncrono, sem interferir no seu processo principal

Ainda não temos suporte em todos navegadores mais usados, mas se sua aplicação é *ie10+* você já pode usar sem medo. Veja o suporte [aqui](http://caniuse.com/#feat=webworkers)

### Resumo prático

- Defina váriaveis no início e não mude o tipo delas;
- Não altere tipos de váriaveis ou de propriedades de um objeto;
- Concatene strings usando ```Array.join```;
- Evite o escopo global;
- Prefira Javascript nativo;
- Conversão de números: prefira ```parseInt(numero, 10)``` - [teste](http://jsperf.com/number-vs-parseint-vs-plus/26);
- No jQuery use ````prototype```em vez de ```$.extend```- [teste](http://jsperf.com/extending-settings);
- O ```for``` nativo é sempre melhor que loops implementados [teste](http://jsperf.com/native-vs-implmented-0/5);
- Prefira o ```for``` mesmo em relação à ```forEach``` e ```filter``` - [teste](http://jsperf.com/for-vs-foreach/49);
- Use ```call``` em vez de ```apply```- [teste](http://jsperf.com/function-calls-direct-vs-apply-vs-call-vs-bind/33);
- Prefira ```removeNode()``` em vez de ```innerHTML = ''``` para limpar algo - [teste](http://jsperf.com/jquery-html-vs-empty-vs-innerhtml/9)
- Selecione elementos por #ID ```getElementById```- [teste](http://jsperf.com/id-vs-getelementbyid/3)
- No jQuery acesse elementos usando DOM em vez de ```.first()``` ou ```.eq()``` - [teste](http://jsperf.com/jquery-first-vs-first2/10);
- Crie textos com ```createTextNode``` em vez de ```innerHTML```- [teste](http://jsperf.com/creating-text-node/3);
- O óbvio: evite _loops_ aninhados;
- O velho: evite acessos ao DOM;
- Não preciso mencionar nada de ```eval()```, certo?

## Conclusão

Resumindo, boa parte das boas práticas nada mais são do que definir a váriável, objeto, no início na sua forma final, com tipo, chaves que serão usadas, e evitar modificá-los ao longo do código. Basicamenteé evitar usar a tipagem dinâmica do Javascript, que tem seu custo em performance.

Fora isso é conhecer os métodos apropriados para cada operação, diferença entre técnicas e ter em mente a finalidade da aplicação, já que cada browser ou dispositivo pode ter uma performance diferente para um mesmo código.

Alguns dos testes de performance entre métodos mostram pouca diferença, de 2% ou 3%, entre métodos, mas buscar a melhor performance em cada parte da sua aplicação irá fazer uma diferença significativa ao final pela soma das pequenas melhorias.

Essa é uma lista básica de pequenas melhorias para nosso dia a dia. Conhece mais alguma? Contribua, comente!


#### Leia mais

- [Optimizing JavaScript code - Google Developers](https://developers.google.com/speed/articles/optimizing-javascript)
- [Writing Fast, Memory-Efficient JavaScript](http://www.html5rocks.com/en/tutorials/memory/effectivemanagement/)
- [JavaScript & DOM performance tips](https://github.com/handsontable/handsontable/wiki/JavaScript-&-DOM-performance-tips)
- [Effectively Managing Memory at Gmail scale](http://www.smashingmagazine.com/2012/11/05/writing-fast-memory-efficient-javascript/)
- [http://moduscreate.com/javascript-performance-tips-tricks/](http://moduscreate.com/javascript-performance-tips-tricks/)
- [Real-World JavaScript Performance Tips](http://blog.newrelic.com/2014/11/14/javascript-perf-tips/)


