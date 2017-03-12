---
layout: post
title:  "Conectando dois nodemcu por SoftwareSerial"
date:   2017-03-01 19:50:00 +0000
categories: iot
---

Vamos conectar duas placas NodeMCU para trocar informações via comunicação
serial, de uma forma bem simples, aonde uam vai enviar um bite para outra e
esta avisar que recebeu o byte através do Serial Monitor do Arduino IDE.

## [](#com-serial)Comunicação Serial?

[Comunicação serial][com-serial] é o processo de mandar 1 bit de cada vez,
sequencialmente, através de um barramento. A comunicação serial ocorre ligando
os pinos RX/TX da placa a outra placa ou dispositivo.

> O nome RX vem de Receive, e o nome TX vem de Transmit. Ou seja o receptor e o transmissor.

O objeto `Serial` que comumente usamos no Arduino IDE aponta por padrão para o [UART0][uart] (serial via hardware) que está mapeado para os pinos  GPIO1 (TX) e GPIO3 (RX), ele pode ser remapeado para os pinos GPIO15(TX, pino D8) e GPIO13 (RX, pino D7) chamando o comando `Serial.swap()`. Não se pode usar dois seriais via hardware ao mesmo tempo, temos que fazer o swap entre eles. Por isso resolvi usar a biblioteca SoftwareSerial para usar 2 pinos para comunicação serial enquando deixar o `Serial` disponível para enviar os logs para o serial monitor do Arduino IDE.

Mais detalhes sobre o `Serial` no NodeMCU(ESP8266) no link [https://github.com/esp8266/Arduino/blob/master/doc/reference.md#serial][esp-serial] .

Entretanto temos a opção de usar a bilioteca SoftwareSerial (https://www.arduino.cc/en/Reference/softwareSerial) que permite usarmos outros pinos digitais para comunicação serial independente do `Serial` via hardware.



## [](#materiais)Materiais

*   2 x NodeMCU
*   Conectores
*   Cabo USB para gravar o progama

## [](#fios)Ligando os fios

> A ligação dos pinos TX/RX deve ser invertida entre as placas:
> TX da placa A liga no RX da placa B.
> RX da placa A liga no TX da placa B.

![Conexão dos fios]({{ site.github.url }}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/NodeMcuSerialIntro_bb.png)

Você pode puxar o projeto no fritzing por este link: [http://fritzing.org/projects/serial-conection-between-2-nodemcus][fritzing-link].

[![Foto conexão dos fios]({{ site.github.url }}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_schema.JPG)][photo_schema3compact_link]

[![Foto Node A - Transmitter]({{ site.github.url }}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_nodeA.JPG)][photo_nodeA]

[![Foto Node B - Receiver]({{ site.github.url }}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_nodeB.JPG)][photo_nodeB]

## [](#codigo) Código

Nos códigos abaixo um NodeMCU vai ser comportar somente como transmissor e
outro somente como receptor, entretando a conexão que fizemos é um caminho de
duas vias: ambos poderiam transmitir e receber dados um para o outro. Para
mantermos o teste simples, somente um irá transmitir e o outro receber.

Código dos dois projetos:

* [Projeto transmissor][project_transmitter]
* [Projeto receptor][project_receiver]

### [](#transmissor) Transmissor

O código abaixo envia a cada um segundo um número (char) entre 65 e 90, que são as letras maiúsculas na [tabela ASCII](https://www.arduino.cc/en/Reference/ASCIIchart).

```cpp
#include <SoftwareSerial.h>

#define D7 13
#define D8 15

SoftwareSerial mySerial(D7, D8); // RX = D7, TX  = D8


void setup() {
  Serial.begin(9600); //Start Serial
  mySerial.begin(9600); //Start mySerial
  pinMode(D7,INPUT); //d7 is RX, receiver, so define it as input
  pinMode(D8,OUTPUT); //d8 is TX, transmitter, so define it as output
} // end of setup


void loop() {

  char letter = random(65,91); //Numbers between 65 and 90, that are the upper case letters in ASCII table (https://www.arduino.cc/en/Reference/ASCIIchart).

  mySerial.write(letter); // write the byte to the serial so other NodeMCU can receive it.

  Serial.print("LETRA ");Serial.print(letter); Serial.println(" ENVIADA"); // Write on serial monitor which letter was sent.

  delay(1000); // Wait for a sec.

} // end of loop
```

Poderia ser usado o método print/println também, a documentação do método está aqui: [https://www.arduino.cc/en/Reference/SoftwareSerialPrint](https://www.arduino.cc/en/Reference/SoftwareSerialPrint).

### [](#reeptor) Receptor

O código do receptor tem um passo a mais que é checar se existem bytes a serem
lidos. Para isso fazemos o teste `mySerial.available() > 0`, ou seja se existem
mais de 0 bytes a sereml idos.

```cpp
#include <SoftwareSerial.h>

#define D7 13
#define D8 15

SoftwareSerial mySerial(D7, D8); // RX = D7, TX  = D8


void setup() {
  Serial.begin(9600); //Start Serial
  mySerial.begin(9600); //Start mySerial
  pinMode(D7,INPUT); //d7 is RX, receiver, so define it as input
  pinMode(D8,OUTPUT); //d8 is TX, transmitter, so define it as output
} // end of setup

void loop() {
  char receivedLetter = '?'; // if empty show question mark

  if (mySerial.available() > 0) { //Check if serial is avaliable, if this check is not done you will read 'ÿ'
    receivedLetter = mySerial.read(); //read the char received. This function returns -1 if there is nothing to read.
    Serial.print("LETRA ");Serial.print(receivedLetter); Serial.println(" RECEBIDA"); // Write on serial monitor which letter was received.
  }

} //end of loop
```



## [](#teste) Teste

TODO descrição do Teste
TODO Fotos do Teste
TODO Vídeo do teste


## [](#observacoes) Observações

TODO O software serial só deixa ler uma comunicação serial por vez, deve-se usar o método listen para alternar entre eles. https://www.arduino.cc/en/Reference/SoftwareSerialListen


## [](#aprofundando) Aprofundando

TODO este foi um tutorial básico e prático, este link possui informações mais detalhadas para aprofuncamento: https://learn.sparkfun.com/tutorials/serial-communication



Porte da SoftwareSerial para ESP8266
https://github.com/plerup/espsoftwareserial


[com-serial]: https://en.wikipedia.org/wiki/Serial_communication
[uart]: https://en.wikipedia.org/wiki/Universal_asynchronous_receiver/transmitter
[esp-serial]: https://github.com/esp8266/Arduino/blob/master/doc/reference.md#serial
[fritzing-link]:http://fritzing.org/projects/serial-conection-between-2-nodemcus
[photo_schema3compact_link]:{{site.github.url}}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_schema.JPG
[photo_nodeA]:{{site.github.url}}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_nodeA.JPG
[photo_nodeB]:{{site.github.url}}/assets/images/post/2017-03-01-nodemcu-conversando-por-serial/photo_nodeB.JPG
[project_transmitter]:{{site.github.url}}/assets/code/post/2017-03-01-nodemcu-conversando-por-serial/NodeAtransmitter.zip
[project_receiver]:{{site.github.url}}/assets/code/post/2017-03-01-nodemcu-conversando-por-serial/NodeBreceiver.zip
