---
title: I²C TX-/TXT-Communication
Lang:  en
layout: category
classes: wide
sidebar:
    nav: manual-en
---

This mode can be used to connect the Swarm to a fischertechnik TX or TXT controller. The fischertechnik controller is not integrated into the Swarm as a Swarm member; however, your normal RoboPro program can exchange data with the Swarm via the I²C interface.

With this coupling, the ftSwarm is an I²C bus slave device and provides up to eight 8-bit registers for data exchange. The TXT controller can actively read the registers or write values to them. All registers can be used as read and write registers.

You determine the meaning/function of a register yourself. For the firmware, the registers are just a block of 8 bytes.

Each ftSwarm, ftSwarmRS or ftSwarmXL controller in the Swarm can take over communication with the TXT controller.

For this operating mode, set **Mode** to **I2C Master** in the **Extension Menu** of the firmware.
{: .notice--info}


### Connecting the hardware

Connecting the two I²C interfaces on the TXT controller is very simple and can be done using jumper cables, for example:

<div class="centershock"><img src="/assets/img/TXT-ftSwarm.svg" width="33%"></div>

The pins of the extension port are not protected against reverse polarity. Switching errors can damage both your ftSwarm controller and the TXT controller.
{: .notice--info}

Please note that the TX controller uses 5V logic levels and requires a level converter such as the ftExtender.
{: .notice--info}


### Send data from the TX/TXT controller to the Swarm

If the TXT is to transfer data to the Swarm, this is done via the RoboPro command **I2C Write**:

<div class="centershock"><img src="/assets/img/i2c-write.png" width="400"></div>

In this example, the TXT controller writes the value 42 to register 3. The I²C address used must be that of the ftSwarm controller. 0x66 is the default address of the controller.

The value is transferred to the Kelda in the Swarm and can be read out there using the ```getRegister``` function:

```cpp
FtSwarmI2C *i2c = new FtSwarmI2C( "I2C Alias");
printf( "Read I2C-Register #3: %d\n", i2c->getRegister(3);
```

Please note that the register changes are “only” transmitted by the TXT in the swarm every 25 ms. If the TXT writes different values to a register within 25 ms, the Kelda can only process the last value.

The I²C address of the ftSwarm controller is set in the **Extension Port Menu** with the **I2C Slave Address** option. The number of available registers is set in the same menu using the **I2C Registers** option.
{: .notice--info}


### Send data from the Swarm to the TX/TXT controller

Data is sent from the Swarm to the TXT controller using the ```setRegister``` function. In this example, the value 42 is set in register 0.

```cpp
FtSwarmI2C *i2c = new FtSwarmI2C( "I2C Alias");
i2c->setRegister(0, 42);
```

The TXT controller reads the register using the RoboPro command “I2C Read”:

<div class="centershock"><img src="/assets/img/i2c-read.png" width="400"></div>

RoboPro must always read out all available registers. The example only works if the number of I²C registers has been set to 1 in the firmware. If, for example, 4 registers are to be used, all 4 registers must always be read in Robo-Pro:

<div class="centershock"><img src="/assets/img/i2c-multiple-read.png" width="250"></div>

The first three read commands require the “leave open” option; this option is not set for the fourth command.


### Interrupt mode

For the TXT, it is often only interesting to read out the I²C registers if they have also been changed. For this purpose, a pin of a motor output can be connected to an input of the TXT. If the Swarm writes to the register, the motor output is activated. The TXT sees the edge and then reads the registers. When the registers are read, the motor output is deactivated again.

<div class="centershock"><img src="/assets/img/i2c-multiple-read-interrupt.png" width="250"></div>

In this code example, the registers are only read out if there is an edge change at input I1.

The motor output must be on the same swarm member on which the I²C connection was switched. Only one of the two connections at the motor output is connected:

<div class="centershock"><img src="/assets/img/TXT-ftSwarm-Int.svg" width="33%"></div>

In the firmware of the ftSwarm controller, the **Interrupt Line** option is set to the corresponding motor output. 

The two menu items **Interrupt Low Value** and **Interrupt High Value** can be used to set the speed values for the motor output. As a rule, these are -255 for **Low** and 255 for **High**. Depending on which connection was used at the motor output, you may have to swap the two values.
