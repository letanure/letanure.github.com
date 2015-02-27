---
layout: post
title: "Vivus   Biblioteca JavaScript para animações em SVG"
description: ""
category: 
tags: []
---
{% include JB/setup %}


<div style="background: #5aa8c5; text-align: center; padding: 10px; margin-bottom: 20px;">
    <svg id="svg-topo" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
    width="100%" height="200px" viewBox="0 0 200 200" enable-background="new 0 0 200 200" onclick="obt1.reset().play();">
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="90"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="85.74"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="72.947"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="39.74"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="34.042" y1="131.189" x2="67.047" y2="77.781"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="31.306" y1="75.416" x2="92.41" y2="60.987"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="68.81" y1="34.042" x2="122.219" y2="67.046"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="124.584" y1="31.305" x2="139.013" y2="92.409"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="165.957" y1="68.809" x2="132.953" y2="122.219"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="168.693" y1="124.584" x2="107.59" y2="139.012"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="131.19" y1="165.957" x2="77.781" y2="132.953"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="75.417" y1="168.693" x2="60.987" y2="107.59"/>
    </svg>
</div>

[Vivus](https://github.com/maxwellito/vivus) é uma lib javascript, sem dependências, para criar animações em SVGs com o efeito de "desenhando", mostrando o SVG sendo desenhado traço por traço com várias opções, como sincronia entre todos os traços ou atraso na animação.

### Como funciona?

Basicamente a biblioteca manipula a propriedade [```stroke-dashoffset```](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke-dashoffset), que especifica o tamanho do traço em relação ao seu ponto inicial.

Mas essa propriedade só existe em elementos do tipo _path_, então para ser possível animar outros tipos de elementos como _circle_, _rect_, _line_ e _polyline_ a library possui uma classe interna chamada _pathformer_, que transforma esses elementos em _path_s.

Outro ponto importante é que animação acontece na ordem em que cada elemento ocorre dentro da _tag_ SVG.

### Requisitos

Para funcionar, observe que:

- O SVG deve ser inline ([suporte ie8+](http://caniuse.com/#feat=svg-html5) );
- todos os elementos do SVG devem ter a propriedade _stroke_ sem preenchimento;
- o SVG não deve possuir elementos ocultos ( a animação ocorre neles também, mas não é mostrada, gerando um "furo" na sequencia de animações);
- Elementos do tipo _text_ não funcionam porque não podem ser convertidos em _path_s.

### Como usar?

Primeiro, óbvio, inclua a lib na sua página (baixe bia bower, no git ou use via CDN):

```html
<script src="//cdn.jsdelivr.net/vivus/0.1.2/vivus.min.js"></script>
```
<script src="//cdn.jsdelivr.net/vivus/0.1.2/vivus.min.js"></script>

Depois, um SVG inline, como por exemplo:

```html
<svg id="animacao1" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
width="100%" height="200px" viewBox="0 0 200 200" enable-background="new 0 0 200 200">
    <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="72.947"/>
    <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="39.74"/>
    <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="31.306" y1="75.416" x2="92.41" y2="60.987"/>
    <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="124.584" y1="31.305" x2="139.013" y2="92.409"/>
    <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="168.693" y1="124.584" x2="107.59" y2="139.012"/>
    <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="75.417" y1="168.693" x2="60.987" y2="107.59"/>
</svg>
```

<div style="background: #000">
    <svg id="sem-animacao" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
    width="100%" height="200px" viewBox="0 0 200 200" enable-background="new 0 0 200 200">
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="72.947"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="39.74"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="31.306" y1="75.416" x2="92.41" y2="60.987"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="124.584" y1="31.305" x2="139.013" y2="92.409"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="168.693" y1="124.584" x2="107.59" y2="139.012"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="75.417" y1="168.693" x2="60.987" y2="107.59"/>
    </svg>
</div>
<br>

Finalmente, chame a função:

```js
new Vivus('animacao1', {type: 'delayed', duration: 200});
```


### Exemplo básico funcional

Juntando tudo você terá o efeito:
<div style="background: #000">
    <svg id="animacao1" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
    width="100%" height="200px" viewBox="0 0 200 200" enable-background="new 0 0 200 200">
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="72.947"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="39.74"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="31.306" y1="75.416" x2="92.41" y2="60.987"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="124.584" y1="31.305" x2="139.013" y2="92.409"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="168.693" y1="124.584" x2="107.59" y2="139.012"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="75.417" y1="168.693" x2="60.987" y2="107.59"/>
    </svg>
</div>
<br>

<script>
    document.addEventListener("DOMContentLoaded", function(event) { 
        new Vivus('animacao1', {type: 'delayed', duration: 200});
        new Vivus('svg-topo', {type: 'delayed', duration: 200});
    });
</script>

O construtor da função possui 3 argumentos:

```js
    new Vivus('id-svg', {objeto-config}, [callback]);
```

 - O #ID do SVG;
 - Um objeto de configurações, descrito abaixo;
 - Uma função de _callback_, opcional, chamado ao final da animação.

### Configurações

O Objeto de configurações possui a seguinte estrutura:

```js
{   
    // Tipo de animação usado
    type    : 'delayed', // String [delayed|async|oneByOne|script]
    // Duração em frames
    duration: 200, // Integer
    // Quando a animação inicia
    start   : 'autostart', // String [inViewport|manual|autostart]
    // Tempo entre a primeira e última animação, apenas para type: 'delayed'
    delay   : 100, // Integer
    // Margem extra entre traços, default 2
    dashGap: 2, // Integer
    // Força o navegador a renderizar novamente os elementos, default true
    forceRender: true, // Boolean
    // Remove estilizações extras no SVG
    selfDestroy: false // Boolean
}
```

### Métodos

Para controlar a animação, temos três métodos disponíveis, com nomes autoexplicativos:

```js
    var animacao = new Vivus('id-svg');
    animacao
        .stop()
        .reset()
        .play(1) // velocidade da animação ou negativo para retroceder
```

### Playground

<div class="example">
    <svg id="animacao2" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
    width="100%" height="200px" viewBox="0 0 200 200" enable-background="new 0 0 200 200">
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="72.947"/>
        <circle fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" cx="100" cy="100" r="39.74"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="31.306" y1="75.416" x2="92.41" y2="60.987"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="124.584" y1="31.305" x2="139.013" y2="92.409"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="168.693" y1="124.584" x2="107.59" y2="139.012"/>
        <line fill="none" stroke="#f9f9f9" stroke-width="3" stroke-miterlimit="10" x1="75.417" y1="168.693" x2="60.987" y2="107.59"/>
    </svg>
    <br>

    <style>
        .example{
            background: #000;
            margin: 15px 0;
            padding: 10px;
            border-radius: 5px
        }
        .controls{
            background: #ccc;
            padding: 10px;
            margin: 10px;
            border-radius: 3px;
            overflow: hidden;
        }
        .controls label,
        .controls .actions{
            display: inline-block;
            margin: 0 10px 0 0;
            float: left;
        }
        .controls label span,
        .controls .actions span{
            display: block;
            height: 25px;
            line-height: 25px;
            font-weight: 600;
        }
        .controls label div,
        .controls .actions div{
            height: 30px;
        }
        #log{
            float: left;
        }
    </style>

    <div class="controls">
        <label>
            <span>Duração</span>
            <div>
                <input type="range" id="duration" min="100" value="200" max="1000" step="100" list="opt-vel">
                <datalist id="opt-vel">
                    <option>100</option>
                    <option>200</option>
                    <option>300</option>
                    <option>400</option>
                    <option>500</option>
                    <option>600</option>
                    <option>700</option>
                    <option>800</option>
                    <option>900</option>
                    <option>1000</option>
                </datalist>
            </div>
        </label>
        <label>
            <span>Tipo</span>
            <div>
                <select id="type" name="type">
                    <option value="delayed" selected>delayed</option>
                    <option value="oneByOne">oneByOne</option>
                    <option value="async">async</option>
                </select>
            </div>
        </label>
        <div class="actions">
            <span>Ações</span>
            <div>
                <button type="button" data-action="stop">Stop</button>
                <button type="button" data-action="play">Play</button>
                <button type="button" data-action="reset">Reset</button>
            </div>
        </div>
        <div id="log">
            Log: Início
        </div>
    </div>
</div>

<script>
    document.addEventListener("DOMContentLoaded", function(event) { 
        var $controls = $('.controls'),
            $actions = $('.actions button'),
            $duration = $('#duration'),
            $log = $('#log'),
            finished = false,
            config = { start: 'manual', type: 'delayed'},
            anim = new Vivus('animacao2', config, callback),
            $type = $('#type');

        $duration.on('change', function(e){
            delete anim;
            config.duration = $duration.val();
            anim = new Vivus('animacao2', config, callback);
        });

        $type.on('change', function(e){
            delete anim;
            config.type = $type.val();
            anim = new Vivus('animacao2', config, callback);
        })

        $actions.on('click', function(){
            var action = $(this).data('action');
            if(finished){
                finished = false;
                anim.reset();
            }
            if(action === 'stop'){
                anim.stop();
                log(0);
            }
            if(action === 'reset'){
                anim.reset();
                log(1);
            }
            if(action === 'play'){
                anim.play();
                log(2);
            }
        });

        function callback (obj) {
            finished = true;
            log(3);
        }

        function log(step){
            if(step === 0){
                $log.text('Animação parada.')
            }
            if(step === 1){
                $log.text('Animação reiniciada.')
            }
            if(step === 2){
                $log.text('Animação sendo executada.')
            }
            if(step === 3){
                $log.text('Animação finalizada.')
            }

        }

    });
</script>



### Leia mais

 - [SVG Drawing Animation](http://tympanus.net/codrops/2013/12/30/svg-drawing-animation/)
 - [Stroke Dash Interpolation](http://bl.ocks.org/mbostock/5649592)
 - [Polygon feature design: SVG animations for fun and profit](http://product.voxmedia.com/2013/11/25/5426880/polygon-feature-design-svg-animations-for-fun-and-profit)