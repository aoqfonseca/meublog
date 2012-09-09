---
layout: post
title: "Design Pattern e Linguagens dinamicas"
date: 2012-09-08 21:16
comments: true
categories:
---

Logo na introdução do livro do GoF, na primeira frase que acredita ser da maior importância para quem deseja ser um desenvolvedor. É ela : *"Projetar software orientado a objetos é difícil, mas projetar software reutilizável  orientado a objetos é ainda mais complicado"* .

Fazendo a ponte com um post anterior, escrever código de qualidade, sem saber algo sobre Padrões de Arquitetura (design patterns) é quase impossível. Brinco até que está difícil de estar trabalhando sem saber isso, pois quase toda entrevista o pessoal adora perguntar algo do assunto.  Fora esse aspecto de seleção, saber patterns é uma boa forma de começar a escrever bons sistemas.

Patterns foram uma verdade absoluta, uma lei escrita em pedra até a muito pouco tempo atrás. Ouso dizer que para muitos é quase um axioma onde se um dia for quebrado alterará o equilíbrio da **"vida no universo"**. Entretanto, com o crescimento do uso de linguagens dinamicas e com paradigmas de classe aberta, parece que a coisa tem mudado um tanto.

Muitos fazem "piadas" com o livro do Gof (Gang of Four - Design Patterns, Eirc Gamma, Richard Helm,  Ralph Johson e John Vlissides),  dizendo que na verdade o título de livro deveria ser "Como tornar o C++/ Java menos ruim", pois a maioria das soluções apresentadas giram em torno da deficiencias dessas linguagens (Tipagem estática, falta de closures, não ter funções como first class, não terem modelos de open class, etc) .  Sendo, assim, quando temos uma linguagem que não tem essas tais limitações, usar patterns é algo desnecessário.

Concordo em parte com o parágrafo acima. Primeiro é preciso considerar que o livro foi escrito à mais de __14 anos__ ( primeira edição saiu em 1996 ou 1997) e pouco se conhecia de linguagens como Python,  Ruby, Groovy, Scala, entre outras semelhantes (embora algumas já existissem).  As duas linguagens que vinham sendo usadas em larga escala eram exatamente o Java e o C++.

Outro aspecto que devemos levar em consideração é que mesmo usando uma linguagem dita moderna, isso não invalida o uso ou conhecimento de padrões de arquitetura. Muito pelo contrário: é importante que conheçamos as motivações por trás de tudo, para que possamos adaptar a nova realidade as soluções catalogadas.

É praticamente impossível pensarmos em escrever uma aplicação, ela ser entregue e jamais ser tocada novamente. Na maioria dos casos ela evoluirá com ou sem o nosso consentimento ou participação. Sendo assim, escrever usando ou baseando-se em padrões facilita em muito o entendimento dos futuros donos deste sistema e além do mais. Quando falamos de equipe, até a comunicação do "como deve ser feito" fica facilitada: "Vamos fazer com um pattern de DTO, por iso temos que fazer os Value Objects, etc".

##Linguagens Dinamicas tem melhores ferramentas:##

Tomando como base Python, Ruby e Groovy, linguagens dinamicas possuem um leque maior de recursos que facilitam em muito criarmos sistemas que evoluam facilmente.  Recursos como closures, open class (classes abertas),  blocos, generadores, decorators, etc, num primeiro momento chegam a negar a necessidade de se criar modelos complexos .

Para que criar um modelo complicado de interfaces, heranças, composições e etc quando podemos simplesmente passar um função como argumento, ou então, capturar e criarmos métodos que ainda nem existem ?

Todos esses recurso facilitam em muito a criarmos sistemas que são simples de evoluir e reutilizar.


##Uma coisa não exclui a outra##

Diante de tudo que foi dito acima, poderia simplesmente, sem muito medo de errar, dizer que Designs Patterns são obsoletos e desnecessários frente a novas ferramentas que possuímos hoje.

Como já disse, concordo em parte com tal afirmação.  Muitas limitações deixam de existir e com isso a necessidade de contorná-las, porém, outros problemas persistem ou tantos outros surgiram.

Padrões não devem ser usados como verdades absolutas e sim como guias para a construção de um sistema bem feito.  Conhêce-los é como uma receita: enquanto estamos aprendendo seguimos-as sem alterar nada, entretanto, a medida que ganhamos experiência sentimos confiante a mudar um pouco e inovar.  Vale ressaltar que não saímos do nada. Não "reinventamos a roda". Adaptamos algo que já se provou sucedido a nossa realidade e ferramentas.


##Algumas referências sobre o assunto ##

*Neal Ford* tem uma excelente apresentação que fez na Oscon de 2009, onde mostra que algum patterns não fazem mais sentido, porém outros ainda se mostram atuais.  Uncle Bob, em um vídeo e texto em seu blog faz uma afirmação parecida: Diz que design patterns ainda são tão atuais quanto antes e importantes. As bases que compões as soluções ainda são "sólidas" - preferir composição a herança.


Convido a quem está lendo a pelo menos conhecer algumas soluções para até mesmo ter do que falar mal. Verá que mudará a forma como pensa a solução.



