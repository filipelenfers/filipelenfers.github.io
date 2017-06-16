---
layout: post
title:  "Particle Variables"
date:   2017-04-18 19:50:00 +0000
comments: true
categories: iot
---


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

Após subir este código no Photon podemos acessar o console e e obter o dado da variável:

1. Acesse a WebIDE.
1. Clique no `Console`, penúltimo ícone do lado esquerdo (um histograma).
1. Clique em `My Devices` No primeiro ícone do lado esquerdo (um cubo).
1. Expanda o seu dispositivo clicando nele.
1. Na lista de variáveis irá aparecer o `analogvalue`, clicando em GET você conseguirá pegar o valor da varíavel atualizado.

Ou também podemos pegar o dado via uma API rest, mas para isso precisamos obter o token de acesso antes.
Para obter o token de acesso e usar api siga os passos abaixo:

1. Acesse a [WebIDE](https://build.particle.io).
1. Clique em `Settings`, é o último icone no menu do lado esquerdo, uma engrenagem.
1. Você verá o `Access Token`, copie ele e reserve.
1. Para acessar a API via `curl` (caso estejas no Linux/MacOS ou usando o bash do Windows) use o comando: `curl -X GET -H "Authorization: Bearer coleSeuTokenAqui" https://api.particle.io/v1/devices/4c0055000c51353432383931/analogvalue`
1. Caso prefiras fazer um de acesso a API usando o Chrome podemos usar a extensão [PostMan](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?utm_source=chrome-app-launcher-info-dialog), abaixo no vídeo demonstro como fazer o request.

TODO !!! vídeo de demonstração. Faltam: desenho do esquema e explicação do da placa (vídeo inicial mostrando a montagem e uma foto do esquema ) e narração.
