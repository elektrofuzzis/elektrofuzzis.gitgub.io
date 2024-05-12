---
title: Tutorial
Lang:  en
classes: wide
layout: category
sidebar:
    nav: manual-en
---

This manual explains the basic use and programming of the ftSwarm controller. We therefore recommend that you first read the manual chapter by chapter and reproduce the examples. The [API reference](../cpp-api/index) explains the various classes in detail as well as the connection diagram for the various sensors and actuators.

1. Getting started
- [Learn about the connectors of the ftSwarm family.](../pinout)
- [Connect your ftSwarm controller with your PC](../serial)
- [Configure wifi and use the status page](../WebUI)
- [Install IDE to run the examples](../ide)


2. Programming in C++
- [Run your first program on a singular controller](../MotorSwitch)
- [Understand the kelda principle to run a swarm](../kelda)
- [The first swarm](../MotorSwitchSwarm)
- [Use alias names to structure your code](../MotorSwitchAlias)
- [How to use buttons, switches and toggles](../switches)
- [Remote control without a line of code](../RemoteControl)
- [Use events to simplfy your code](../EventControlled)
- [RGB LEDs & ftPixel](../FtSwarmPixel)
- [OLED Display](../FtSwarmOLED)

3. Firmware & Versions
- [Firmware & Updates](../firmware)
- [Versions](../versions)

4. Advanced
- [The complete configuration](../Configuration)
- [Using PlatformIO & VSCode](../PlatformIO)
- [Connect your swarm using RS485](../rs485)
- [Debug your code](../debugging)

The tutorial is not intended to explain everything in detail. If you like to have a deep dive into ftSwarm's commands & features please checkout the [API](../cpp-api/index.md) documentation.

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
