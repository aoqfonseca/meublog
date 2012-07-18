---
layout: post
title: Usando growl com python e ferramenta de autotest
tags:
- atualidades
- autotest
- growl
- peon
- python
- testes
status: publish
type: post
published: true
meta:
  _edit_last: "1"
---
A um certo tempo atrás trabalhava com Ruby, mais precisamente, desenvolvia utilizando o framework Rails. Dentro desse eco-sistema, existia uma "ferramenta" que sou apaixonado: [Autotest][1] (zentest).

Essa ferramenta fica monitorando seus arquivos ruby e caso faça qualquer alteração ele executa os testes (spec) do projeto. Isso é realmente uma "mão na roda" pois, para quem curte TDD, você fica o tempo todo monitorando as alterações no seu código e vai evoluindo bem.

Atualmente mudei de time e passei a trabalhar em projetos com django/python. Logo, comecei a procurar dentro desse novo ambiente, uma ferramenta similar que me permitisse fazer a mesma coisa. Vi que o pessoal do Dojo usa uma ferramente desenvolvido pelo [Flávio Amieiro][2]. O tempo foi passando e não encontrei nenhuma que me agradasse ao ponto do autotest (facilidade de uso e instalação).

Foi quando encontrei o Peon, desenvolvido pelo [Bernardo Heynemann][3].  O Peon é uma ferramenta que é fácil de instalar (pip install ou baixa e executa make install) e fácil de usar basta:

{% codeblock lang="bash"%}
peon make test -d tests
{% endcodeblock %}

O comando acima é para quando alguém alterar algum arquivo .py no diretório tests ele irá executar o comando make test. Se você apenas chamar o peon, ele irá executar o nosetests para toda mudança em qualquer arquivo python do projeto.

Além disso, ele tem uma integração com a notificação do linux, permitindo em caso de falhar algum teste - por exemplo, ele te avisar. Entretanto, como eu uso o Mac OS, queria poder ter esse mesmos avisos com o Growl.

Pesquisando encontrei uma forma de fazer isso.

Existe uma biblioteca python (py-Growl) que faz essa integração ( semelhante ao pynotify da libnotify do linux). Abaixo um código mostrando como fazer. A explicação é bem simples:

{% codeblock lang:python %}
try:
    import Growl
except ImportError:
     return

path_image = abspath(join(dirname(__file__), image))
icon = {'applicationIcon': Growl.Image.imageFromPath(path_image)}

growl = Growl.GrowlNotifier(app_name, [app_name], **icon)
growl.register()
growl.notify(app_name, title, message)
{% endcodeblock %}

Primeiro você cria um notifier, informando o nome da app (ela será usada para identificar quem está mandando algo para o Growl. Isso é importante), lista de tipos de mensagem que serão enviadas e um dicionário com ícones.

Depois você registra seu notifier e usa o método notify, passando o nome da app que você informou na criação do objeto, um título (um dos tipos que você informou) e a mensagem. E pronto!

Esse código já está no fork que eu fiz do Peon e vou fazer um pull request em breve. Fica a dica de usar o Peon e o Growl. Fica muito maneiro.

[1]: http://www.zenspider.com/ZSS/Products/ZenTest/"
[2]: http://flavioamieiro.com/
[3]: http://blog.heynemann.com.br "Blog do Bernardo Heynemann"
