---
layout: post
title:  "Usando Platform IO como IDE"
date:   2017-03-24 19:50:00 +0000
comments: true
categories: iot platformio nodemcu
---

TODO imagens!!!

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

1. No menu `PlaformIO` no topo clique em `Initialize or Update PlatformIO Project`
1. Selecione a placa com que desejar trabalhar (no meu caso o `NodeMCU`) e o diretória em que estará o projeto.
1. clique em `Initialize`, o processamento pode demorar um pouco pois o Plataform IO irá instalar o que será necessário para desenvolver no ambiente.
1. Será criado uma estrutura de diretórios, já com os arquivos de configuração e gitignore.
1. Clique com o botão direito na pasta 'src' e clique em `new file`.
1. De o nome do arquivo como `main.cpp`

Você será requisitado a instalar o `Clang` para ter um auto complete inteligente. Este passo é opcional.

1. Caso deseje instalar o `Clang` clique na opção `Install Clang`.
1. Você será redireciona com a página com as intruções de como instalar com Clang em diversos SOs.

Dentro do arquivo main.cpp cole o código:

```cpp
/**
 * Imprime na serial a cada 1 segundo
 */
#include "Arduino.h"

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  Serial.println("Teste!");
   // espere um segundo
  delay(1000);
}
```

1. No menu `PlaformIO` no topo clique em `Build`.
1. O código será compilado e será apresentada uma mensagem em verde indicando o sucesso.
1. Conecte seu dispositvo conectado na USB do computador
1. No menu `PlaformIO` no topo clique em `Upload`.
1. Note que a COM foi automaticamente detectada e o upload iniciado.

1. Com o upload feito abra o Serial Monitor, No menu `PlaformIO` no topo clique em `Serial Monitor`.
1. O console na parte de baixo da tela será aberta e podemos ver a cada 1 segundo sendo impresso na tela "Teste!"

## Importando projetos

Podemo importar projetos de Arduino IDE no Platform IO.

1. No menu `PlaformIO` no topo clique em `Import Arduino IDE Project...`
1. Selecione a pasta do projeto e escolha o dispositvo
1. Clique em `Import`
1. O projeto estará no menu lateral a esquerda já dentro da estrutura de diretórios do PlatformIO.
1. Pronto, seu projeto está disponível do PlatformIO
