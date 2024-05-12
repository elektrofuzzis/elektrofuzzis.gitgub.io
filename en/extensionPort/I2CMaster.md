---
title: I²C Breakout Boards
Lang:  en
layout: category
classes: wide
sidebar:
    nav: manual-en
---

I2C devices/breakout boards can be connected to the Kelda of your Swarm: 

- [ftSwarm](../../products/ftSwarm), [ftSwarmRS](../../products/ftSwarmRS), [ftSwarmXL](../../products/ftSwarmXL): To do this, connect the GND, SDA(SCL), SDA(SCA) connections to the appropriate pins of your breakout board. You can use the 3.3V supply voltage to supply your breakout board. Make sure that your breakout board works with a 3.3V supply voltage and 3.3V logic level.
- [ftSwarmControl](../../products/ftSwarmControl): This controller can use either 3.3V or 5V breakout boards. Send the SDA3V/SDC3V for breakout boards with 3.3V, SDA5V/SDC5V with 5V breakout boards. The bus addresses 0x3C and 0x68 are already occupied by the OLED display and the optional gyro.

The pins of the extension port are not protected against reverse polarity. Switching errors can damage your ftSwarm controller.
{: .notice--info}

Programming the breakout board is simple. There are usually suitable Arduino libraries for your breakout board that you can use. The only difference is the initialization of the wire library. In the examples of your Arduino library, the I²C bus is initialized with **Wire.begin()**. This is not necessary in your program, as the initialization is already carried out by **ftSwarm.begin()**.

The operating mode for I²C breakout boards is set in the firmware in the **Extension Port** menu. Select the **I2C Master** option under **Mode**.
{: .notice--info}
