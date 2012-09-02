---
layout: post
title: "Escrevendo código limpo"
date: 2012-09-02 16:00
comments: true
categories: clean, code, qualidade, metrica
---

Gostaria de começar este artigo com uma frase que está no início do primeiro capítulo do livro [CleanCode][1] do [UncleBob][2]: *"You are reading this book for two reasons. First, you are a programmer. Second, you want to be a better programmer. Good, we need better programmers."*

Vivemos num momento interessante dentro da profissão de desenvolver sistemas: temos as metodologias ágeis, direcionamentos onde o foco é o ser humano ([Peopleware][3]), a busca pela qualidade e pelo desempenho ganham forma e embaseamento, a maturidade nos leva a uma busca constante de excelência, e outras coisas.

Um exemplo disso são os diversos processos e práticas que tem surgido - e solidificado -  nos últimos tempos como TDD, BDD, SOLID (veja no livro do [Clean Code ][1] - Robert Martin aka "Uncle Bob"), etc. Apesar de pessoalmente acreditar que tais iniciativas sejam importantes e determinantes para entregarmos sistemas de qualidade, penso que ainda precisamos de um "algo mais".

Escrever "código", ao contrário do que muitos pensam, não é uma atividade simples. Segundo Brian Kernigan - coautor de AWK programing language, *"é quase o mais complicado dos empreendimentos humanos"* . Todo sistema nasce simples e consciso. Todo sistema nasce bem feito, porém com o passar do tempo e de seu uso e constantes evoluções sua complexidade aumentam e sua "qualidade" provavelmente cai. Mesmo que ele tenha 100% de cobertura de testes (coisa que no mundo real é um grande feito) e seu time siga *a risca* todas as regras.


##TDD e BDD importam##

Antes de mais nada, gostaria de dizer que nada justifica um código sem testes. Testes são uma parte fundamental de um bom código. E eu disse testes. Não disse que fazer TDD ou BDD. Testes garantem um forma simples de manter a aderência as especificações e segurança para realizar futuras mudanças. Autores como Michael Feathers \[[Working Effectivily with Legacy Code][4]\], chegam afirmar que sem testes não existe a possibilidade da melhora contínua, disciplina essencial para termos bons bases de código.

TDD (*Test Driven Development*) e BDD(*Behave Driven Development*) são extrapolações de testes, onde os usamos para nos guiar na busca de uma melhor arquitetura. É possível termos testes automatizados sem seguir tais práticas, porém o contrário não.

TDD e BDD são ótimas ajudantes para termos sistemas robustos e bem feitos, para termos "códigos limpos", mas como disse antes, não são o suficiente.

##Design Patterns e princípios como SOLID importam##

Acredito que a maioria das pessoas que leêm meu blog, são pessoas que se preocupam com a qualidade de seus sistemas. Isso deve se refletir em estudos e muita leitura. Sendo assim, creio que a maior parte já tiveram contato - ou até dominam - assuntos como padrões de projetos, *refactoring*, SOLID, etc.

Vou além, e digo que muitos usam tais conhecimentos em seus dias a dias quando estão a trabalhar em seus projetos.

Tais principio são a "pedra fundamental" sobre o qual o resto todo se apoia. São as tais regras de ouro. Por isso são de extrema importância. Conhecê-las faz um imenso diferencial no código que produzimos pois nos tornamos mais conscientes e preocupados.

Entretanto, somente isso não significa termos um sistema robusto e de qualidade. Já trabalhei em muitos projetos cujos os colegas dominavam e sabiam de "coeur" cada palavra do Design Pattern, mas produziam código *sujos* e com pouca qualidade.

##O que é qualidade? Como é um código de qualidade?##

Responder essa pergunta não é algo simples e estou longe de ter as credencias necessárias para me atrever a tamanha responsabilidade. Por isso, recorri aos grandes autores já citados para buscar o que seria a tal qualidade almejada tanto em nossos código.

Em sua grande maioria, os autores que li (Martin Fowler, Kent Beck, Michael Feather, Uncle Bob, Erich Gamma, Joshua Kerievsky, entre outros) concordam em alguns pontos que listo abaixo.

