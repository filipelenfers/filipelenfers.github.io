---
layout: post
title:  "Usando Platform IO como IDE"
date:   2017-03-24 19:50:00 +0000
comments: true
categories: iot platformio nodemcu
---

## O que é o Platform IO ?

O [`Platform IO`][http://docs.platformio.org/en/latest/what-is-platformio.html] é
um ecosistema para desnevolvimento de IoT. Ele se integra a várias
IDEs dando a elas a capacidade e features para o trabalhar com IoT, possui um
gerenciamento de biliotecas e funciona em diversos SOs como Linux, Mac e Windows.

Um conceito muito forte por trás do Platform IO é que você deve ser livre para
escolher a IDE que preferir e SO que preferir para trabalhar com IoT. Além do
foco em facilidade e simplicidade para começar a desenvolver o mais rápido o
possível ao invés de gastar muito tempo preparando seu ambiente de desenvolvimento.

### Porque usar?

A ideia de liberdade do Plaform IO nos permite escolher aonde trabalhar. O Arduino IDE, por exemplo,
é um tanto limitado em seus recursos. Usando o plaform IO podemos usar editores de texto avançados
como Sublime Text e Atom, ou conhecidas IDEs como Visual Studio e Eclipse, e ter todos os recursos
dessas IDEs a mão.

### Lista de frameworks e placas

Para saber se o Platform IO te atende, ou seja é compatícel com a placa e frameworks
que vais usar consulte o link:
[http://docs.platformio.org/en/latest/frameworks/index.html][http://docs.platformio.org/en/latest/frameworks/index.html]

Neste post vamos usar o NodeMCU usando o framework do Arduino.


### Integração com outras IDEs

Aqui demonstramos o uso com o Atom, entretando o Platform IO se integra com várias IDEs.

* Fã de Sublime Text?
* Curte mesmo o Visual Studio?
* Old School? Prefere um VIM ou Emacs ?

Todas são opções de uso do Platform IO.

Através deste link [http://docs.platformio.org/en/latest/ide.html][http://docs.platformio.org/en/latest/ide.html]
verifique se sua IDe é suportada.

###  PlatformIO Plus

O platform IO possui uma versão Plus que é paga. Esta versão entrega mais recursos:

* Testes unitários locais e remotos
* Análise estática de código
* Integração com Cloud IDEs

Mais detalhes e outras features na página do [Platform IO Plus][https://pioplus.com/pricing.html].


## Instalando

Vamos usar o Atom, por ele ser livre e gratuito, desenvolvido pela GitHub e instalar o
plugin do Platform IO nele.

1. Instale o [Atom][https://atom.io]
1. Abra o Atom e use o atalho Ctrl+Shift+P
1. Digite `install pack` e selecione a opção `Settings View: Install Packages And Themes`
1. Na caixa de pesquisa procure por `platformio-ide`.
1. Clica na opção para instalar o `platformio-ide`.

Pronto, tudo certo para começarmos a usar o [Platform IO][http://platformio.org/get-started/ide?install].

## Criando um projeto

TODO http://docs.platformio.org/en/latest/ide/atom.html#quick-start

## Upload para a placa


## Importando projetos

TODO como importar do Arduino IDE
