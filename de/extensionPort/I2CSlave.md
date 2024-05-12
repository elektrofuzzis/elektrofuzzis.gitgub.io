---
title: I²C TX-/TXT-Kommunikation
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-de
---

Mit diesem Modus kann der Swarm mit einem fischertechnik TX- oder TXT-Controller verbunden werden. Dabei wird der fischertechnik-Controller nicht als Swarm-Member in den Swarm integriert; Ihr normales RoboPro-Programm kann aber über die I²C-Schnittstelle mit dem Swarm Daten austauschen.

Bei dieser Kopplung ist der ftSwarm ein I²C-Bus-Slave-Device und stellt bis zu acht 8-Bit-Register für den Datenaustausch bereit. Der TXT-Controller kann die Register aktiv auslesen oder in sie Werte schreiben. Alle Register können als Schreib- und Leseregister verwendet werden.

Sie legen selbst fest, welche Bedeutung/Funktion ein Register hat. Für die Firmware sind die Register nur ein Block aus 8 Bytes.

Jeder ftSwarm-, ftSwarmRS- oder ftSwarmXL-Controller im Swarm kann die Kommunikation mit dem TXT-Controller übernehmen.

Stellen Sie für diesen Betriebsmodus im **Extension Menu** der Firmware **Mode** auf **I2C Master**.
{: .notice--info}


### Anschluß der Hardware

Die Verbindung der beiden I²C-Schnittstellen ist beim TXT-Controller sehr einfach und kann z.B. mit Jumperkabeln erfolgen:

<div class="centershock"><img src="/assets/img/TXT-ftSwarm.svg" width="33%"></div>

Die Pins des Extension Ports sind nicht gegen Verpolung geschützt. Schaltfehler können sowohl Ihren ftSwarm-Controller als auch den TXT-Controller beschädigen.
{: .notice--info}

Beachten Sie bitte, dass der TX-Controller 5V-Logiklevel verwendet und einen Pegelwandler wie den ftExtender benötigt.
{: .notice--info}


### Daten vom TX-/TXT-Controller an den Swarm senden

Soll der TXT Daten an den Swarm übertragen, so erfolgt dies über das RoboPro-Kommando **I2C Write**:

<div class="centershock"><img src="/assets/img/i2c-write.png" width="400"></div>

In diesem Beispiel schreibt der TXT-Controller in das Register 3 den Wert 42. Die verwendete I²C-Adresse muss die des ftSwarm-Controllers sein. 0x66 ist die Defaultadresse des Controllers.

Der Wert wird im Swarm auf die Kelda übertragen und kann dort mit der Funktion ```getRegister``` ausgelesen werden:

```cpp
FtSwarmI2C *i2c = new FtSwarmI2C( "I2C Alias");
printf( "Read I2C-Register #3: %d\n", i2c->getRegister(3);
```

Bitte beachten Sie, dass die Registeränderungen durch den TXT im Swarm "nur" alle 25ms übertragen werden. Schreibt der TXT innerhalb von 25 ms unterschiedliche Werte in ein Register, so kann die Kelda nur den letzten Wert verarbeiten.

Die I²C-Adresse des ftSwarm-Controllers wird im **Extension Port Menu** mit der Option **I2C Slave Address** eingestellt. Die Anzahl der verfügbaren Register wird im gleichen Menü über die Option **I2C Registers** eingestellt.
{: .notice--info}


### Daten vom Swarm an den TX-/TXT-Controller senden

Das Senden von Daten vom Swarm an den TXT-Controller erfolgt über die Funktion ```setRegister```. In diesem Beispiel wird der Wert 42 in Register 0 gesetzt.

```cpp
FtSwarmI2C *i2c = new FtSwarmI2C( "I2C Alias");
i2c->setRegister(0, 42);
```

Mit dem RoboPro-Kommando "I2C Read" liest der TXT-Controller das Register aus:

<div class="centershock"><img src="/assets/img/i2c-read.png" width="400"></div>

RoboPro muss immer alle zur Verfügung stehenden Register auslesen. Das Beispiel funktioniert so nur, wenn die Anzahl der I²C-Register in der Firmware auf 1 gesetzt wurde. Sollen z.B. 4 Register verwendet werden, so müssen in Robo-Pro immer alle 4 Register gelesen werden:

<div class="centershock"><img src="/assets/img/i2c-multiple-read.png" width="250"></div>

Die ersten drei Lese-Kommandos benötigen die Option "offen lassen", beim vierten Kommando wird diese Option nicht gesetzt.


### Interruptmodus

Für den TXT ist es häufig nur interessant die I²C-Register auszulesen, wenn diese auch verändert wurden. Dazu kann ein Pin eines Motorausgangs  mit einem Eingang des TXT verbunden werden. Schreibt der Swarm in das Register, wird der Motorausgang aktiviert. Der TXT sieht die Flanke und liest dann die Register aus. Mit dem Auslesen der Register wird der Motorausgang wieder deaktiviert.

<div class="centershock"><img src="/assets/img/i2c-multiple-read-interrupt.png" width="250"></div>

In diesem Code-Beispiel werdenm die Register werden nur ausgelesen, wenn am  Eingang I1 einen Flankenwechsel stattfindet.

Der Motorausgang muss auf dem gleichen Swarm-Member liegen, auf dem auch die I²C-Verbindung geschaltet wurde. Es wird nur einer der beiden Anschlüsse am Motorausgang verbunden:

<div class="centershock"><img src="/assets/img/TXT-ftSwarm-Int.svg" width="33%"></div>

In der Firmware des ftSwarm-Controllers wird die Option **Interrupt Line** auf den entsprechenden Motorausgang gesetzt. 

Mit den beiden Menüpunkten **Interrupt Low Value** und **Interrupt High Value** können die Speed-Werte für den Motorausgang eingestellt werden. In der Regel sind dies -255 für **Low** und 255 für **High**. Je nachdem, welcher Anschluß am Motorausgang verwendet wurde, müssen Sie die beiden Werte evtl. vertauschen.

