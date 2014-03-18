---
layout: post
title: "Quando fazer Refactoring"
date: 2014-02-04 16:59
comments: true
categories: 
---

TL; DR;
Sempre que falo sobre refactoring, sempre ouço a pergunta de quando fazer e como alocar tempo para realizá-lo.

Para mim não existe um quando e nem quantidade de tempo para refactoring: sempre é momento de fazê-lo. Se simplesmente o refactoring não for considerado, mesmo que tenha a melhor estrutura e arquitetura, seu sistema irá ficar obsoleto e se tornará um grande legado. Fazer refactoring é um dos pilares para mantermos a qualidade da base de código.


## REFACTORING ##

[Martin Fowler](http://martinfowler.com/) em seu livro [Refactoring](http://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672), define como sendo a prática de melhorar o código em busca de maior clareza, melhor estrutura para extensão, maior comunicação, etc ... sem alterar o comportamento.

Refactoring é a técnica para manter o seu código atual, sem duplcidades (DRY), seguindo boas práticas e princípios como o [SOLID](http://en.wikipedia.org/wiki/SOLID_(object-oriented_design)).

Uma boa analogia é de sempre buscarmos a melhor forma de resolver o mesmo problema, tendo em vista a clareza, a boa comunicação, facilidade de extensão. Note aqui que não falei de perfomance. 


## PORQUE REFACTORING ##

[Kent Back](http://pt.wikipedia.org/wiki/Kent_Beck), possui uma citação interessante que explica bem o porque:

_Programs have two kinds of value: what they can do for you today and what they can do for you tomorrow. Most times when we are programming, we are focused on what we want the program to do today. Whether we are fixing a bug or adding a feature, we are making today's program more valuable by making it more capable.
You can't program long without realizing that what the system does today is only a part of the story. If you can get today's work done today, but you do it in such a way that you can't possibly get tomorrow's work done tomorrow, then you lose. Notice, though, that you know what you need to do today, but you're not quite sure about tomorrow. Maybe you'll do this, maybe that, maybe something you haven't imagined yet.
I know enough to do today's work. I don't know enough to do tomorrow's. But if I only work for today, I won't be able to work tomorrow at all.
Refactoring is one way out of the bind. When you find that yesterday's decision doesn't make sense today, you change the decision. Now you can do today's work. Tomorrow, some of your understanding as of today will seem naive, so you'll change that, too.
What is it that makes programs hard to work with? Four things I can think of as I am typing this are as follows:_

_1. Programs that are hard to read are hard to modify._

_2. Programs that have duplicated logic are hard to modify._

_3. Programs that require additional behavior that requires you to change running code are hard to modify._

_4. Programs with complex conditional logic are hard to modify._

_So, we want programs that are easy to read, that have all logic specified in one and only one place, that do not allow changes to endanger existing behavior, and that allow conditional logic to be expressed as simply as possible._
_Refactoring is the process of taking a running program and adding to its value, not by changing its behavior but by giving it more of these qualities that enable us to continue developing at speed._

Transcrevendo, seria dizer que todos os sistemas possuem 2 valores: o que pode ser feito hoje e que pode ser feito amanhã.  Na maioria dos casos, sempre pensamos no presente. Porém, sistemas evoluem e novas funcionalidades, correções de bugs, vão ocorrendo e o código sendo alterado.  Nesses ciclos, acabamos duplicando código, adicionando responsabilidades a métodos, alterando as lógicas, etc. Com isso o código vai ficando confuso e complexo. 

A técnica de Refactoring, é justamente olhar para esse sistema e buscar sempre um jeito melhor te atender os requisitos. Jeito esse que leva em conta coisas como comunicação, clareza, facilidade de extensão, e coisas simmilares.

Por isso, se quisermos manter um sistema com uma boa qualidade e simples de ser entendido e extendido, é muito importante sempre realizarmos refactorings. 

## REFACTORING, TESTES AUTOMATIZADOS e TDD ##

Não é meu objetivo entrar muito a fundo no assunto, entretanto, é importante dizer que é muito díficil fazer Refactoring em sistemas sem testes automatizados. Não é impossível. Mas extremamente difícil. Isso porque, ao final de um ciclo, você terá que testar se nenhum comportamento esperado foi alterado.

Por isso, de forma a simplificar, não fazemos refactoring sem testes. Caso o seu sistema não tenha testes, primeiro, faça o teste. Depois faça o Refactoring. Nisso podemos encaixar o TDD. O próprio trabalho de escrever os testes te ajudará a decidir o que mudar, a melhor forma, etc. 



