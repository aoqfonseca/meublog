---
layout: post
title: "VOCÊ NÃO É O TWITTER"
date: 2013-04-06 13:27
comments: true
categories: engenharia, infra, ruby, jvm
---

*TL;DR*

Surgiram atualmente diversos artigos onde grandes e famosos produtos (e players da internet) explicam como o time de engenharia mudou a tecnologia/ linguagens e conseguiu maravilhas em redução de máquina e aumento de carga em seus sistemas. 

A grande maioria dos que li, usavam Ruby on Rails e passaram a usar Java (inclua aqui Scala, Groovy, Clojure) ou Go ou até Python em seu lugar, e com isso, reduziram drásticamente o custo de infra (energia, máquinas, resfriamente, etc) e/ou aumentaram sua capacidade carga (quantidade de requisições, conexões, etc). Enfim, foram além da simples troca de arquitetura.

Entretanto, antes que todos comecem a demonizar Ruby e/ou as ditas linguagens modernas é preciso analisar o contexto desses artigos e entender que nem de longe somos um [Twitter][4] para nos preocuparmos com esse tipo de coisa agora.


##Um pouco sobre mim e porque posso falar sobre o assunto##

Tenho em torno de 12 anos de profissão. Hoje, sou desenvolvedor senior da [Globo.com][1], atuando no time de jornalismo - responsável por sites como G1, Ego, Cobertura de Eventos, etc.

A [Globo.com][1] é uma empresa onde se desenvolve os maiores portais de jornalismos, esportes e entretenimento do Brasil . Fora isso, temos plataformas de vídeos, imagens, música, em milhares de outras coisa. 

Uma das coisas legais de se trabalhar lá é o fato de sempre procurarmos a melhor ferramenta para o trabalho. E com isso, sempre estamos experimentando  as tecnologias, linguagens, plataformas, e tudo mais que nos permite sermos mais produtivos e eficientes.

Atualmente a grande maioria dos produtos que desenvolvemos são feitos usando Python e Ruby (e seus frameworks como Tornado, Django, Ruby on Rails, Sinatra, etc).

Nossos produtos tem acessos bem grandes: Portais com milhões de vísitas únicas por dia; streaming de vídeos na faixa de gigabytes por dia, terabytes de arquivos (imagens, html, css, javascripts) e por aí vai. 


##Diferenciando um pouco ...##

Diante do relato acima muitos poderiam pensar que [Globo.com][1], deva ter as mesmas preocupações que um Facebook, [Twitter][4] ou [SoundCloud][2]. 

Posso adiantar que, sobre determinados aspectos, sim: Nenhum de nossas aplicações e novas funcionalidades vão para "produção" (para uso do nossos usúarios) sem que antes façamos bons testes de carga, testes de segurança, entre outras coisas relacionadas. Ainda na fase de desenvolvimento, temos a preocupação de fazermos coisa que deverão aguentar milhões de acessos, milhares de conexões simultaneas, picos, etc, sem jamais deixar de atender uma requisição. 

Porém se compararmos nosso volume de acesso e nosso tipo de produto, não somos parecidos com o pessoal do [Twitter][4], [Google][3], [SoundCloud][2], entre outros. 

Nossos produtos são em sua maioria estáticos: Um vez que são produzidos, nos geramos uma cópia estática e a servimos para os clientes. O [Twitter][4], por exemplo, tem um natureza muito mais dinâmica: o conteúdo é servido por usuário (com toda certeza deve existir um cache no meio do caminho) a cada requisição.

##Entendendo o problema e o contexto ##

Quando pensamos em [Google][3], [SoundCloud][2], logo pensamos em um datacenter gigantesco com milhares de máquinas. Tudo isso para atender a grande demanda de processamento que é gerada pelas milhões de requisições que os usuários fazem. São buscas, buscas por músicas, cadastros de novos usuários, posts, documentos, edição, envio de novo conteúdo, etc.

Para esse tipo de acesso, um pouco que se possa ganhar em desempenho, seja por uma escolha de arquitetura, seja pela troca de linguagem é algo muito significativo. 

_Lembre-se que estamos falando de parques com milhares máquinas._

Isso porque se conseguirmos, num cenários desses, reduzir em 10% a quantidade de máquinas e processamento, imaginem o quanto de dinheiro que isso representa na conta no final do mês. Muito né. 

Por isso que empresas e aplicativos desse porte, precisam, constantemente, buscar por meios de reduzir processamento e atender mais requisições. Por que empresas como essas correm atrás de tecnologias, arquitetura, linguagens, etc que possam ajudá-las nessa missão, nem que sejam em 1%. 


## Onde eu entro nisso tudo? Porque eu não sou o twitter?##

A grande maioria das pessoas, hoje em dia, está desenvolvendo sistemas que mal atenderão um milhar de pessoas. Existe uma infinidade de pessoas estão trabalhar em projetos de aplicações internas a empresas, os ditos corporativos.

Pouquíssimos são aqueles que estão desenvolvendo algo para uma quantidade superior a centenas de milhares. Nem vou falar naqueles que estão desenvolvendo para milhões.

Enfim, a grande maioria, está criando produtos para no máximo milhares de acessos. 

Alguns podem dizer: eu tenho a minha startup e estou desenvolvendo um produto . E quero muito que ele atinja milhões de usuários como um [Facebook][5]. Entretando, novamente, a grande maioria em seu lançamento contará com centenas de acesso e terá um crescimento bem linear e vegetativo. 

Mesmo que ocorra um *boom* no acesso, isso é bem pouco provável, não é preciso pensar nisso quando nem o produto existe ainda. 

O que quero dizer é que antes que comecemos a fazer a guerra de dizer que agora todos nós devemos largar o Ruby on Rails, ou Django, ou PHP, etc e partir para desenvolver em Assembly, precisamos entender que isso ainda não é o nosso problema. 

Nosso problema é ainda entregar valor para o cliente o mais rápido possível. Para grande maioria de nossas aplicações o custo de infra é infimo - quase desprezível - frente ao custo de desenvolvimento. Por isso usar de tecnologias de nos dê produtividade ainda é a melhor escolha. 

Fazendo referência ao título do POST, não somos o [Twitter][4], e por isso não devemos ainda nos perder nessas dicussões.

## Um grande porém ... ##

Porém, mesmo que a gente não esteja na equipe de desenvolvimento da _engine de busca do Google_, precisamos estar *antenados* com que acontece a nosso redor. É legal saber que mudanças de arquitetura e tecnologia podem ter um impacto em nosso produtos. 

Mais importante é saber das opções existente e a experiência de _missão crítica_ desses grandes players e quem sabe, quando precisarmos, seguir por um caminho menos obscuro. 

Hoje na [Globo.com][1] já estamos discutindo usar outras coisa além de Python e Ruby. Não descatarmos por completo JVM e estamos já criando coisas com [Go][6].


Esse era o recado que gostaria de deixar para vocês.


[1]: http://www.globo.com
[2]: http://soundcloud.com
[3]: http://www.google..com
[4]: http://twitter.com
[5]: http://facebook.com
[6]: http://golang.org
