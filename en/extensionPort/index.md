---
title: Extension Port
Lang:  en
layout: category
classes: wide
sidebar:
    nav: manual-en
---

The ftSwarm, ftSwarmRS, ftSwarmXL and ftSwarmControl controllers have an extension port. The port can be used to connect I²C-based devices or provide additional motor outputs. The following functions are available:

- In [I2C Master Mode](../I2CMaster), I²C modules or I²C breakout boards can be connected to the extension port of the Kelda. For example, additional displays or sensors can be connected to the Swarm.
- In [I2C Slave Mode](../I2CSlave), data can be exchanged with a TX or TXT controller or another Swarm via the port.
- With [MPU-6050 Mode](../gyro), an optional MPU-6050 gyro can be read out in the Swarm.
- [Output Mode](../outputs), the two GPIOs SDA and SCL of the extension port can be used as PWM signals, e.g. to provide additional motor outputs.

The operating mode of the port is set in the firmware in the **Extension Port Menu**. 

The connections on the individual controller types have small differences:

- [ftSwarm](../../products/ftSwarm): The ftSwarm has an 8-pin header and uses 3.3V logic level.
- [ftSwarmRS](../../products/ftSwarmRS) & [ftSwarmXL](../products/ftSwarmXL): Both controllers have a 4-pin pin header and use 3.3V logic level.
- [ftSwarmControl](../../products/ftSwarmControl): The ftSwarmControl has a 14-pin connector strip on the left-hand side of the housing. This connector strip provides the IOs both as 3.3V and 5V logic levels. The extension port of the ftSwarmControl can only be used in I²C master mode.

Note: The IOs can be loaded with a maximum of 8mA. The power supplies with max. 100mA. The IOs and power supplies are not protected against reverse polarity.
{: .notice--info}
