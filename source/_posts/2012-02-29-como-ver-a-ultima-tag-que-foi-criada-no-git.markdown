---
layout: post
title: "Como ver a última tag que foi criada no git"
tags:
- atualidades
- codigo
- deploy
- describe
- git
- tag
status: publish
type: post
published: true
meta:
  _edit_last: "1"
---
O git tem um comando que retornar a descrição de algo. Ele é o git describe e com ele e mais alguns truques é possível detectar qual foi a última tag criada no seu repositório.
Antes de mais nada não se esqueça de fazer um git fetch para ter os dados atuais. E depois execute o comando abaixo:

{% codeblock lang:bash %}

git describe --tags $(git rev-list --tags --max-count=1)

{% endcodeblock %}

Esse comando busca na lista de revisões pelas tags e com isso você consegue ver qual foi a última.  Usei isso para colocar esse dados no meu projeto toda vez que fizer um deploy em produção. Assim sempre terei em algum lugar a última tag que foi subida.
