---
title: Extension Port
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-de
---

Die Controller ftSwarm, ftSwarmRS, ftSwarmXL und ftSwarmControl verfügen über einen Extension Port. Über den Port können I²C-basierte Geräte angeschlossen oder zusätzliche Motorausgänge zur Verfügung gestellt werden. Es stehen die folgenden Funktionen zur Verfügung:

- Im [I2C Master Mode](../I2CMaster) können am Extension Port der Kelda I²C-Bausteine oder I²C-Breakoutboards angeschlossen werden. So können z.B. zusätzliche Displays oder Sensoren an den Swarm angeschlossen werden.
- Im [I2C Slave Mode](../I2CSlave) können über den Port Daten mit einem TX-, TXT-Controller oder einem anderen Swarm ausgetauscht werden.
- Mit dem [MPU-6050 Mode](../gyro) kann im Swarm ein optionaler MPU-6050-Gyro ausgelesen werden.
- [Output Mode](../outputs) können die beiden GPIOs SDA und SCL des Extension Ports als PWM-Signale verwendet, um z.B. zusätzliche Motorausgänge bereitzustellen.

Der Betriebsmodus des Ports wird in der Firmware im **Extension Port Menu** eingestellt. 

Die Anschlüsse an den einzelnen Controllertypen haben kleine Unterschiede:

- [ftSwarm](../../products/ftSwarm): Der ftSwarm hat eine 8-polige Stiftleiste und verwendet 3.3V Logiklevel.
- [ftSwarmRS](../../products/ftSwarmRS) & [ftSwarmXL](../products/ftSwarmXL): Die beiden Controller haben eine 4-polige Stiftleiste und verwendeen 3.3V Logiklevel.
- [ftSwarmControl](../../products/ftSwarmControl): Der ftSwarmControl hat eine 14-poligen Steckerleiste an der linken Seite des Gehäuses. Diese Steckerleiste stellt die IOs sowohl als 3.3V- sowie als 5V-Logiklevel zur Verfügung. Der Extension Port des ftSwarmControl kann nur im I²C-Master-Modus verwendet werden.

Hinweis: Die IOs können mit maximal 8mA belastet werden. Die Stromversorgungen mit max. 100mA. Die IOs und Stromversorgungen sind nicht gegen Verpolung geschützt.
{: .notice--info}
