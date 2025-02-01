---
title: Tutorial
Lang:  en
classes: wide
layout: category
sidebar:
    nav: manual-en
---

This manual explains the basic use and programming of the ftSwarm controller. We therefore recommend that you first read the manual chapter by chapter and reproduce the examples. The [API reference](../../cpp-api/index) explains the various classes in detail as well as the connection diagram for the various sensors and actuators.

1. Getting started
- [Learn about the connectors of the ftSwarm family.](../pinout)
- [Connect your ftSwarm controller with your PC](../serial)
- [Configure wifi and use the status page](../WebUI)
- [Install IDE to run the examples](../ide)


2. Programming in C++
- [Run your first program on a singular controller](../../programming/MotorSwitch)
- [Understand the kelda principle to run a swarm](../../programming/kelda)
- [The first swarm](../../programming/MotorSwitchSwarm)
- [Use alias names to structure your code](../../programming/MotorSwitchAlias)
- [How to use buttons, switches and toggles](../../programming/switches)
- [Remote control without a line of code](../../programming/RemoteControl)
- [Use events to simplfy your code](../../programming/EventControlled)
- [RGB LEDs & ftPixel](../../programming/tSwarmPixel)
- [OLED Display](../../programming/FtSwarmOLED)

3. [Connect your Swarm using RS485](../../rs485/rs485)

4. Extension Port
- [Overview](../../extensionPort/index)
- [I²C Breakout Boards](../../extensionPort/I2CMaster)
- [I²C TX-/TXT-Communication](../../extensionPort/I2CSlave)
- [Gyro](../../extensionPort/gyro)
- [Motor Outputs](../../extensionPort/outputs)

5. Firmware & Versions
- [The complete configuration](../../firmware/Configuration)
- [Firmware & Updates](../../firmware/firmware)
- [Versions](../../firmware/versions)

4. Advanced
- [Using PlatformIO & VSCode](../../advanced/PlatformIO)
- [Debug your code](../../advanced/debugging)


### Intended Use & Warranty

The ftSwarm project to build small networked controllers for DIY and toy applications. 
This project gives you the needed hard- and software. But it's your project and you need to take care of your project.

- Hobbyist projects need to be supervised all time.
- Don't build robotics, which could harm humans, pets or anything else.
- This project is not intended to build professional robotics.
- You need to test the provided hard- and software on your own, to assure the needed functionality and stability of your hobbyist project.

Our hard- and software is engineered as a hobbyist project. So it has built-in errors and limitations.
Therefore we exclude any warranty on the hardware and software presented here.
{: .notice--info}
