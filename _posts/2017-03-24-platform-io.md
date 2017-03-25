---
layout: post
title:  "Usando Platform IO como IDE"
date:   2017-03-24 19:50:00 +0000
comments: true
categories: platformio nodemcu iot
---

## [](#oquee) O que é o Platform IO ?

O [`Platform IO`](http://docs.platformio.org/en/latest/what-is-platformio.html) é
um ecosistema para desnevolvimento de IoT. Ele se integra a várias
IDEs dando a elas a capacidade e features para o trabalhar com IoT, possui um
gerenciamento de biliotecas e funciona em diversos SOs como Linux, Mac e Windows.

Um conceito muito forte por trás do Platform IO é que você deve ser livre para
escolher a IDE que preferir e SO que preferir para trabalhar com IoT. Além do
foco em facilidade e simplicidade para começar a desenvolver o mais rápido o
possível ao invés de gastar muito tempo preparando seu ambiente de desenvolvimento.

### [](#porque) Porque usar?

A ideia de liberdade do Plaform IO nos permite escolher aonde trabalhar. O Arduino IDE, por exemplo,
é um tanto limitado em seus recursos. Usando o plaform IO podemos usar editores de texto avançados
como Sublime Text e Atom, ou conhecidas IDEs como Visual Studio e Eclipse, e ter todos os recursos
dessas IDEs a mão.

### [](#placas) Lista de frameworks e placas

Para saber se o Platform IO te atende, ou seja é compatícel com a placa e frameworks
que vais usar consulte o link:
[http://docs.platformio.org/en/latest/frameworks/index.html](http://docs.platformio.org/en/latest/frameworks/index.html)

Neste post vamos usar o NodeMCU usando o framework do Arduino.


### [](#aprofundando) Integração com outras IDEs

Aqui demonstramos o uso com o Atom, entretando o Platform IO se integra com várias IDEs.

* Fã de Sublime Text?
* Curte mesmo o Visual Studio?
* Old School? Prefere um VIM ou Emacs ?

Todas são opções de uso do Platform IO.

Através deste link [http://docs.platformio.org/en/latest/ide.html](http://docs.platformio.org/en/latest/ide.html)
verifique se sua IDE é suportada.

### [](#plus) PlatformIO Plus

O platform IO possui uma versão Plus que é paga. Esta versão entrega mais recursos:

* Testes unitários locais e remotos
* Análise estática de código
* Integração com Cloud IDEs

Mais detalhes e outras features na página do [Platform IO Plus](https://pioplus.com/pricing.html).


## [](#instalando) Instalando

Vamos usar o Atom, por ele ser livre e gratuito, desenvolvido pela GitHub e instalar o
plugin do Platform IO nele.

1. Instale o [Atom](https://atom.io)
1. Abra o Atom e use o atalho Ctrl+Shift+P
1. Digite `install pack` e selecione a opção `Settings View: Install Packages And Themes`
1. Na caixa de pesquisa procure por `platformio-ide`.
1. Clica na opção para instalar o `platformio-ide`.

Pronto, tudo certo para começarmos a usar o [Platform IO](http://platformio.org/get-started/ide?install).

## [](#criando) Criando um projeto

* No menu `PlaformIO` no topo clique em `Initialize or Update PlatformIO Project`

[![Incializando o projeto]({{ site.github.url }}/assets/images/post/2017-03-24-platform-io/Capturar.PNG)][capturar_1]

* Selecione a placa com que desejar trabalhar (no meu caso o `NodeMCU`) e o diretória em que estará o projeto.
* clique em `Initialize`, o processamento pode demorar um pouco pois o Plataform IO irá instalar o que será necessário para desenvolver no ambiente.
* Será criado uma estrutura de diretórios, já com os arquivos de configuração e gitignore.

[![Estrutura de diretórios]({{ site.github.url }}/assets/images/post/2017-03-24-platform-io/Capturar3.PNG)][capturar_3]

* Clique com o botão direito na pasta 'src' e clique em `new file`.
* De o nome do arquivo como `main.cpp`

[![Criar arquivo]({{ site.github.url }}/assets/images/post/2017-03-24-platform-io/Capturar5.PNG)][capturar_5]

* Você será requisitado a instalar o `Clang` para ter um auto complete inteligente. Este passo é opcional.
* Caso deseje instalar o `Clang` clique na opção `Install Clang`.
* Você será redireciona com a página com as intruções de como instalar com Clang em diversos SOs.

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

* No menu `PlaformIO` no topo clique em `Build`.
* O código será compilado e será apresentada uma mensagem em verde indicando o sucesso.

* Conecte seu dispositvo conectado na USB do computador
* No menu `PlaformIO` no topo clique em `Upload`.
* Note que a COM foi automaticamente detectada e o upload iniciado.

* Com o upload feito abra o Serial Monitor, No menu `PlaformIO` no topo clique em `Serial Monitor`.
* O console na parte de baixo da tela será aberta e podemos ver a cada 1 segundo sendo impresso na tela "Teste!"

[![Serial Monitor]({{ site.github.url }}/assets/images/post/2017-03-24-platform-io/Capturar11.PNG)][capturar_11]

## [](#importando) Importando projetos

Podemo importar projetos de Arduino IDE no Platform IO.

* No menu `PlaformIO` no topo clique em `Import Arduino IDE Project...`
* Selecione a pasta do projeto e escolha o dispositvo

[![Estrutura de diretórios]({{ site.github.url }}/assets/images/post/2017-03-24-platform-io/Capturar13.PNG)][capturar_13]

* Clique em `Import`
* O projeto estará no menu lateral a esquerda já dentro da estrutura de diretórios do PlatformIO.
* Pronto, seu projeto está disponível do PlatformIO


## [](#pronto) Pronto!

Agora você já tem o ambiente pronto para usar o Platform IO como ambiente de desenvolvimento.
É um ambiente muito mais rico que o Arduino IDE, na minha opinião! Espero que vocês
apreciem usar o Platform IO.


## [](#aprofundando) Aprofundando

* [Instalando bibliotecas](http://docs.platformio.org/en/latest/librarymanager/index.html)
* [Detalhes sobre o funcionamento do Linter em arquivos .INO](http://docs.platformio.org/en/latest/ide/atom.html?highlight=INO#smart-code-linter-is-disabled-for-arduino-files)
* [Controle de dependências](http://docs.platformio.org/en/latest/librarymanager/ldf.html)

[capturar_1]:{{site.github.url}}/assets/images/post/2017-03-24-platform-io/Capturar.PNG
[capturar_3]:{{site.github.url}}/assets/images/post/2017-03-24-platform-io/Capturar3.PNG
[capturar_5]:{{site.github.url}}/assets/images/post/2017-03-24-platform-io/Capturar5.PNG
[capturar_11]:{{site.github.url}}/assets/images/post/2017-03-24-platform-io/Capturar11.PNG
[capturar_13]:{{site.github.url}}/assets/images/post/2017-03-24-platform-io/Capturar13.PNG
