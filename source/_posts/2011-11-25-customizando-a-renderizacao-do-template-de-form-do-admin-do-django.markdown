--
layout: post
title: "Customizando a renderiza\xC3\xA7\xC3\xA3o do template de form do admin do Django"
tags:
- django
- form
- template
status: publish
type: post
published: true
meta:
  _edit_last: "1"
--

Esse post é daqueles que gosto de escrever para deixar registrado algo para lembrar daqui a um tempo.

No projeto onde estou trabalhando, precisei *customizar* a uma página que foi feita com ajuda do Admin do Django. A questão, mais detalhadamente, era a foram que o formulário seria montado: ele deveria ficar bem diferente do que a saída padrão do framework.
Uma coisa que adoro no [Django][1] é sua arquitetura plugável e nas várias apps que já trazem *prontas* algumas coisas. A questão é que quando preciso sair desse jeito comum de fazer as coisas, o que era simples se torna complexo numa "piscar de olhos".

Voltando a minha história,  nesse projeto tive que fazer um CRUD onde a tela fugia um pouco do padrão de formulários:  forma dos campos, layouts, etc.  Para resolver isso procurei pelo google como fazer para customizar o template do admin para usar um meu e não o default da app.  Para quem já trabalha com Django sabe, que nem precisava dessa busca do google, pois não existe melhor site de documentação do que do Django.

Partindo para a documentação do Django, consegui fazer o que queria e achei alguns passos e truques que quero compartilhar com vocês.

A receita é bem simples:

Primeiro você deve criar dentro da sua app uma pasta onde ficará o template do form que irá substituir do admin:

{% codeblock lang:bash %}
mkdir -p minha_app/templates/admin/minha_app/meu_modelo/
{% endcodeblock %}

Depois coloque um arquivo dentro para substituir:

{% codeblock lang:bash %}
touch minha_app/templates/admin/minha_app/meu_modelo/change_form.html
{% endcodeblock %}

Com isso, o Django passará a usar esse arquivo para renderizar o form de criação e alterado do seu modelo. Além disso você tem que ter o form o e model admin definidos. Veja a documentação para mais detalhes.

Agora vão as dicas com os pulos do gato:

1. O Django tem a estranha a mania de tentar resolver as coisas ao invés de mostrar os erros. Assim, caso seu template tenha algum erro ele irá usar o template dele para montar e não te mostrará nada. Uma forma de forçar o erro é de alterar o caminho do template no seu form e assim ele não fará o chain e não esconderá o erro.

2. Caso queira mudar todos os forms, coloque o template na raiz do projeto e não da app.

Bem é isso e espero que ajude alguém pois bati bastante cabeça para resolver essa, por incrivel e simples que pareça. 

[1]: https://www.djangoproject.com/
