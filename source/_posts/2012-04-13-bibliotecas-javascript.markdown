---
layout: post
title: "Bibliotecas para Javascript"
date: 2012-04-13 00:02
comments: true
categories: javascript, teste
---

Com interfaces webs cada vez mais ricas, o uso de javascript vem aumentando cada vez mais. A pouco tempo atrás ter um código javascript em nossas páginas praticamente se limitava, na maioria dos casos, a algumas linhas que vinham aninhadas ali mesmo dentro do html e faziam o básicão: algum menu, esconder mostrar um elemento, etc. Hoje, temos elementos como carrocéis, galerias de fotos, popins, modais, animações das mais variadas e não é mais três linhas e sim arquivos que chegam até a casa dos megasbytes. Existem casos onde a página enviada no request chega a ser apenas um esqueleto e toda inteligência fica por conta de milhares de linhas de javacript.

Com isso fica evidente que precisamos cada vez ter mais cuidado com essas peças de código que colocamos em nossas páginas, como melhorar nossa modelagem (usando conceitos de Orientaçção a Objeto para aumentar reutilização), melhor distribuição por arquivos, namespaces, módulos, e muitas outras que iremos aborda aqui ou em outros artigos.

### Orientação a objeto e um monte de lib de terceiros ###

Primeira coisa que gostaria de abordar é Orientação a Objeto. A maioria dos desenvolvedores que conheço - de javascript (alguns só de jquery) - parecem desconhecer que a linguagem tem esse recurso e quão ele é poderoso. Tudo bem que o mecanismo não é dos mais simples de entender e implementar (prototype) mas existe e funciona. Eu, pessoalmente, gosto muito de colocar a minhas lógicas em classes. Isso me ajuda muito a definir as relações e as interações entre as camadas, atores, modelos, etc. A primeira dica que fica, para a questão de classes em Javascript, e que existem algumas bibliotecas que facilitam (bastante) a tarefa de criar classes e definir seus métodos ( Prototype, Mootools, etc) mas acredito que elas tenham mais do que precisa.

Tem gente baixando um monte de JS e só usando 10% que é a parte que realmente precisa.

Quantas vezes vi colegas incluírem, por exemplo, o jquery inteiro e o jquery-ui somente para usar 2 ou 3 funcionalidades que ele poderia ter implementado ele mesmo com algunas dezenas de linhas de código e poupado alguns megas da banda dele.  Isso não só se aplica ao jquery, tem milhares de outras libs e situações que são incluídas para somente usarmos 10% do que eles nos oferecem.

Por essas que acredito que uma forma melhor é quebrar as libs em "pedaços menores" e com isso o usuário pode levar somente aquilo que ele realmente precisa. Um bom exemplo de como fazer isso é o projeto microjs. Nele existem diversos de pequenos js com finalidades bem específicas. Dê uma olhada.


### Patterns ###

 Agora imagina que você irá implementar uma interface toda estática, cuja o conteúdo será populado e gerenciado através do Javascript. Se acha que isso é só um exemplo, veja o tempo Real de futebol ou cobertura do Rock in Rio (cobertura de eventos da globo.com). Imagina como seria a complexidade do código para implementar tal cenário. Você tem diversos elementos e interações na página, ciclos de vida, paginações, animações, requisições, eventos, etc. Se você fizer isso, só com funções, sem separar nada, o código se tornará um inferno - mal escrito, e impossível de dar manutenção. Se resolver isso com classes, mesmo assim terá um monte de código que com o tempo se tornará inviável. Embora seja um caminho.

### MVC - Model View Controller ###

Nesses momentos que temos que lançar mão de patterns para ver como podemos elaborar nosso domínio de forma que ele resolva nosso problema e seja fácil de extender ou adaptar. Um pattern excelente para situações como essas é o MVC. Escrevi um tempo atrás um artigo onde falava sobre MVC no javascript. Só para recapitular, MVC é um pattern que visa a separação da lógica de apresentação, controle e modelo de um sistema.

Antes que comece a torcer o nariz, o código da sua página pode sim ser separada em model, view e controller. O controller será a parte do código que irá gerenciar o fluxo: dada um requisição, pede que seja feito um processamento e retorna com uma resposta que será renderizada por outra parte que é o view. O view é a parte que irá montar, os dados vindo do controller, dentro da visão para o usuário. Por fim o model representar as fontes de informações e a parte que terá toda a lógica do " negócio" (o domain).

Fazer isso não é das tarefas mais simples e novamente podemos ficar um amontoado de código.

Existe uma biblioteca que faz esse meio de campo e nos deixa livre para focar na parte da implementação que nos interessa. Ela é o BackBoneJS. Ele monta um conceito de rotas que apontam para controller que por usa vez fazem uso de modelos e visões. Isso tudo de uma forma bem simples e sem complexidades ocultas.


### Referencias ###

1. http://pt.wikipedia.org/wiki/MVC - Model-view-controller (MVC)
2. http://microjs.com/ - Catálogo de MicroJS.
3. http://mootools.net/ - Página do Mootools
4. http://www.prototypejs.org/ - Biblioteca Prototype
5. http://www.slideshare.net/leobalter/javascript-sexy-com-jquery-underscore-e-backbone - Apresentação do BackBone.js
6. http://documentcloud.github.com/backbone/ - Pagina do BackBone.js
