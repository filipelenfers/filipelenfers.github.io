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

O Photon (TODO link do photon) é um dos dispositivos que Particle vende, ele é composto de um microcontrolador STM32 ARM Cortex M3 e um chip Cypress Wi-Fi. É um dispositivo pequeno e que possui um pequeno led imbutido na porta D7 para testes.

TODO imagens do Photon.

O Photon já vem com um firmware instalado chamado Tinker (TODO link para tinker) que permite controlar as portas do dispositivo pelo celular, fazendo escritas ou leituras nas suas portas.

Outra coisa interessante da própria Particle são as `Particle functions`, funções que podem ser invocadas no dispositivo via API, e as `Particle variables` que são um jeito fácil de subir o valor de uma variável para a cloud da Particle. Abaixo falamos um pouco mais sobre esses dois recursos.
A plataforma da Particle também conta com um facilidades de publish/subscribe, aonde você pode fazer publish privado (para somente 1 dispositivo) ou público (para todos que se inscreverem no canal).

Com todos esses recuros usar o Photon permite uma prototipação rápida e fácil, sendo uma boa escolha para projetos de IoT. Na própria documentação da Particle eles também ajudam você a trnasformar um protóprio em um produto (TODO add link https://docs.particle.io/guide/how-to-build-a-product/intro/).

A plataforma cloud da Particle é gratuíta, até 25 dispositivos ou 250k de eventos (evnio e recebimento de dados) por mês. Existem outros planos que podem ser conferidos nesta página.(TODO link preços https://www.particle.io/products/hardware/electron-cellular-dev-kit)

A Particle vende também o Electron que ao invés de Wi-Fi usa uma rede de ceular 2G/3G e já vem com plano de dados embutido.Neste artigo vamos focar no Photon.

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

***Os exemplos abaixo foram tirados da própria página da Photon, aqui apresentarei uma versão resumida e um vídeo de demonstração. Para mais detalhes acessa a página [https://docs.particle.io/guide/getting-started/tinker/photon/](https://docs.particle.io/guide/getting-started/tinker/photon/).***

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

1. Conecte um LED na porta `D0` e ao `GND`. A porta `D0` é um `PWN` e pode simular uma saída analógica.
1. Clique na na porta `D0` e escolha `analogWrite`.
1. Um slider aparecerá ao lado da porta permitindo que você escolha valores entre 0 e 255.
1. Use o slider e veja o brilho do LED aumentando e diminuindo.
1. Você pode resetar o modo do `D0` ao manter ele presionado por alguns segundos.

TODO !!! vídeo de demonstração.

### [](#tinkerLeituraDigital) Leitura Digital

1. Conecte um sensor digital de som na porta `D0`. Outro jeito é conectar a saída `3v3` diretamente ao `D0` aonde você sempre receberá um sinal `HIGH`.
1. Clique na na porta `D0` e escolha `digitalRead`.
1. O aplicativo começará a ler os sinais digitais e mostrará se está lendo `HIGH` ou `LOW`.
1. Faça seu sensor digital de som mudar de estado, ou desligue/ligue o conexão com o `3v3` para mudar a leitura e clique brevemente sobre `D0` fazendo ele atualizar o valor lido.

TODO !!! vídeo de demonstração.

### [](#tinkerLeituraAnalógica) Leitura Analógica

1. Conecte um sensor de luz (fotoresistor - LDR)  no pino `A0` e no `A5`.
1. Conecte um resistor (usei um de 10K) de luz (fotoresistor - LDR)  no pino `A0` e no `GND`.
1. No mobile app configure o `A5` para `digitalWrite` e troque ele para `HIGH`.
1. No mobile app configure o `A0` para `analogRead`.
1. Exponha o sensor a luz e clique no `A0` para atualizar o valor lido.
1. Agora cubra o sensor, o protegendo da luz, e clique no `A0` para atualizar o valor lido.

TODO !!! vídeo de demonstração.

## [](#webide) Desenvolvendo

Para desenvolver para o Photon podemos usar tanto sua WebIDE quanto uma IDE local que é baseada em Atom. Para os exemplos vamos usar a WebIDE pela facilidade de começar desenvolvendo sem problemas com ela, o fato do Photon receber o flash do programa pela internet permite este uso fácil da WebIDE.

O desenvolvimento é feito igual ao Arduino, na própria IDE vocé terá acesso a várias biblitecas disponíveis para o Photon.

O link para download da IDE local é: [https://www.particle.io/products/development-tools/particle-desktop-ide](https://www.particle.io/products/development-tools/particle-desktop-ide).

### [](#webide) Usando WebIDE

Acesse [https://build.particle.io/](https://build.particle.io/) e faça seu cadastro para começar a usar. Do lado esquedo você verá algumas `Example Apps`, clique em `Blink AN LED` e o código de exemplo de piscar LED irá aparecer na tela.

TODO !!! imagem focada neste pedaçao acima.

Do lado esquerdo clique no símbolo de alvo para adicionar um dispositvo, caso já não tenha adicionado, e adicione seu Photon.

TODO !!! imagem focada neste pedaçao acima.

Clique no raio que aparece no lado esquerdo e o programa irá subir para seu Photon automaticamente, mesmo que ele não esteja na USB (mas esteja ligado e conectado em uma Wifi :) ) e veja o LED piscar. O upload do flash para o Photon pode demorar um pouco.

TODO !!! imagem focada neste pedaçao acima.

TODO !!! vídeo de demonstração.

### [](#particlefunctions) Particle functions

`Particle functions` são funções que podem ser expostas para serem chamadas quando você invoca uma API. Podemos chamar essa API diretamente via HTTP Request, via o console da Particle ou via a própria app mobile. Abaixo vamos demonstrar como ligar o LED embarcado na placa remotamente usando uma `Particle function`.

TODO !!! Código.


TODO !!! vídeo de demonstração.

### [](#particlevariables) Particle variables

`Particle variables` são um jeito fácil de subir o conteúdo de uma variável para a cloud da Particle e depois obter novamente o valor da cloud via uma API.
Vamos usar o mesmo setup do [Leitura Analógica](#tinkerLeituraAnalógica).

```cpp
int photoresistor = A0;

int power = A5;

int analogvalue;

void setup() {

    pinMode(photoresistor,INPUT);
    pinMode(power,OUTPUT);

    digitalWrite(power,HIGH);

    Particle.variable("analogvalue", &analogvalue, INT);
}

void loop() {
    analogvalue = analogRead(photoresistor);
    delay(1000);
}
```

Após subir este código no Photon podemos acessar o console e e obter o dado da variável.

TODO !!! Foto da tela do console

Ou também podemos pegar o dado via uma API rest, mas para isso precisamos obter o token de acesso antes.

Para obter o token de acesso e usar api siga os passos abaixo:

1. Acesse a [WebIDE](https://build.particle.io).
1. Clique em `Settings`, é o último icone no menu do lado esquerdo, uma engrenagem.
1. Você verá o `Access Token`, copie ele e reserve.
1. Para acessar a API via `curl` (caso estejas no Linux/MacOS ou usando o bash do Windows) use o comando: `curl -X GET -H "Authorization: Bearer coleSeuTokenAqui" https://api.particle.io/v1/devices/4c0055000c51353432383931/analogvalue`
1. Caso prefiras fazer um de acesso a API usando o Chrome podemos usar a extensão PostMan, abaixo no vídeo demonstro como fazer o request.

TODO !!! vídeo de demonstração.

### [](#pubsub) Publish/Subscribe

A biblioteca da Particle nos disponibliza funções para fazer broadcast, usando o padrão Publish/Subscribe.
Publicações podem ser públicas, aonde qualquer um que se inscreva pode receber as mensagens, ou podem ser privadas aonde somente você poderá ter acesso.

Abaixo vamos fazer um demonstração simples de publish e suscribe para dar uma ideia de funcionamento.

Para mais detalhes acesse a referencia de desenvolvimento neste link: [https://docs.particle.io/reference/firmware/photon/#particle-publish-](https://docs.particle.io/reference/firmware/photon/#particle-publish-).

TODO !!! Código: receber mensagem para piscar rápido ou devagar. Publicar que alternou de estado fast->slow, ou de slow->fast.

TODO !!! Video de demo


### [](#restoretinker) Resturando o Tinker

Conforme fomos desenvolvendo e escrevendo novos programas na memória do Photon acabamos apagando o Tinker. Mas restaurá-lo é muito simples, vamos fazer novamente o flash do código dele no Photon:

1. Acesse a Web IDE: [https://build.particle.io/](https://build.particle.io/).
1. Do lado esquerdo, na seção `Example Apps` clique na opção `Tinker`.
1. O código do Tinker será aberto, clique no raio do lado esquerdo para fazer o flash no dispositivo.
1. Pronto, o Tinker foi restaurado no seu Photon.

TODO vídeo do restore do Tinker.


### [](#webhooks) Webhooks

A plataforma da Particle permite que `Webhooks` sejam configurados. Webhooks são chamadas a APIs na web que a Particle irá fazer dado algum evento, assim você pode fazer com que em determinadas situações um webservice seja chamado para realizar alguma ação.

Mais detalhes sobre o Webhooks veja o link: [https://docs.particle.io/guide/tools-and-features/webhooks/](https://docs.particle.io/guide/tools-and-features/webhooks/).

Neste outro link [https://docs.particle.io/tutorials/integrations/webhooks/](https://docs.particle.io/tutorials/integrations/webhooks/) temos outros exemplos práticos como o uso do Twilio para envio de SMS.



## [](#docs) Documentação

    - [Referência para desenvolvimento](https://docs.particle.io/reference/firmware/photon/)
    - [Guia inicial do Photon](https://docs.particle.io/guide/getting-started/intro/photon/)
    - [Webhooks](https://docs.particle.io/guide/tools-and-features/webhooks/)
    - [Exemplos Webhooks](https://docs.particle.io/tutorials/integrations/webhooks/)
    - [Photon Datasheet](https://docs.particle.io/datasheets/photon-datasheet/)
