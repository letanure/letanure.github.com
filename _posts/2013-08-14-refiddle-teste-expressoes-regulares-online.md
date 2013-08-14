---
layout: post
title: "reFiddle: teste expressões regulares online"
description: ""
category: 
tags: [regex, utilidades]
---
{% include JB/setup %}

Hoje, precisei fazer uma regex em javascript e achei uma ferramenta online ótima sobre o assunto, o [reFiddle].

Pelo próprio nome, lembra o [jsfiddle], outra ferramenta muito útil, para testar e compartilhar códigos HTML/CSS/Javascript.

![Captura de tela do reFiddle]({{ site.url }}/assets/images/reFiddle-screen.png)

----

## Funções

o [reFiddle] tem a mesma estrutura básica de ações / input que conhecemos de outros serviços do gênero:

- Área de Input do pattern da expressão regular, com syntax highlight
- Área Corpus: Input de strings para testes da regex
- Área Replace: Play: para iniciar o teste nas strings abaixo, marcando as que passam com um fundo verde, vermelho as que falham
- Save: salvar em uma url única o seu teste
- Fork: copiar um teste em uma nova url, para modificações
- Clear: começar do zero
- Undo: voltar ao estado antes do Clear
- Área Discuss: uma área de comentarios, da [disqus]
- Painel de opções, com:

  - Regex Options:

      - seleção entre Javascript, Ruby ou .Net
      - Match all occurrences ( /g ), Ignore case ( /i ) e ^$ match each line ( /m )
      - Descriçao do reFiddle, com tags, título e descrição
      - Opções de privacidade, com direitos de modificação e listar publicamente

  - Corpus Test Results

      - Número de resultados encontrados pela sua expressão regular no texto da àrea "Corpus"
  - History

      - histórico de modificações
  - Ask on StackOverflow
        
      - link para o [stackoverflow] e uma [lista de perguntas] interessantes sobre regex de lá
  - Legal & Credits: 

      - licença e agradecimentos aos projetos que usaram  (  Code Mirror, CSS3 PIE, jsfiddle, jQuery, StackOverflow )
  
  - Feedback 

      - idéias e pedidos mais solicitados por usuários e contato, do [uservoice]

Uma parte interessante, com muito conteúdo, mas pouco organizado é a lista de reFiddles públicos, marcados por [tags].

----

## Exemplos

Finalizando, os dois reFiddles que fiz hoje:

- [Nomes de usuário, 2 a 20 caracteres, letras e números apenas](http://refiddle.com/by/luiz-tanure/username-check)
- [Agrupar e substituir cada grupo de 4 linhas com &lt;td&gt;...&lt;/td&gt;](http://refiddle.com/by/luiz-tanure/find-each-4-lines-td-td-2)

----

## Bônus

- [cheat-sheet](http://www.cheatography.com/davechild/cheat-sheets/regular-expressions/) de expressões regulares do [Cheatography](http://www.cheatography.com/), disponível em [PDF](http://www.cheatography.com/davechild/cheat-sheets/regular-expressions/pdf/) também

E uma lista de outros serviços que testam regex online:

- [Rubular](http://rubular.com/): a Ruby regular expression editor
- [RegexPal](http://regexpal.com/): a JavaScript regular expression tester
- [freeformatter](http://www.freeformatter.com/regex-tester.html)
- [txt2re](http://www.txt2re.com/)

----

[reFiddle]: http://refiddle.com/
[jsfiddle]: http://jsfiddle.net/
[disqus]: http://disqus.com/
[stackoverflow]: http://stackoverflow.com/
[lista de perguntas]: http://refiddle.com/stackoverflow
[uservoice]: https://www.uservoice.com/
[tags]: http://refiddle.com/tagged
