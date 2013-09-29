---
layout: post
title: "Code Review"
date: 2013-09-28 20:48
comments: true
categories: engenharia de software, boas práticas
---
TL; DR;

Embora toda experiência, conhecimento de processos e boas práticas, ninguém está imune a cometer erros, escrever código com BUG e/ou ruim. Todo ser humano é imperfeito e está fadado a cometer erros mesmo que sendo um gênio e tendo um profundo conhecimento. BUGS e códigos mal escritos não são somente fruto de desconhecimento e despreparo mas também, de condições e contextos no qual o desenvolvedor está inserido. Sendo assim, a questão não está em não cometer o erro (bugs, código mal _escrito_, etc) e sim procurar formas de detectá-lo o mas breve possível evitando assim que esse tenha um ciclo de vida longo.


##O problema do código _feio_##

_"Escrever código para máquina é fácil."_

Nem sempre os problemas de um sistema estão em BUGs ou aderência aos requisitos. Muitas vezes, para não dizer a maioria, os maiores problema estão em códigos mal escritos, difícies de manter, duplicados, sem padrão, etc. Isso se agrava quando falamos em projetos onde temos mais  de uma pessoa envolvida e com  mudanças na equipes (entrada de pessoas novas por exemplo). Logo, é preciso buscar formas para que esse tipo de coisas não aconteça.

Escrever código também é uma forma de comunicação e é necessário dar a essa prática a mesma atenção de um texto. Embora, códigos sejam instruções para computadores realizar, é preciso pensar em quem irá ler esse código e ter em mente que essa pessoa tem que ser capaz de entender corretamente a mensagem e propósito da arquitetura e forma deste sitema. Outros além dos autores iniciais, muito provávelmente, irão dar manutenção, e com isso precisarão entender bem como as peças se encaixam para resolver o domínio.

Falhar em escrever um código legível, compreensível, com padrões perceptivos, é escrever código legado e fadado a morte.

Código bem feito leva a todos futuros autores a seguir um padrão e a entender sem grandes esforços como as relações se desenrolam. No oposto, código mal escrito, o efeito é inverso: têm-se um empilhamento de funcionalidades, duplicações, diversos padrões, formas, código _obscuro_, etc.

## Estudos e estudiosos do assunto##

Tendo como ponto de partida o fato de que código é uma forma de comunicação semelhante as demais e que é preciso buscar a excelência nisso, muitos estudiosos do assunto buscam formas, processos, ferramentas, para evitar que se produza código ruins (mal escritos). Linguagens como Python, Java, etc criam convensões de boas práticas, _code styles_ (estilo de escrita de software). IDE's criam validadores de sintaxe. Estudiosos de processo, procuram por práticas para ajudar o desenvolver a não escrever ou achar os defeitos o mais breve possível.

Existe um artigo interessante no site de developer da IBM que lista as 11 praticas provadas que realmente ajudam na revisão de código [Leia o artigo](http://www.ibm.com/developerworks/rational/library/11-proven-practices-for-peer-review/).

A revisão de código é uma das práticas, juntamente com o _Pair Programming_ (programação em pares) que vêem de encontro a resolver o problema de código _ruim_. A programação em par é a prática onde duas pessoas trabalham juntas na concepção e escrita da funcionalidade. Ela resolve em parte o problema pois são dois pares de olhos vendo. Porém, ainda é possível escrever coisas que não sejam _"legíveis"_ a futuros programadores daquele sistema.

A revisão de código tem sido mais eficiente nesse sentido. Revisar um código não consiste apenas em outras pessoas lerem o código escrito antes de alguma determinada etapa. Consiste no uso de ferramentas e analisadores também. Inclusive uma boa prática é se algo pode ser analisado pelo computador é melhor que ele que faça e não outro, como por exemplo, complexidade ciclomática, code styles, duplicação, etc.

## Como resolver, como fazer para implementar essa prática ##

Uma vez que se tenha optador pela revisão de código, o primeiro passo consiste em simplesmente fazer. Começar da forma que o time desejar. Os ajustes, como toda boa prática, vem com  tempo, e na medida da maturidade e domínio do processo, vai se mudando e adaptando.

. Como já foi abordado acima, devem buscar ferramentas para analisar a base de código nos mais diversos aspectos. Linguagens como python tem analisadores de pep8(conjunto de boas práticas de escrita de código), analisadores estáticos (analisam variaveis, duplicidade, e outra coisas); já Java tem IDE's que vem com suite grande de ferramentas nesse mesmo sentido. Já em Ruby e Javascript tais coisas são trabalhos em andamento.que vem com suite grande de ferramentas nesse mesmo sentido. Já em Ruby e Javascript tais coisas são trabalhos em andamento.

. todos tem seu código revisto.  Não é só responsabilidade os engenheiros senior revisar. É de todos.

. Uma boa forma é que o código só seja enviado para o repositório (git, svn, etc) se foi revisado. Por isso, o desenvolvedor antes de _comitar_  ou dar _push_ chama outra pessoa e faz.

. Projetos com times grandes podem trabalhar, caso seja usem coisas semelhantes a git, usar patches. Assim, cada um tem seu "repositorio" e na hora de integrar criam e enviam um patch. Esse patch irá ser revisto por algum outro membro.

. Evite fazer com muito código. O ideal, segundo o  artigo citado, é não passar de 200 a 400 linhas de código. Isso reforçar o conceito de fazer pequenos passos e ir enviando para o repositorio.

. Evite o efeito Big Brother... Faça reviews abertos e de forma clara. Deixe tudo muito aberto e simples.

. Torne a prática uma cultura do time e não mais um processo a seguir. A revisão de código deve ser desejada por todos e seguida. Pedida.


## Concluindo ##

Independente da forma e de como irá realizar, é importante entender que código deve ser legível. Código deve ser compreensível a outros humanos também, não somente a máquina. Isso irá aumentar a vida do sistema, facilitar novos colaboradores (para os casos de open source), etc.

Code Review é uma boa forma de garantir isso.

## Leia mais ##
[Effective Code Review - Alex  Gaynor](http://alexgaynor.net/2013/sep/26/effective-code-review/)

[What Makes Peer Code Review an Agile Process? - Lyndsey Clevessy](http://agile.dzone.com/articles/what-makes-peer-code-review-agile)

[Running an Effective Code Review - Esther Schindler](http://www.cio.com/article/472372/Running_an_Effective_Code_Review)
