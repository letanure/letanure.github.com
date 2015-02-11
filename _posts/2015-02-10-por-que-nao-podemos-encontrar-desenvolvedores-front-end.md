---
layout: post
title: "Por que não encontramos desenvolvedores Front-End?"
description: ""
category: 
tags: []
---
{% include JB/setup %}

---

> Tradução do artigo ["Why can’t we find Front End developers?"](http://jjperezaguinaga.com/2014/03/19/why-cant-we-find-front-end-developers/)

---

Outro dia me deparei com uma [pergunta do Quora relacionada com Front End e Startups](http://www.reddit.com/r/javascript/comments/14zwpv/why_are_front_end_developers_so_high_in_demand_at/) em "Por que é que startups têm dificuldade em encontrar desenvolvedores de front-end?". O OP adiciona os seguintes cometários:

> (...) Eu acho que a maioria das pessoas concorda que o desenvolvimento front-end é muito mais fácil do que outros campos da engenharia. Então porque é que startups têm dificuldade em encontrar desenvolvedores front-end?

Eu vi algumas boas respostas, e a maioria delas vão direto ao ponto. Segue a minha opinião, com base na minha experiência de trabalho, à procura de emprego Front-End, entrevistando Front End Engineers, e trabalhando diariamente em projetos Front-End.

---

## Área relativamente nova

A primeira e mais fácil resposta à pergunta "Por que não podemos encontrar desenvolvedores Front-End" **é porque é uma nova área**. A maioria das pessoas discorda desta afirmação, uma vez que Desenvolvimento Front-End é semelhante á Desenvolvimento Web, que já existe há mais de 20 anos. No entanto, **o conceito de Desenvolvimento Front-End como a implementação técnica de interfaces e experiências de usuário como um campo específico de "trabalho"**, é definitivamente muito novo. **A parte "Engenharia" para Front End começou a crescer apenas alguns anos atrás.**

![A visualização da busca pelo termo "Engineer Front End" nos últimos anos pelo Google Trends.]({{ site.url }}/assets/images/google-trends-front-end-engineer.png)


Ninguém deve ser culpado por essa confusão entre Desenvolvimento Web VS Desenvolvimento Front-End que acontece ainda; para a maioria das pessoas fora da indústria Web o **Desenvolvimento Web é uma linha confusa entre o design visual de uma página web e da execução técnica dela**; afinal, Desenvolvimento Web é algo que Front ends fazem, com a ressalva de que **Engenheiros Front End focam-se apenas nas áreas que envolvem os usuários.**

A idéia de existir um nome para apenas a execução técnica de interfaces e experiências de usuário como um campo de trabalho começou apenas recentemente. Quinze ou mais anos atrás, os recursos eram distribuídos igualmente entre o design visual de uma página web e as implementações técnicas da mesma; com o crescimento da Web como algo mais do que apenas uma landing page/ marketing page, a necessidade de desenvolvedores tornou-se visível. As pessoas começaram a aprender Javascript, tecnologias de infra-estrutura, UX, bancos de dados, e até mesmo do projeto de sistemas apenas para a web. Hoje, **uma aplicação web como AirBnB, Facebook, ou Quora, possuem muito mais recursos de Desenvolvimento do que os recursos de Design**; em outras palavras, hoje em dia é "mais rápido" criar design visual de uma página web do que implementá-lo. **Isso não quer dizer que Design é menos importante ou que o esforço utilizado no design é menor do que a 20 anos atrás, mas que a demanda de desenvolvimento para páginas atuais é maior que antes.**

![Aplicações web atuais necessitam de mais recursos de desenvolvimento do que recursos de design.]({{ site.url }}/assets/images/webproduct.jpg)

Como a implementação técnica de uma aplicação web envolve várias áreas, na década de 90 "Engenheiros Web" eram um monte de **pau para toda obra**: eram os Administradores de Bancos de Dados (DBA), SysAdmins, Desenvolvedores Backend, DevOps, engenheiros de Software, UX e Front Ends. A última, provavelmente, era a etapa mais temida, mexer com Javascript, HTML e CSS, para fazer uma implementação visual que fizesse sentido nestas coisas chamadas browsers. **Para gostar  de Front-End você deve ter algum interesse em Design (e ser um pouco masoquista).**

![Este gif ainda é usado para representar o sofrimento que a maioria dos front ends novatos passam por; CSS é a linguagem de estilo utilizada para criar o visual correto em uma página. Na maioria das vezes não se comporta como se espera.]({{ site.url }}/assets/images/cssgif.gif)

Depois de algum tempo ficou claro que para lidar com a quantidade trabalho que aplicações web necessitam, era necessária uma divisão das tarefas técnicas, a fim de ter várias pessoas trabalhando na aplicação. Eu não sei qual tarefa levava a maior quantidade de tempo, ou qual delas era a mais difícil[1], mas o fato de que já não era mais possível ter uma única pessoa para lidar com todos os detalhes técnicos logo tornou-se uma preocupação em muitas agências web e empresas. Como resultado, todos os nomes de cargos que mencionei antes (Backend Engineer, DBA, etc) estão presentes no Setor de Web; Observe que a **maioria desses trabalhos estão aí a muito tempo, mas com requisitos certos de cada um para a induústria web é algo que começou provavelmente nos últimos 10 anos.**

![Atualmente nós ainda temos umas pobres almas que tem que lidar com dodas as implementações técnicas de uma aplicação web; Nós chamamos eles de Desenvolvedores Full Stack, e os realmente bons são tão poucos que é mais fácil achar unicórnios[2]. Designers também não são fáceis também, veja  [Como contratar designers](https://insideintercom.io/how-to-hire-designers/) para mais informações.]({{ site.url }}/assets/images/webproducttoday.jpg)

Hoje em dia Startups tem bem claro que, se quiserem ter sucesso, elas precisam cobrir adequadamente todas as áreas técnicas de um aplicativo da Web: Front-End, de back-end, DBA, operações e assim por diante. PaaS (Platform as a Service) foram criadas com o único propósito de diminuir as operações necessárias à uma Startup, como várias BaaS (back-end como serviço), tais como [Parse.com](https://parse.com/), vão tão longe quanto a fornecer banco de dados e endpoints para as suas aplicações (mas você ainda precisa de alguém para ajudá-lo a projetar o banco). Front End não foi "atendido" ainda, mas há [alguns serviços lá fora](http://designmodo.com/startup/) que lhe permite comprar módulos de Front-End e componentes para a sua página; se você quiser criar um aplicativo Web moderno, não há nenhuma maneira de evitar contratar um bom engenheiro de Front-End, da mesma forma que você não evitar contratar um designer se você quer realmente construir uma marca.

[1] Isso é uma mentira, fazer um site funcional no IE era a tarefa mais demorada. Você também deve ter perdido alguns pontos de vida fazendo isso.

[2] A maioria dos desenvolvedores front end possui falhas nas habilidades necessárias para criar uma aplicação Web completa, seja no lado do Front End, Backend ou operações. Esperanr que uma única pessoa lide com as tarefas que pelo menos 3 pessoas devem fazer em tempo integral é irrealista. Entretanto, eu conheço alguns ninjas que podem podem dar conta desde a GUI (Graphical user interface) até um processo zumbi  lá que pode enfrentar a partir de uma interface gráfica para um [processo zumbi](http://en.wikipedia.org/wiki/Zombie_process); Se você tem um desses em sua equipe, faça um favor a todos e nunca deixe-o ir embora.

## Equívocos

Outra razão importante (e na minha opinião a mais importante) sobre a dificuldade de encontrar um Front End, é porque é uma **área incompreendida**. Como a pessoa da pergunta original descreveu, a maioria das pessoas pensa que Front End é "relativamente mais fácil". Do jeito antigo *"O que a maioria das pessoas ..."*, segue um detalhamento sobre o que fazem Engenheiros Front End:

### O que a maioria das pessoas pensa que é Front End:

1. Pegar um arquivo de Photoshop, imagem ou Wireframe e torná-lo em uma página da web.
2. Às vezes criar um design no Photoshop, imagem ou Wireframe.
3. Programar Javascript,que cria animações e faz transições de uma página web.
4. Programar HTML e CSS, que define o conteúdo e estilo de uma página web.

### O que Front Ends realmente fazem:

1. Estabelecer uma linguagem visual entre designers e engenheiros
2. A partir de um projeto visual, definir um conjunto de componentes que representam o conteúdo, marca, recursos, etc.
3. Estabelecer uma guia para a aplicação Web em termos de convenções, frameworks, requisitos, linguagens visuais e especificações.
4. Definir o escopo do aplicativo Web em termos de dispositivos, navegadores, telas e animações.
5. Desenvolver uma diretriz de Garantia de Qualidade para garantir a fidelidade da marca, a qualidade do código, revisão de produto pelas partes interessadas.
6. Estilo de aplicações Web com espaçamentos adequados, tipografia, títulos, fontes, ícones, margens, preenchimentos, grids e assim por diante.
7. Estilo de aplicações Web com várias resoções de imagens, mockups para dispositivos, enquanto cuida de diretrizes de design.
8. Código HTML, tendo em conta a semântica, acessibilidade, SEO, schemas e microformats.
9. Conectar a um API para recuperar informações de maneira amigável, com pouco consumo de bateria, e claro ao cliente/dispositivo.
10. Desenvolver código do lado do cliente para executar animações, transições, lazy load, interações, fluxos de aplicativos, levando em comta otimização progressiva e compatibilidade reversa com versões anteriores.
11. Certificar conexões de back-end são seguras, levando em conta Cross Origin Resource Sharing (CORS), procedimentos, proteção contra Cross Site Scripting (XSS) e Cross Site Request Forgery (CSRF).
12. Nunca esquecendo que, apesar de prazos rigorosos, pedidos dos envolvidos e limitações de dispositivos, **O usuário está, e será sempre estará em primeiro lugar.**

Para atingir os objetivos acima mencionados, o Front End usa muitas ferramentas que vão desde programas de Design Visual (Photoshop, Adobe, Macaw, Sketch) até Ferramentas de Programação (IDEs, linha de comando, controle de versão, scripts bash, automatizadores de tarefas). Às vezes até tem que cuidar de Marketing (Newsletters, Campanhas, Analytics, SEO, Social Media), UX (animações, transições, feedback, interfaces, linguagem visual) até coisas de conteúdo (breakpoints, evitando palavras órfãs, legibilidade, cores).

## Front Ends ruins

Provavelmente a maís óbvia razão no porquê é tão difícil achar bons front end é porque existem **muitos front ends ruins**. Como pontado corretamente no [post no Quora](http://www.quora.com/Startups/Why-are-front-end-developers-so-high-in-demand-at-startups-if-front-end-development-is-relatively-easier-than-other-fields-of-engineering), a área possui uma **barreira de entrada muito baixa**. Javascript, CSS e HTML não são linguagens de programação difíceis de entender. Qualquer um pode ir à [CodeAcademy](http://www.codecademy.com/) ou [Codeschool](https://www.codeschool.com/) e aprender o básico em alguns dias, enquanto aprerder coisas como Erlang (uma das minahs linguagens favoritas), Go ou mesmo ANSI C, exige que você entenda muitos dos mecanismos de um computador. **Ajustar cores e imagens dentro de uma página da web é realmente muito fácil, enquanto que compreender o que está por baixo da web uma coisa totalmente diferente.**

At the end, the Front End Engineer market is plagued with guys that do many of the following:

No fim das contas, o mercado Engenheiro Front End é atormentado com caras que fazem muitos dos seguintes procedimentos:

### O que front ends ruins fazem (e, assim, atrapalham front ends bons):

1. Abuso de bibliotecas JavaScript, uma vez que eles não sabem realmente como funciona o Javascript (por exemplo, jQuery para tudo).
2. Abuso de Plugins Javascript, usando o código de outras pessoas sem ser capaz sequer de lê-lo (por exemplo, jQuery.doParallaxPls.js).
3. Adiciona Frameworks CSS nas aplicações (Bootstrap, Fundação, Skeleton) para utilizar apenas 5% do CSS / JS, sem olhar quaisquer requisitos, projetos, ou fazer qualquer tipo de comparação/avaliação.
4. Divulgar a idéia de que só porque você adicionou um Framework CSS, um site é "Responsivo", ou que a responsividade é algum tipo de tempero que você pode simplesmente jogar em uma aplicação web a qualquer momento.
5. Falam sobre "Responsive Web Design", mas sem conhecimento de técnicas do lado do servidor.
6. Escreve, CSS sem convenções, preprocessadores, padrões de nomenclatura, boas práticas, e, ao mesmo tempo escrevendo CSS com muitos seletores qualificados, ids, números de mágicos, !important.
7. Ignorando performance, vazamentos de memória (não sabem o que é realmente um vazamento de memória), deixando de auditar o seu código ou medi-lo.
8. Apresentar um produto sem qualquer tipo de métricas, ou as métricas sendo "Ele funciona no meu computador / Browser / Device" ™
9. Na prática, criando software ignorando 30 anos de Engenharia de Software.

Na maioria das vezes você quer um cara ou garota de **Ciência da Computação**  que **decidiu trabalhar com Front-End**. Não é um requisito ter um histórico de CC para ser um bom engenheiro de Front End, **mas a mecânica fundamental de Informática e Software deve ser sempre levada em conta, mesmo se você está programando Javascript ou para um navegador**. Bons front ends sabem que a web é, provavelmente, uma das plataformas e ambiente mais poderosos existem, e como tal, o código que é executado lá, **deve** ser desenvolvido com o mesmo cuidado (ou até mais) do que qualquer outra linguagem.

Um bom engenheiro Front End não só levará em conta o funcionamento da Web e as linguagens envolvidas, mas também tem experiência em todos os diferentes componentes, sistemas e conceitos que interagem com ele. Eis algumas coisas que um engenheiro Front End experiente deve saber ou fazer antes das tarefas normais de Front-End:

### O que front ends experientes precisam saber e fazem (dica: este são os que você quer contratar):

1. Resolução de DNS, o uso de redes de fornecimento de conteúdo (CDN), e desempenho de multiplos Hostnames nas chamadas de recursos.
2. Cabeçalhos HTTP (Expires, Cache-Control, If-Modified-Since)
3. Todas as regras do Steve Souders (Websites de alto desempenho)
4. Como resolver todos os problemas mostrados pelo PageSpeed, YSlow, Chrome Dev Tools Audit, Chrome Dev Tools Timeline.
5. Quando deixar tarefas para o servidor ou para o browser.
6. Uso de cache, tecnicas de pre-fetching e post-load.
7. Javascript nativo, saber quando fazer algo a partir do zero procurar o código de outros, e ao mesmo tempo ser capaz de avaliar os prós e os contras de usá-los.
8. Conhecimento e uso de bibliotecas modernas MVC Javascript (por exemplo, AngularJS, EmberJS, ReactJS), bibliotecas gráficas (por exemplo, D3, SnapSVG), bibliotecas de manipulação do DOM (por exemplo, jQuery, Zepto), lazy loading ou bibliotecas de gerenciamento (e.g. RequireJS, CommonJS) , gerenciadores de tarefas (por exemplo, Grunt, Gulp), gerenciadores de pacotes (por exemplo, Bower, Componentjs) e testes (por exemplo, Protractor, Selenium).
9. Formatos de imagem, benefícios, quando usar cada um e como, técnicas de otimização de imagem e estratégias de carregamento (sprites, técnicas de carregamento lento, limpeza de cache, PNG entrelaçado)
10. Conhecimento e uso de padrões CSS, convenções e estratégias modernas (por exemplo, BEM, SMACSS, OOCSS)
11. A Ciência da Computação do Javascript (memory management, single threaded nature, garbage collector algorithms, timeouts, scoping, hoisting, patterns)

## Conclusão

Hoje, mais do que nunca, **a web tem um lugar para front ends**. Foi, provavelmente, devido a evolução de vários dispositivos, navegadores e padrões web, que tornou urgente encontrar pessoas que se concentram no lado do usuário. Front Ends e desenvolvedores de todo mundo eram capazes de criar produtos excitantes que desafiavam o que nós pensavamos que a Web irá ser: um lugar para ver um menu de seu restaurante ou horários uma empresa. Agora temos de [galerias 3D  inteiras](http://threejs.org/), [comunicação em tempo real por Video](http://www.html5rocks.com/en/tutorials/webrtc/basics/?redirect_from_locale=de), [Estações de Rádio](http://grooveshark.com/), e até mesmo ferramentas inteiras para escritórios (por exemplo, Google apps, Microsoft Office online). Tudo agora no topo da **Nuvem**, uma entidade onipresente que armazena tudo o que escrevemos, ouvimos, enviamos e assistimos.


Embora seja difícil encontrar Front Ends, eu sei que mais e mais pessoas irão se juntar às fileiras do exército Front End. Não só por causa de ambientes de trabalho incríveis ou grandes pagamentos, mais vagas de Front End, mas também por causa que codificar para a web é incrível e emocionante: você tem a chance de tocar a vida de milhares de usuários, oferecendo serviços emocionantes para qualquer pessoa com uma conexão com a internet, tudo isso em cima dessas coisas chamadas Browsers, que, apesar de suas limitações, são capazes de analisar, desenhar e exibir qualquer tipo de idéias loucas. Boa jornada front ends, a Web está esperando por vocês.





