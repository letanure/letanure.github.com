---
layout: post
title:  "Hello World - Post aprendizado"
date:   2013-08-13 01:12:14
---


Acabando com a enrolação e a velha desculpa de _"casa de ferreiro, espeto de pau"_ resolvi colocar um blog no ar.

## Qual o objetivo desse blog?

bem, listando:

- Divulgar coisas legais sobre *front end*
- Aprender e ensinar um pouco. Ao ter a obrigação de postar algo, acabo aprendendo bastante, e a avalanche de coisas que encontro no dia a dia, deixam de ser só bookmarks que acabo esquecendo

( e também deixar pública essa lista de favoritos)

## Como é feito esse blog?

Estava querendo usar algo diferente, por aprendizado (e orgulho nerd). Procurei opções e no final estava entre o [octopress] e o [jekyll]. Acabei escolhendo o jekyll por achar que me daria mais liberdade e facilidade para alterar o que desejo.

Sim! esse é um post de aprendizado. Escrever em [markdown] me é familiar, mas em um blog, é novidade sim.

Coisas que gosto de ter a facilidade (na verdade só listando para testar markdown e alguns extras do jekyll:

highlight:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

include de gist:

{% gist 6125171 %}

## Próximos passos

- adicionar suporte à [SASS], [COMPASS], [coffeescript], [guard]
- alterar a estrutura de assets, no estilo [asset pipeline] do rails
- fazer uma pagina com exemplo funcional de javascript, para ver se funciona bem nessa estrutura
- alterar o layout (isso, acho que não vai acabar nunca...)
- ir documentando e postando sobre cada passo desses, para que a criação desse blog ja entre na idéia "Aprender e ensinar"
- lembrar de usar acentuação e verificar o ~~etxto~~ texto  sempre =(
- descobrir porque o [strikethrough] da linha acima não está funcionando :'( e aprender sobre o redcarpet markdown (e se vale continuar usando ele)

[jekyll]:    http://jekyllrb.com
[octopress]:    http://octopress.org/
[markdown]:    http://pt.wikipedia.org/wiki/Markdown
[SASS]: http://sass-lang.com/
[COMPASS]: http://compass-style.org/
[coffeescript]: hhttp://coffeescript.org/
[guard]: https://github.com/guard/guard
[asset pipeline]: http://guides.rubyonrails.org/asset_pipeline.html
[strikethrough]: https://help.github.com/articles/github-flavored-markdown#strikethrough
[redcarpet markdown]: https://github.com/vmg/redcarpet