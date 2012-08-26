---
layout: post
title: "Entregando sistemas robustos"
date: 2012-08-25 19:11
comments: true
categories: 
---

A muito tempo atrás trabalhei com uma pessoa, Jorge Baccar, que me ensinou que deveria evitar o perfil de "programador otimista".  O "programador otimista" é o tipo de profissional que só se preocupava em implementar o "caminho feliz do sistema": implementa o caso de sucesso ou exatamente pedido pelo cliente. Por exemplo: se o cliente quisesse uma funcionalidade para criar novo usuário (cadastro), nosso programador otimista, só implementaria o necessário para ter um novo usuário - nem pensaria em validações de nome correto, email correto, etc. 

Para um cliente desavisado, esse profissional cumpre com sucesso e, de certa forma, velocidade suas tarefas. Porém, no final das contas, ele não entrega uma solução completa pois caso algo saia um pouco do cenário de sucesso, o sistema irá congelar e se comportar de forma bizarra. 

##Todos nós somos programadores otimistas

Todos nós somos programadores otimistas. Quanto de nós já não enfrentou prazos curtos de entrega onde existia espaço para mais nada além de fazer o mínimo necessário para atender aos pedidos do cliente ? 

Entretanto mesmo com prazos curtos de entrega, conexões falham, bancos falham, servidores param/travam, filers corrompem, e por aí vaí. Assim, nesse contexto, maioria de nossas funcionalidades não estão preparadas para lidar com essas situações caóticas e mesmo assim continuar funcionando sem a necessidade de uma intervenção humana.

Elas não são robustas. 

##Sistema não são ilhas

Nos sistema atuais é quase impossível que você não tenha que se conectar a um outro sistema. Isso mesmo sem considerar que um banco de dados é um sistema externo. Hoje, inclusive tem sido defendido, a maioria dos sistemas são grande mashups - mistura e conexão - de diversos sistemas. 

Se você fez um site de venda, terá que se conectar com uma api de cobrança. Outro, você terá que se conectar ao servidor de e-mail, ou então terá que avisar a um outro sistema sobre uma atividade sua. E por aí temos diversos exemplos. 

Se os nossos sistemas podem dar erros/defeitos, por que esses outros também não podem? Será que nunca ocorrerá de sua internet cair?

Imaginando que só tenha pensando na funcionalidade pedida pelo seu cliente, enquanto tudo estiver funcionando, ele estará super feliz. Porém o que aconteceria com seu sistema sem uma dessa pontas falhasse? Você ficaria com uma transação incompleta ? O seu sistema iria parar de funcionar? 

## Não existe sistema que nunca falhou

Não existe um sistema que esteja rodando um minimo de tempo em produção que nunca tenha falhado. Imagine agora que esse sistema é um daqueles que você depende para completar uma operação, como por exemplo uma venda. 
Se a gente não pensar em criar algo mais tolerante a falha, provavelmente o seu sistema, no exemplo de vendas, iria parar totalmente gerando um prejuízo enorme. Imagine agora que esse seu sistema fosse o site de vendas da amazon (seriam milhões a cada hora que não conseguisse vender). 

## Um livro para ajudar

Recentemente li um livro que fala exatamente sobre esse assunto. O livro é o [Release It][1] do Michael T. Nygard. Nele o autor explica de forma detalhada como a gente pode se precaver de sermos um programador otimista e quais são as armadilhas que devemos evitar se quisermos produtos mais robustos. 
Recomendo muito essa leitura.

## Mão na massa - O que fazer

Determine o domínio de seu problema. Em seguinda, monte um esquema com todos os possíveis pontos de falhas e procure soluções e formas de implementar para que seu sistema seja robusto.

No caso de um sistema de venda, você pode, por exemplo optar por um processamento assíncrono do meio de pagamento usando uma fila para não limitar .

Pense no seu sistema além da funcionalidade. Pense no seu sistema como um imenso ecossistema. 


[1]: http://pragprog.com/book/mnee/release-it




