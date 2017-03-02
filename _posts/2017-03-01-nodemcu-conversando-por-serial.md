---
layout: post
title:  "Conectando dois nodemcu por SoftwareSerial"
date:   2017-03-01 19:50:00 +0000
categories: iot
---

Vamos conectar duas placas NodeMCU para trocar informações via comunicação
serial, de uma forma bem simples, aonde uam vai enviar um bite para outra e
esta avisar que recebeu o byte através do Serial Monitor do Arduino IDE.

# [](#com-serial)Comunicação Serial?

[Comunicação serial][com-serial] é o processo de mandar 1 bit de cada vez,
sequencialmente, através de um barramento. A comunicação serial ocorre ligando
os pinos TX/RX da placa a outra placa ou dispositivo.

O objeto `Serial` que comumente usamos no Arduino IDE aponta por padrão para o [UART0][uart] (serial via hardware) que está mapeado para os pinos  GPIO1 (TX) e GPIO3 (RX), ele pode ser remapeado para os pinos GPIO15(TX, pino D8) e GPIO13 (RX, pino D7) chamando o comando `Serial.swap()`. Não se pode usar dois seriais via hardware ao mesmo tempo, temos que fazer o swap entre eles. Mais detalhes sobre o `Serial` no NodeMCU(ESP8266) no link [https://github.com/esp8266/Arduino/blob/master/doc/reference.md#serial][esp-serial] .

Entretanto temos a opção de usar a bilioteca SoftwareSerial (https://www.arduino.cc/en/Reference/softwareSerial) que permite usarmos outros pinos digitais para comunicação serial independente do `Serial` via hardware.



# [](#materiais)Materiais

*   2 x NodeMCU
*   Conectores
*   Cabo USB para gravar o progama

# [](#header-1)Ligando os fios

> A ligação dos pinos TX/RX deve ser invertida entre as placas:
> TX da placa A liga no RX da placa B.
> RX da placa A liga no TX da placa B.

TODO Figura do esquema
TODO Foto do esquema

# [](#header-1) Código

## [](#header-1) Transmissor

TODO Código do transmissor

## [](#header-1) Receptor
TODO Código do receptor


# [](#header-1) Teste

TODO descrição do Teste
TODO Fotos do Teste
TODO Vídeo do teste


Porte da SoftwareSerial para ESP8266
https://github.com/plerup/espsoftwareserial


[com-serial]: https://en.wikipedia.org/wiki/Serial_communication
[uart]: https://en.wikipedia.org/wiki/Universal_asynchronous_receiver/transmitter
[esp-serial]: https://github.com/esp8266/Arduino/blob/master/doc/reference.md#serial
