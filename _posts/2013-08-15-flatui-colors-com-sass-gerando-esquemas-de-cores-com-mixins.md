---
layout: post
title: "FlatUI colors com SASS: Gerando esquemas de cores com mixins"
description: ""
category: blog
tags: [SASS, Mixins, Cores]
---

Semana passada postaram em vários grupos de front-end o [flatuicolors](http://flatuicolors.com), um site bem simples que lista e dá a opção de copiar as cores usadas no FlatUI ( [gratuito](http://designmodo.github.io/Flat-UI/) ou [pago](http://designmodo.com/flat/)  ).

Um site simples e bonito, exibindo as cores, com a opçao de copiar em vários formatos,  com um simples clique (infelizmente em flash, já que não é possível acessar a area de transferencia com javascript).

Gostei das cores, resolvi guardar elas, porque vou esquecer o site ou ele vai sair do ar, entao copiei elas (do CSS direto, pq clique em cada um, copia nome, copia cor, etc, dá muito trabalho...).

Logo depois, resolvi criar um mixin no SASS para gerar essas cores ou outros esquemas de cores, e o resultado está aí embaixo, usando [lists](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#lists), [loops @for](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#id11) e [nht()](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#nth-instance_method).

{% gist 6246587 %}

e um [CodePen](http://codepen.io/letanure/pen/djKkb) com todos 

{% include JB/setup %}
