---
layout: post
title: "Sistemas com responsabilidades únicas"
date: 2013-03-21 21:09
comments: true
categories: engenharia. software
---

## Introdução ##

Muitos desenvolvedores já estão familiarizados com diversos princípios de engenharia de software, como por exemplo alguns enunciados pelo livro [Clean Code ][1]. Tais princípios ficaram eternizados com a sigla SOLID, que é acronimo e significa:

 *S*ingle Responsability Principle ( Principio de Responsabilidade Única);

 *O*pen Close Principle ( Principio do aberto para extensão e fechado para modificação);

 *L*iskov  Substitution Principle (A classe filha pode ser substituida pela classe pai);

 *I*nterface Segregation Principle (expor interfaces não objetos);
 
 *D*ependency Inversion  Principle ( Dependencias baseadas na abstração e não nas implementações concretas )

Para saber um pouco mais, siga clicando [aqui][2]*


Aplicando essa definições em nossos código, a idéia é ter um código mais limpo: código legível; fácil de compreender por outros desenvolvedores; simples de evoluir; simples de manutenciar; etc. A questão é que, mesmo usando toda essa engenharia, todos nossos sistemas atuais tendem a crescer e ganhar complexidade.

Todos os sistemas nascem simples: com responsabilidades únicas e bem definidas. Assim após a nossa primeira *release*, nosso sistemas evolui, ganhando novas funcionalidades, acertos, melhorias , ajustes para melhorar perfomance, refactorings, etc. Com o passar do tempo, nosso pequena e bem escrito aplicativo, torna-se um megazord de complexidade, duplicidade de código, e outras coisas que nenhum de nós gosta. Enfim, ele se torna um grande legado que ninguém quer mais mexer. 

Tenho certeza que todos tem algum projeto que trabalhou que serve de exemplo para a situação descrita acima.  Lembra daquele sistema que tinha, lá no início, algumas centenas de linha de código apenas e já de milhares (até milhões); ou/e daquele projeto super bem arquitetado e hoje é uma bagunça sem fim que até mesmo que trabalhou desde início se perde para entender como as chamadas *trafegam* para completar uma requisição.

Mesmo que esse ditos projetos estejam usando testes automatizados e tenha sidos feitos seguindo princípios como TDD. Mesmo que eles sofram refactorings constantes, o fato é que eles crescem e vão adquirindo novas responsabilidades antes não previstas. Com isso, vamos torcendo aquele modelo original e amontando código. 

Diante disso, o que vejo e vivencio é que a medida que essas bases de código crescem, fica impossível de manter principios de reutilização, *DRY*, padrões de nomes, *code style*, e diversas outras coisas importantes. Enfm, acabamos um imenso legado que é caro demais de evoluir, muito caro de reescrever e muito importante para nosso cliente que não abra mão dele e tem novas necessidades a serem atendidas.

## Nosso dilema atual ##

Como disse, os sistemas crescem. E com eles suas bases de código. 

Poderíamos dizer que este problema já é conhecido e muito bem abordado pelo Michael Feathers em seu [livro][3] sobre código legado: podemos sim isolar e aplicar todas as técnicas sugeridas, mas bases de código grandes, são bases de código grandes e ponto final. Pdemos melhorar os métodos, encapsular melhor algumas, etc ... a questão que ainda temos um modelo que não foi feito para aqueles novos casos, ainda temos situações novas que não estavam previstas e poucas possibilidades de interface do nosso sistema.

Se não existessem os problemas financeiros ou quaisquer outras _constraints_ tenho certeza que a maioria dos desenvolvedores, diriam que está na hora de reescrever todo o sistema.  Todos nós adoramos projetos *Green Field* (projetos que estão começando do zero).

Em novos projetos, temos as oportunidade de desenhar bem a nossa arquitetura, aplicar novos conceitos e utilizar novas tecnologias.

A questão é que fazer isso com sistemas de milhares de linhas de código é uma tarefa árdua e que custa bastante caro - nenhum gerente, cliente, PO... vai querer pagar por isso - até porque você não estará entregando nenhum valor novo (estará sim se pensarmos em infra, mais request, e outras coisas parecidas, mas poucos clientes percebem isso logo de cara)


## Motivos para reescrever sistemas ##

1. __Tecnologias caducam, envelhecem:__

Muitas tecnologias se tornam ao longo do tempo obsoletas e ultrapassadas. Sempre temos uma nova versão da linguagem, um novo servidor, um banco de dados mais moderno ou que utilize um outro paradigma que resolve melhor o seu problema... enfim a tecnologia evolui e traz novas soluções - e melhores - para os nosso problemas.


