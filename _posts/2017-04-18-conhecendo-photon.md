---
layout: post
title:  "Conhecendo o Photon - Particle.io"
date:   2017-04-18 19:50:00 +0000
comments: true
categories: iot
---

## [](#oquee) O que é a Particle e o Photon ?

Particle (TODO link do particle home) é uma plataforma completa para IoT que fornece tanto os dispositivos (como o Photon) quanto uma plataforma em cloud para com que o dispositivo envie e receba dados, faz logs dos eventos e permite conectar webhooks a ela.
A Particle fornece ferramentas de desnevolvimento e SDKs para que você posso criar programas que interagam com os dispositivos. Uma coisa interessante é que o Patricle permite fazer o flash dos programas para o dispositivo de forma remota, via Wi-Fi.

A plataforma cloud da Particle é gratuíta, até 25 dispositivos ou 250k de eventos (evnio e recebimento de dados) por mês. Existem outros planos que podem ser conferidos nesta página.(TODO link preços https://www.particle.io/products/hardware/electron-cellular-dev-kit)

O Photon (TODO link do photon) é um dos dispositivos que Particle vende, ele é composto de um microcontrolador STM32 ARM Cortex M3 e um chip Cypress Wi-Fi. É um dispositivo pequeno e que possui um pequeno led imbutido na porta D7 para testes.

TODO imagens do Photon.

O Photon já vem com um firmware instalado chamado Tinker (TODO link para tinker) que permite controlar as portas do dispositivo pelo celular, fazendo escritas ou leituras nas suas portas.

A Particle vende também o Electron que ao invés de Wi-Fi usa uma rede de ceular 2G/3G e já vem com plano de dados embutido.Neste artigo vamos focar no Photon.

Com todos esses recuros usar o Photon permite uma prototipação rápida e fácil, sendo uma boa escolha para projetos de IoT. Na própria documentação da Particle eles também ajudam você a trnasformar um protóprio em um produto (TODO add link https://docs.particle.io/guide/how-to-build-a-product/intro/).

## [](#setup) Setup

### [](#setupphoton) Setup do Photon

Para fazer o setup emum novo Photon você precisa:

1. Baixar a app da Particle no seu celular.
1. Conectar o Photon no USB para ligar ele.
1. O Photon vai emitir uma rede Wifi, conecte seu celular nela.
1. Abra o aplicativo da Particle e registre o seu Photon.
1. Pronto, agora o Photon poderá ser manipulado via Tinker.

Link para documentação oficial: (https://docs.particle.io/guide/getting-started/start/photon/#step-1-power-on-your-device)[https://docs.particle.io/guide/getting-started/start/photon/#step-1-power-on-your-device]

O vídeo abaixo demonstra o setup e como fazer um teste via Tinker, fazendo o LED embarcado na placa ligar e desligar pelo celular:
<iframe src="https://player.vimeo.com/video/178282058" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/178282058">Particle Photon: Setup &amp; Blink</a> from <a href="https://vimeo.com/particle">Particle</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

## [](#tinker) Tinker

O Tinker é um programa para rodar no seu dispositivo que permite que a mobile app da Particle o controle, permitindo fazer escritas e leituras nas portas
de forma rápida e fácil. É excelente para testes e protótipos sem sequer ter que escrever código.
Abaixo vamos fazer uns exemplos práticos de uso do Tinker.

Os Photons já vem com o Tinker embarcado de fábrica.

Mais detalhes sobre o Tinker: (https://docs.particle.io/guide/getting-started/tinker/photon/)[https://docs.particle.io/guide/getting-started/tinker/photon/]

Para puxar a app mobile use os links abaixo:
   - [iPhone](https://itunes.apple.com/us/app/particle-build-photon-electron/id991459054?ls=1&mt=8)
   - [Android](https://play.google.com/store/apps/details?id=io.particle.android.app)
   - [Windows Phone](https://www.microsoft.com/en-us/store/p/particle/9nblggh4p55n)

Abaixo vamos mostrar alguns exemplos de testes feitos usando o Tinker. Você já teve ter o Photon com o seu setup feito para isso.

***Os exemplos abaixo foram tirados da própria página da Photon: [https://docs.particle.io/guide/getting-started/tinker/photon/](https://docs.particle.io/guide/getting-started/tinker/photon/), aqui apresentarei uma versão resumida.***

### [](#tinkerPiscarLed) Acender LED - Escrita Digital
Como o Photon já tem um LED embarcado na porta de D7 vamos usar ele no primeiro exemplo.

1. Conecte o app mobile da Particle com seu dispositivo Photon.
1. Na tela do Tinker clique no `D7` e escolha a opção `digitalWrite`.
1. A palavra `LOW` irá aparecer ao lado do `D7`, clique outra vez no `D7` e a saída mudará para `HIGH` e o LED acenderá.
1. Ao clicar novamente no `D7` ele muda para `LOW` e apaga o LED.
1. Você pode resetar o modo do `D7` ao manter ele presionado por alguns segundos, assim você pode novamente escolher posteriormente se ele será um `digitalWrite` ou `digitalRead`.

TODO !!! vídeo de demonstração.

### [](#tinkerPiscarLed) Acender LED com controle de luminosidade - Escrita Analógica
Neste exemplo vamos conectar um LED ao nosso Photon e usar a escrita analógica para mudar a luminosidade do LED.

### [](#tinkerLeituraDigital) Leitura Digital
TODO mostrar leitura digital

### [](#tinkerLeituraAnalógica) Leitura Analógica
TODO mostrar leitura analógica


## [](#webide) Desenvolvendo

### [](#webide) Usando WebIDE

### [](#particlefunctions) Particle functions

### [](#particlevariables) Particle variables

### [](#webide) Resturando o Tinker

### [](#webhooks) Webhooks


## IDE Local

## [](#docs) Documentação
