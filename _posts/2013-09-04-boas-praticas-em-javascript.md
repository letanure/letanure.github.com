---
layout: post
title: "Boas praticas em javascript"
description: ""
category: blog
tags: [javascript]
---
{% include JB/setup %}

Em uma tarefa no trabalho, tive que propor um padrão para uso e criação no javascript, aproveitei e fiz um gtuia de estilo e boas práticas, usando algumas referencias e experiências anteriores. Segue o resultado.

A Maioria das regras não é específica de javascrip, mas sim boas praticas de programação em qualquer linguagem.

Vale dizer que procurei usar exemplos com jQuery, porque é o mais comum e o que usamos muito no dia-a-dia. Mantive aqui dessa forma para facilitar  (e porque quem escreve javascript puro, espero eu, já sabe isso e vai entender e traduzir os exmplos de jQuery para JS puro, mas o contrário nao acontece).

## Faça compreensível

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

```javascript
// nomes que descrevem o código, nao o objetivo da função
function maiorDeDezoitoAnos(idade){
  return idade >= 18;
}
// é melhor descrever o objetivo
function possuiMaioridade(idade){
  return idade >= 18;
}
```

É uma boa ideia criar um padrão para suas variáveis e funções, como por exemplo:

```javascript
// variáveis com $ no início são elementos selecionados com jQuery
var $header    = $('#header');
var $menuItens = $('#menu a');

// maiúsculas para constantes
var IMAGES_PATH = '/assets/images/';
var CLIENT_NAME = 'Fulan0';

// _ no início para variáveis e funções privadas
var _count = 0;

```

