---
title: I²C Breakout Boards
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-de
---

An der Kelda Ihres Swarm können I2C-Bausteine/Breakoutboards angeschlossen werden: 

- [ftSwarm](../../products/ftSwarm), [ftSwarmRS](../../products/ftSwarmRS), [ftSwarmXL](../../products/ftSwarmXL): Verbinden Sie dazu die Anschlüsse GND, SDA(SCL), SDA(SCA) mit den passenden Pins Ihres Breakoutboards. Die 3.3V-Versorgungsspannung können Sie für die Versorgung Ihres Breakoutboards verwenden. Achten Sie darauf, dass Ihr Breakoutboard mit einer 3.3V Versorgungsspannung und 3.3V Logiklevel arbeitet.
- [ftSwarmControl](../../products/ftSwarmControl): Dieser Controller kann wahlweise 3.3V- und 5V-Breakoutboards verwenden. Versenden Sie die SDA3V/SDC3V für Breakoutboards mit 3.3V, SDA5V/SDC5V mit 5V-Breakoutboards. Die Busadressen 0x3C und 0x68 sind bereits durch das OLED-Display unf den optionalen Gyro belegt.

Die Pins des Extension Ports sind nicht gegen Verpolung geschützt. Schaltfehler können Ihren ftSwarm-Controller beschädigen.
{: .notice--info}

Die Programmierung des Breakoutboards ist einfach. In der Regel gibt es passende Arduino-Bibliotheken für Ihr Breakoutboard die Sie verwenden können. Der einzige Unterschied ist die Initialisierung der Wire-Bibliothek. In den Beispielen Ihrer Arduino-Bibliothek wird mit **Wire.begin()** der I²C-Bus initialisiert. Dies ist in Ihrem Programm nicht notwendig, da die Intialisierung bereits  durch **ftSwarm.begin()** durchgeführt wird.

Der Betriebsmodus für I²C-Breakoutboards wird in der Firmware im Menu **Extension Port** eingestellt. Wählen Sie bei **Mode** die Option **I2C Master** aus.
{: .notice--info}