2. __Nós aprendemos:__

Com o passar do tempo e com a experiência vemos que, nem sempre o caminho que adotamos foi o melhor. Também vemos que existem jeitos melhores de implementar determinada lógica.

Existe o fato também, que evoluímos como profissionais: com isso vemos que aquele sistema que fizemos a um tempo atrás, poderia ter sido feito de um jeito diferente. Infelizmente mudanças desse tipo não dá para fazer de forma gradual. Geralmente, eles são mudanças radicais e temos que fazer tudo de uma vez só.

3. __todo sistema tem prazo de validade:__

Um outro bom motivo para reescrevermos nosso sistema é ligado ao negócio. Muitas vezes vemos que a forma de nosso negócio mudou e que o sistema atual com sua base de código infinita não nos atende mais. Mesmo que façamos diversos apendices, o sistema não é mais capaz de nos atender com proficiencia. Se tornam aqueles sistemas cheios de jeitinhos para fazer coisas. O usuário tem que fazer um cursinho para saber todos os "pulos do gato" para ele conseguir concretizar uma operação. Sistemas ERPs são os melhores exemplos disso. Você acaba torcendo o seu problema para caber dentro daquele sistema que é impossível de mudar ou reescrever.



## Vamos ao que interessa ##

Fica um bom tempo falando sobre a questão de engenharia de software e do problema de sistemas com muitas linhas de código. Falei também dos motivos que podemo nos levar a querer reescrever um sitemas. Mas para que?

Escrevi sobre tudo isso para mostrar que precisamos dar o passo seguinte no desenvolvimentos de software. Precisamos pensar em sistemas como peças únicas de um conjunto para resolver problemas. Sendo assim, essas unidade deve ser responsavel por resolver um e somente um aspecto do problema e não todo ele. A solução se dá pela soma das partes que agindo em conjunto atendem ao nosso domínio.

Precisamos aplicar os conceitos de SRP (veja acima) na concepção de nosso sistemas. Ao invés de fazermos uma peça única e monolítica que aborde todo o nosso dominio, fazmemos pequenas partes que cuidam de cada aspecto.

Ganhamos com isso sistemas pequenos, e simples de manter.  Num caso que li recentemente, cada peça ficou com poucas centenas de linhas. Isso facilita manter pois bases pequenas são mais simples. Bases pequenas são mais fácil de entender e manter seu padrões; bases pequenas são mais fácil de jogar fora e fazer de novo. No mesmo case que citei acima, eles reescrevem uma parte em uma semana e foi imperceptível para o cliente.

Outro aspecto é que se fizermos com pequenas partes e essas partes existirem independentes uma das outras, podemos ir além. Imagine que eu quebre o sistema em diversos serviços que se falem via REST: eu posso literalmente escrever cada serviço numa linguagem diferente que não vai causar nenhum problema. Com isso posso escolher a melhor tecnologia/linguagem para o meu problema. Além disso, mantendo as interfaces, eu posso refazer todo a parte interna sem afetar as outras peças do conjunto.

Isso é simplesmente o céu de todo desenvolvedor.

Em meu trabalho atual estamos caminhando para algo parecido. Ou seja, uma forma mais orientada a serviços, onde cada sistema tem uma responsabilidade e essa é simples. Manter essa coisa simples e com pouca coisa para resolver é a grande chave do sucesso.

Se olhar arquitetura de grandes portais, produtos web (como [Twitter][4], basecamp, [SoundCloud][2], etc) verá um monte de pequenos sistemas conversando para atender a demanda do usuário.

Se uma parte se tornar o gargalo, podemos melhorar só aquela parte: colocando mais servidores, reescrevendo, etc.

Isso é aplicavel a qualquer contexto.

A alguns anos atrás trabalhei numa empresa que tinha diversos sistemas que eram integrados através de troca de mensagens (queue e brokers). Claro que nem chega perto do que estou propondo mais foi uma semente e vi que dava muito certo.


##Cenas do próximos capítulos ...##

Mais a frente - estou terminando de organizar tudo - pretendo publicar um  novo post explicando melhor como implementar essa questão de sistemas pequenos e com pouco responsabilidade.

Só para deixar curioso, existem formas de fazer sem necessáriamente escrever um monte de sistemas; como existem formas de fazer de forma  bem desacoplada. Enfim fiquem ligados.


[1]: http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882
[2]: http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod
[3]: http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052