* __Código bom é aquele que sobrevive ao seu autor__: código deve ser escrito não para compiladores e sim para pessoas. Código bom é aquele que é fácil de entender e compreender a sua forma. Comunica com clareza a sua função e razão de ser.

* __Código tem que ser simples__: a complexidade se dá pela soma das partes. Código simples divide o problema em partes menores e as resolve. E no final chama essas pequenas partes para compor o todo da solução

* __Código bom é aquele "manutenciavel"__: possui toda o ambiente necessário para que ele seja facil de evoluir: testes, documentação, etc.

* __Código que vai além da especificação funcional__: um bom código vai além das especificações do cliente. Ele procura cobrir todos os cenários e estar preparado para as situações não previstas; ele é feito por "não otimistas" (explica mais a frente).


##Com eu faço de qualidade? Além de TDD (BDD), Patterns, SOLID, o que mais precisa ser feito?##

A resposta é mais simples do que você imagina:

__DISCIPLINA__

Saber tudo isso não significa e nem faz a mágica de tornar o seu código maravilhoso. Eu falo isso com propriedade. Por muitas vezes sou um feroz defensor de boas práticas e então, meus colegas acham código meu sem teste, mal escrito, com erros de implementação, etc.

Um outro aspecto é a constante verificação da complexidade, qualidade e cobertura de seu código. A disciplina não será nada se não houver um objetivo à atingir.

Outra coisa na qual acredito é que devemos ser menos otimistas ao escrever nossos sistemas. Citando dois amigos - [Leonardo Balter][6] e [Alexandre Martins][7] - precisamos de trocar o "boné de programador" e fazer mais *"Testes de trollagem"*. Precisamos tentar a todo custo testar os limites do que estamos fazendo. Precisamos ir além da especificação. Michael T. Nygard em seu livro, [Release It][5], diz que sistemas que precisam pensar em suas possíveis falhas e serem capazes de suportar os cenários não previstos.

Inclusive, existe um excelente artigo do pessoal da NetFlix, sobre uma ferramenta chamada de Caos Monkey. Essas ferramenta derruba os servidores e analisa como o sistema se comporta para verificar se tudo é robusto. Isso é um aspecto muito esquecido nas aplicações e cada vez mais determinante na entrega.

Tenho um caso de um sistema muito bem feito, com testes, boa arquitetura, etc, que falhou vergonhasamente quando foi para produção pois esqueceram de configurar o cache corretamente. Pensar nisso é ter a visão holística de que tanto falam diversos autores.

##Ferramentas para ajudar##

Uma grande ferramenta sem dúvida são os testes automatizados. Outra tão boa quanto são aquelas que "medem" diversos parametros, com frequencia de sua base de código, como: dependência ciclomática; duplicidade de código; aderência a convenções de código (Pep8 para python, JSLint, CodeStyle para Java, etc); analise de perfomance; tolerância a falhas; etc.

Ter um servidor de CI (integração contínua) rodando essas ferramentas, testes, e outras coisas que sejam importantes para o time, é uma grande coisa a ser feita. Coloque alertas, encha a caixa de email do pessoal com mensagens de alerta e obriguem a todos terem carinho com o "build". No time agradeço a presença do meu amigo Vinícius que me lembra e nos cobra coisa como essas.


##No final ...##

No final o que mais importa é termos a disciplina e obstinação de sempre buscarmos a melhora contínua do que fazemos. Novas formas, padrões, teorias irão surgir, novas linguagens e ferramentas irão surgir. Porém sempre caberá a nós a busca por fazer nosso trabalhar melhor do que do dia anterior. Esse é o compromisso que quero assumir comigo e com meu trabalho.

Eu não sou um exemplo e nem desejo ser modelo, mas nem por isso devemos acreditar que só os melhores e somente em projetos de "empresas legais" que isso será possível. Faça aos poucos, se comprometa em fazer diferente. Faça e conquiste seu espaço, os resultados irão te ajudar a provar o valor de tais práticas.


[1]: http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882
[2]: http://en.wikipedia.org/wiki/Robert_Cecil_Martin
[3]: http://www.amazon.com/Peopleware-Productive-Projects-Second-Edition/dp/0932633439
[4]: http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052
[5]: http://pragprog.com/book/mnee/release-it
[6]: http://leobalter.net/
[7]: http://blog.m.artins.net/
