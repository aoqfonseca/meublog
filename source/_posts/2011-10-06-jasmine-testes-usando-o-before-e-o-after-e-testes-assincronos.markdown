---
layout: post
title: "Jasmine testes:  Usando o before e o after e testes assincronos."
tags:
- agil
- "ass\xC3\xADncrono"
- jasmine
- javascript
- setup
- TDD
- teste
status: publish
type: post
published: true
---
Um dos pontos fortes que considero no Jasmine é seu "suporte" a execuções assíncronas para teste. Isso significa, que dado aquele seu código, que tem um chamada que tem duração de tempo, ocorre com callback, etc, você será capaz de testar isso com relativa facilidade com Jasmine.

Somente para lembrar, todo arquivo de teste do Jasmine é composto de um contexto onde temos diversas asserts que irão validar o funcionamento do nosso código:

{% codeblock lang:javascript %}
describe("teste de algo", function(){
    it("deve acontecer algo e o valor ser outro", function(){
        expect(true).toBeTruthy();
    });
});
{% endcodeblock %}

No código acima criamos o contexto com a função describe, que recebe um texto com a descrição e uma função a ser executada. Dentro do corpo da função a gente tem a chamada do it que também recebe um texto com descrição e um função.

Uma coisa legal é que como qualquer framework de teste, ele tem métodos para executar código antes e depois de cada teste (acertiva). Esse métodos são o beforeEach (para executar algo antes) e o afterEach(para executar o depois).
Essas funções recebem como argumento uma função cujo o corpo será executado. Veja o exemplo abaixo:

{% codeblock lang:javascript %}
describe("teste algo com before e after", function(){
    var variavel;
    beforeEach(function()
        variavel = true;
    });

    afterEach(function(){
        variavel = false;
    });

    it("teste", function(){
        expect(variavel).toBeTruthy();
    });
});
{% endcodeblock %}

Mais isso não é o objetivo do artigo. O nosso objetivo é mostrar o quão é fácil colocar a rotina de espera para dentro do seu teste:

{% codeblock lang:javascript %}
describe("teste algo com before e after", function(){
    var variavel;
    beforeEach(function(){
        variavel = true;
        setTimeout(function(){
            variavel = false;
        }, 100);

    });

    it("teste", function(){
        expect(variavel).toBeTruthy();
        waits(200);
        runs(function(){
            expect(variavel).toBeFalsy();
        });
    });
});
{% endcodeblock %}

O método de waits que usamos acima, gerar uma espera para a execução de 200 milisegundos. Depois ele irá executar na ordem, o contéudo das funções runs que vierem em seguida. Com isso podemos ter testes para nossas animações ou até chamadas com callback. Para callback, ao invés de usarmos a função waits, devemos usar a a função waitFor que recebe uma função que retornará true ou false.

Bem ficamos por aqui. Leia a documentação do projeto e aguarde nosso próximo posts. Aguardo os comentários.
