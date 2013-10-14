---
layout: post
title: "Reinstalando o vim na sua máquina com suporte a python e Ruby"
date: 2013-10-14 17:44
comments: true
categories: vim, python, ruby
---

Esse é um post para ajudar a me lembrar de uma procedimento e quem sabe ajudar alguém com o mesmo problema.

Eu uso como editor padrão o VIM (algumas vezes o MACVim). Além disso uso muito Python e Ruby como linguagens para desenvolver meus projetos. Para facilitar esse meu dia a dia, uso alguns plugins que me ajudam como por exemplo o python-mode e o jedi. O python-mode ajuda com as validações de pep8, pyflakes, etc. Já o jedi ajuda nos imports do python. Para ruby eu tenho o sintaxe highlight mesmo.

Tudo isso funciona perfeitamente no meu MACVim, porém no vim não estava funcionando. Ambos tinham sido instalados via homebrew. Buscando pelo Google, achei que a solução era compilar o vim manualmente. Isso realmente resolveu meu problema, e segue abaixo os passos que fiz. Primeiro certifique-se  tem instalado o mercury no seu computador (hg).


hg clone https://vim.googlecode.com/hg/ vim_source
cd vim_source
./configure --disable-nls --enable-multibyte --with-tlib=ncurses --enable-pythoninterp --enable-rubyinterp --with-features=huge
make -j 3 && sudo make install


Com isso o sistema irá reinstalar todo o vim com os suportes e links corretos.

Espero que ajuda alguém.
