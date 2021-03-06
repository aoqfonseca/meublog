---
layout: post
title: "criando widgets javascript"
date: 2013-09-22 10:35
comments: true
categories: javascript, app, engenharia
---
TL;DR;

Nos projetos atuais  nos quais trabalho, muitas vezes acabamos fazendo o que chamados de Widget. Esses widget são feitos para serem "inseridos" e usados outros portais e produtos. Na maioria dos casos, esses widgets são como apps escritas em javascript para consumir uma api e montar um dado dentro da página onde ele foi inserido.

O [Leonardo Balter](http://leobalter.net) numa [palestra](http://www.slideshare.net/leobalter/guia-de-sobrevivncia-js-no-mundo-open-source) que ele deu no Front in Rio 2012, abordou bem o assunto sobre como podemos escrever frontend apps sem inteferir no contexto da página onde está posta. Por isso pretendo apenas extender o conceito.

##  Contextualizando ##
Vamos lá, a grande maioria das pessoas, atualmente, que dizem conhecer e saber programar, apps front, faz uso de alguma biblioteca. Sem grandes pesquisas, creio que a maioria delas deva usar algo como JQuery, Mootools, BackBoneJs, AngularJS, ou similares.

Tais libs são "uma mão na roda" e realmente facilitam a codificar, testar, etc.

A pergunta que faço é:  Precisamos de todos os recursos disponíveis nesses frameworks/bibliotecas? Acredito que na maioria dos casos, se escrevessemos somente em Javascript puro, usando HTML e CSS, e não mais do que isso, conseguiríamos entregar o desejado.


##  Entendendo o "Problema" ##

Ao analisar mais detalhadamente a situação, conversando com alguns colegas especialistas em front end e com outros nem tão especialista assim. Uma das coisas que notei é que muito deles não conhecia de fato Javascript: Sabiam detalhes de cada elemento HTML, funções e motivos de cada linha de CSS; entretando desconheciam recursos básicos da linguagem Javascript, como por exemplo, fazer um laço de _for_ (muito usavam a, por exemplo, a função each do jquery).

Com isso, é possível concluir uma exagerada dependência de bibliotecas, para fazer coisas que são perfeitamente possíveis de serem feitas sem elas, usando apenas JS puro. O resultado disso, são widgets com megas de tamanho, sendo que a lógica deles mesmo são meros  kilobytes, o restante são as bibliotecas que eles carregam junto (Jquery tem minificado 93kb, veja o site). Isso pode parecer um detalhe banal num mundo onde  casas tem links de Mb... Porém uma nova variável se apresentou no horizonte que é o mundo do mobile.

 Outro ponto interessante foi uma pesquisa recente (não consegui achar o link) onde afirma que, sites que são lentos para carregar tem menor taxa de conversão. Isso mesmo, tempo é dinheiro, literalmente. Se o seu site leva mais de  5 segundos  para mostrar algo, já se foram quase 50% das pessoas aí (CHUTE!!!!).

Voltando para o mobile, ter sites grandes e pesados de carregar significa mais gasto de 3g e bateria. Maximiliano Firtman, fez numa edição do BrazilJS, uma ótima apresentação sobre o assunto, onde mostar números, dados mais concretos que meus chutes. E as pessoas tem pouca paciência - menos ainda no mobile, pode cre - para esperar seu site gigante carregar todas as libs e processá-las.

Mais aí você pode dizer, que usa a técnica de deixar o  carregamento no final de página. Desculpa meu amigo, mas o seu site ainda é pesado de carregar, vai consumir bando e bateria no mobile e pode gerar alguma perda na entrega de conteúdo.

Ok. Dito isso, voltemos paras os widgets.

Se você está criando uma widget e esse tem dependências de centenas de kb de libs (template lib, dom lib, ajax lib, etc) você se encaixa na mesma análise. E pior. Você está fazendo isso com qualquer um que use seu  código - as vezes sem saber da  âncora que você é no site deles.

Outro aspecto de widget gordos (vou chamá-los assim para facilitar), é que eles também podem gerar conflitos com outras coisa na páginas dos outros: imagine a questão das versões como podem gerar um verdadeiro inferno.

## Os conflitos ##

Para seguir adiante com a discussão é importante que fique claro que menos é mais: ou seja, quão menor for sua app/widget, melhor. Não se iluda, isso dá trabalho. Abrir mão de libs, significa você cuidar de vários detalhes antes abstraídos, porém, posso garantir que o resultado compensa.

Gosto sempre de usar exemplos. Acredito que eles sejam a melhor forma de mostrar um ponto de vista.  No meu trabalho fizemos um widget. Esse widget vai em quase todos os produtos e portais e portanto é bem usado.  Esse widget, no momento que foi feito, fizeram a escolha de implementá-lo usando libs. Pois bem.

Até aí foi uma escolha simples e até bem intencionada. Com o uso de libs e seus recursos muita complexidade seria resolvida e os desenvolvedores ganhariam tempo para lidar com os desafios do produto e não dos navegadores, etc.

O problema é que com isso, prendemos nossa solução a uma lib e sua versão. Obrigamos os produtos que queriam usar esse widget e ter essa versão, essa lib.

Os mais experientes já devem estar imaginando o cenário que isso nos levou... Hoje temos diversos produtos usando a implementação e reclamando do tamanho, do fato de termos uma versão muito antiga, conflito com implementações.

Nesse caso em específico, além do uso de libs, houve um sério problema de engenharia de software. Poderíamos ter componentizado melhor, separado melhor e essa mudança para versão mais nova seria mais simples.  Entretanto, nos amarramos demais a biblioteca e agora teremos que reescrever tudo.

Para coroar nossa análise, se tivessemos usado simples JS puro - isso daria trabalho mais é totalmente possível - agora teríamos um produto bem mais fácil de evoluir e não atrapalharíamos a vida de nossos clientes/usuários.

No mesmo tempo que essa app foi feita, uma outra app foi feita por outro time. Também é usada por todos os portais. A diferença é que eles optaram por fazer com VanillaJS. Deu muito trabalho, problemas de cross-browser para resolver, ajax, etc. Mas no final eles conseguiram e tem sido um benchmark para nós todos. Eles provaram que a entrega foi bem melhor  e  com usuários felizes.

## A conclusão ##

Vamos lá a formula de bolo para ajudar a:

1. Tentar sempre usar somente javascript. Mais nada
2. Lembre  de isolar bem o seu contexto de váriaveis.
3. Sempre que possível use de namespaces/
4. Se não der para usar só js, procure por um micro framework para resolver o seu problema de forma bem específica. Embede o código dessa lib na sua.
5. Menos código, menos bugs.
6. Seja cuidadoso e sempre se coloque no lugar da pessoar que irá usar.

_"Escreva como se a pessoa que fosse usar  seja um psicopata e sabe onde mora"_