de uma olhada no padrão de nomenclatura do [crockford](http://javascript.crockford.com/code.html#names)

----

## Evite Globais

No geral é uma péssima idéia, porque aumenta a chance de ter algo sobrescrito. 
Uma opçao é utilizar [closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures) e [module pattern](http://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript)

## Seja consistente no estilo de código

Voce pode escrever seu código de muitas maneiras, mas procure manter o mesmo estilo em todo seu projeto, mantendo um padrão nos nomes, identacões, patterns, etc.

Uma dica, utilize o [jslint](http://www.jslint.com/) para validar seu código.

## Escreva os comentários necessários

É comum ouvir "Um bom código não precisa de explicação".
Concordei com isso durante um bom tempo, mas na prática vi que não funciona. muitas pessoas, de diferentes níveis, podem ter que trabalhar no seu código e nem sempre elas tem experiencia, tempo ou conhecimento do negócio para entender tudo.
Facilite a vida delas (e a sua) comentando seu código, mas não explicando o que ele faz, mas qual a regra de negócio. Exemplo:

```javascript
// ruim: verifica se é maior de 18
// bom: menores de idade sao redirecionados
if( age >=18 ){ ... }
```

Preciso mesmo falar que comentários não devem ir pra produção? Minifique seu código, para deploy!

## Evite misturar tecnologias.

No dia a dia, bem simples: estilize seu HTML com CSS, nao com JS. Exemplo:

```javascript
// Errado
$('.user-name').css({
  'border'  : '1px solid red',
  'color'   : 'red'
});
// Certo
$('.user-name.error').addClass('error');

```

Crie os estilos que precisar (e animações, quando possível), e no javascript controle quando os estilos sao aplicados, em vez de regra a regra.


## Use sintaxe abreviada

Conheça as notações de variaáveis e funções abreviadas e procure usá-las. Exemplos

```javascript
// Use
var cores = ['rosa', 'azul', 'verde'];
// em vez de
var cores = new Array();
lunch[0]='rosa';
lunch[1]='azul';
lunch[2]='verde';

// Use
var x = v || 10;
// em vez de 
if(v){
   var x = v;
} else {
   var x =10;
}

// Use
var direcao = (x > 100) ? 1 : -1;
// em vez de 
var direcao;
if(x > 100){
   direcao = 1;
} else {
   direcao = -1;
}
```

## Modularize seu código

Evite escrever funções, trechos de cófigo muito longos, ou aninhados.
Procure separar regras e códigos repetidos.

Exemplo:

```javascript
// Em vez de 
$('#botao1').on('click', function(){
  $('#resultado').load('ajax/lista-pessoas.html', function() {
    $('#formulario').slideUp()
  });
})
$('#botao2').on('click', function(){
  $('#resultado').load('ajax/lista-empresas.html', function() {
    $('#formulario').slideUp()
  });
})
//...

// Faça
function hideForm(){
    $('#formulario').slideUp();
}
$('#botao1').on('click', function(){
  $('#resultado').load('ajax/lista-pessoas.html', function() {
    hideForm();
  });
})
$('#botao2').on('click', function(){
  $('#resultado').load('ajax/lista-empresas.html', function() {
    hideForm();
  });
})

// Ou melhor
function hideForm(){
  $('#formulario').slideUp();
}
function carregaDados( elemento, url){
  $(elemento).on('click', function(){
    $('#resultado').load(url, function() {
      hideForm();
    });
  })  
}
carregaDados('#botao1', 'ajax/lista-pessoas.html');
carregaDados('#botao2', 'ajax/lista-empresas.html');

```

Quando estiver escrevendo código assim, fica fácil e natural começar a usar algum pattern javascript.


## Progressive enhacement

Igual a idéia de progressive enhacement que usamos em CSS, principalmente, escreva sua aplicaçãoo pensando nas dependencias e suporte de cada coisa. Elementos na página que dependam de javascript devem ser bem pensados.
Por exemplo, um botão que seu unico comprotamento seja abrir um modal, podemos pensar em inserir o botao através de javascript também, assim se ocorre algum erro e a funçao que abre o modal nao for funcionar, também não existirá o botaão, para que o usuário clique, nada aconteça e fique frustado.

Uma lida em técnicas de [javascript não obstrutivo](http://en.wikipedia.org/wiki/Unobtrusive_JavaScript) ajuda!

## Desenvolva pensando em configurações e internacionalização

Quando estiver criando a aplicaçao, pense em cada valor, texto, variável, se é o caso de deixá-la separada, permitindo alterá-la depois. Exemplo:

```javascript
// Em vez de
  $.ajax({
    type: "POST",
    url: "api/usuarios",
    data: {limit: 10},
    success: function(data){
      $('#formulario').hide();
      $('#mensagem').text('Busca efetuada com sucesso');
      $('#lista').html(data).fadeIn('fast');
    },
    error: function(){
      $('#mensagem').text('Erro na busca');
    }
  });

// Faça
var config: {
  messages = {
    success: 'Busca efetuada com sucesso',
    error: 'Erro na busca'
  },
  api: {
    usuarios: "api/usuarios"
  },
  animate: {
    velocity: "fast"
  },
  list: {
    perPage: 10
  }
}
//...
$.ajax({
  type: "POST",
  url: config.api.usuarios,
  data: {limit: config.list.perPage},
  success: function(data){
    $('#formulario').hide();
    $('#mensagem').text(config.messages.success);
    $('#lista').html(data).fadeIn(config.animate.velocity);
  },
  error: function(){
    $('#mensagem').text(config.messages.success);
  }
});


```
Pense em colocar em configurações, mensagens, classes e ids, numeros padrão, etc
Isso facilita a reutilizar o código e separar em módulos, quando for o caso, além de facilitar o uso por outras pessoas.
A idéia, junto com observaçoes anteriores é criar módulos, e deixar apenas as configuraçoes que deseja abertas para alteração.

## Evite muitos aninhamentos

Simples de evitar, seguindo as dicas anteriores. O motivo é facilitar o entendimento e manutençao dos seus códigos.
Afinal, ninguém quer trabalhar num código assim:

```javascript
$('#botao').on('click', function(){
  $.ajax({
    type: "POST",
    url: 'usuarios',
    success: function(data){
      $('resultado').fadeIn('fast', function(){
        $('#formulario').animate({
          heigth: 0, 
          opacity: 0
        }, 300, function(){
            $('#mensagem').animate({
              heigth: 200,
              opacity: 1
            }, 300, function(){
              //etc etc
            })
          }
        )
      })
    },
    error: function(){
      $('#mensagem').text(config.messages.success);
    }
  });
});
```
## Otimize loops

Existem várias maneiras de fazer loops, uma melhores que outras. Hoje, comum encontrar códigos usando loops do jquery ($.each) que loops nativos poderiam resolver.  Uma técnica simples para melhorar ainda mais os loops ```for()``` nativos é fazer cache de variáveis de comparaçao, evitando executar o ```.length``` a cada iteração. Exemplo:

```javascript
// Use
var cores = ['Azul', 'verde', 'rosa', 'vermelho'];
for(var count=0, quantCores=cores.length; count < quantCores; count++){ // 
   console.log( cores[i] );
}

// em vez de
var cores = ['Azul', 'verde', 'rosa', 'vermelho'];
for(var count=0; i < cores.length; count++){
   console.log( cores[i]) ;
}
````

Para comparaçao, um teste de performance no [jsperf](http://jsperf.com/loops/111) comparando diversos tipos de loop.
Aqui, o loop otimizado, como acima, executou 159k vezes, contra 113k vezes do tradicional.
Na prática nao é muita diferença, isolado, mas dependendo do tamanho do sistema, cada otimizaçao pequena, somadas, conta muito no final.


## Minimize acessos ao DOM

Evite ao máximo acessar o DOM para buscar ou inserir informações. É lento e não se pode confiar no que está no DOM.
Coisas simples podem minimizar o acesso, por exemplo, se alguma funçao precisa atualizar uma atbela no seu HTML, em vez de eprcorre ```<td>``` por ```<td>``` alterando os valores, pode ser mais eficiente criar uma funçaoq ue reescreva toda a tabela, e depois simpelsmente troque a antiga pela nova. Outra bem simples é fazer cache de objetos jQuery, por exemplo:

```javascript
// Em vez de
$('#botaoEnviar').on('click', function(){
  $(this).prop('disabled', true);
  $('$formulario').addClass('enviando');
  $.post('ajax/contato', function(data) {
    $('#mensagem').html(data);
    $('$formulario').removeClass('enviando');
    $('#botaoEnviar'),prop('disabled', false);
  });
});

// Faça
var $botaoEnviar = $('#botaoEnviar');
var $formulario = $('#formulario');
var $mensagem = $('#mensagem');

$botaoEnviar.on('click', function(){
  $botaoEnviar.prop('disabled', true);
  $formulario.addClass('enviando');
  $.post('ajax/contato', function(data) {
    $mensagem.html(data);
    $formulario.removeClass('enviando');
    $botaoEnviar.prop('disabled', false);
  });
});
```

## Não desenvolva específico para um navegador

Se você precisa de uma funcionalidade específica de um navegador, ou em um funciona e no resto não, adapte seu código ou mesmo as regras do projeto. Muitos problemas que encontro na comunidade, se referem muito mais a arquitetura da aplicaçao, do que ao código em si. Analise bem o suporte de cada coisa que for utilizar e repense a aplicaçao se for o caso.


## Não confie em nenhum dado

É uma boa prática validar os dados que entram na sua aplicaçao, sejam eles do back-end, do usuário ou do DOM.
Alguma vezes dá para seguir a regra 'se você entrega errado, vai receber errado', mas no geral, para sua aplicação funcionar e ter qualidade, teste qualquer entrada de dados, para nao ter erros no seu javascript. Hoje,q ualquer usuário pode abrir o código e alterar o que quiser. Então verifique os tipos de dados, nao conte com dados presentes no DOM sempre, nao use javascript para dados sigilosos.


## Adicione funcionalidades com javascript, não conteúdo

Se na sua aplicaçao voce precisa criar e inserir muito HTML, se seus códigos estao cheios de ```<div>```s, ```<td>```s, etc, analise e repense sua aplicaçao, veja se nao é o caso de usar algum sistema de templates ( handlebars... ).
são códigos dificeis de manter, que podem etr problemas de desempenho.
Caso precise, use templates separados do JS, ou carregue HTML do back-end com AJAX.

## Não reinvente a roda

Use libraries e frameworks (e contribua com eles se puder!). Eles já dão alguma estrutura conhecida ao seu projeto, facilitando que outros trabalhem, ja tem funções comuns prontas, etc. Enfim: agilizam muito o trabalho, diminuindo problemas de compatibilidade cross-browser e tem uma sintaxe conhecida.

Mas inserir o jQuery inteiro pra pegar o valor de um input, ou o jQueryUI completo para usar só o datepicker, nao vale, certo?

## Código de desenvolvimento não é código de produção

Se acostume a compactar, remover comentarios, concatenar os seus javascripts antes de mandar para produção. Hoje em dia existem diversas ferramentas para isso, inclusive online, então nao existem amis desculpas.
Tenha uma versão de desenvolvimento, normal, comentada e uma para o site em producão. Frameworks back-end modernos ja afzem isso automaticamente. se o seu back-end falar que não, procure no google e esfregue na cara dele, ok?

#Bônus

Apresentaçao do [Christian Heilmann](http://christianheilmann.com/) sobre boas práticas:

<iframe src="http://www.slideshare.net/slideshow/embed_code/1041724?rel=0" width="700" height="500" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC;border-width:1px 1px 0;margin-bottom:5px" allowfullscreen webkitallowfullscreen mozallowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="https://www.slideshare.net/cheilmann/javascript-best-practices-1041724" title="Javascript Best Practices" target="_blank">Javascript Best Practices</a> </strong> from <strong><a href="http://www.slideshare.net/cheilmann" target="_blank">Christian Heilmann</a></strong> </div>

#### Fontes
[Thinkful - Javascript Best Practices](http://www.thinkful.com/learn/javascript-best-practices-1)

