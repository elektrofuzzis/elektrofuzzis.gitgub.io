---
title: The ftSwarm Project
layout: category
classes: wide
Lang: en
sidebar:
    nav: sitebar-en
---

The goal of the ftSwarm project is to build small networked controllers for DIY and toy applications. 
Since they are networked with each other, they can act like a swarm. For example, they can act as several independent robots to solve a task together. 

In larger models, the controllers can be installed at different positions close to actuators and sensors - together they control the complete model.

Originally, the project was designed to use with *fischertechnik*. Since the mounting grooves are compatible with Makerbeam profiles, ftSwarms could be used in many DIY projects. 

<style>
td, th {
    border: none!important;
}
</style>

<table>
    <tr>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmRS.png" width="200"></td>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmXL.png" width="250"></td>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmCAM.png" width="150"></td>
    </tr>
    <tr>
        <td style="text-align: center; font-weight: bold;">ftSwarmRS</td>
        <td style="text-align: center; font-weight: bold;">ftSwarmXL</td>
        <td style="text-align: center; font-weight: bold;">ftSwarmCAM</td>
    </tr>
    <tr>
        <td style="vertical-align: top; text-align: justify;">
            Although the ftSwarmRS (pictured right) is almost as small as a matchbox at just 45.0 x 37.5 x 23.0 mm, it can control two 9V DC motors, up to sixteen RGB LEDs, two servos and read out six analog or digital sensors.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            The ftSwarmXL is designed for the really big projects. With its 8 inputs for analog and digital sensors and 8 outputs for 9V DC motors, it has an extremely high port density in a housing measuring just 75 x 45 x 14 mm.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            The ftSwarmCAM can be used to transmit images and videos from the model. It also controls two motors, a servo and has three digital inputs. Two directly connectable LiPo batteries mobilizes the controller.
        </td>
    </tr>
    <tr>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmControl.png" width="200"></td>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmPwrDrive.png" width="200"></td>
        <td style="text-align: center;"><img src="/assets/img/ftSwarmDuino.png" width="200"></td>
    </tr>
    <tr>
        <td style="text-align: center; font-weight: bold;">ftSwarmControl</td>
        <td style="text-align: center; font-weight: bold;">ftSwarmPwrDrive</td>
        <td style="text-align: center; font-weight: bold;">ftSwarmDuino</td>
    </tr>
    <tr>
        <td style="vertical-align: top; text-align: justify;">
            In addition to two joysticks, eight buttons and an LCD display, the ftSwarmControl control panel can control two DC motors and read out four digital sensors. In remote control mode, simple models can be simple models can be controlled without any line of code.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            With the ftSwarmPwrDrive, stepper motors can be integrated into the Swarm. The controller is plugged onto an ftPwrDrive controller and thus integrates the four stepper motors and five limit switches of the ftPwrDrive into the Swarm.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            Upcycling for the ftDuino. The ftSwarmDuino is plugged into the I²C connector of the ftDuino controller and the eight inputs and four outputs of the ftDuino controller can be used in the Swarm.
        </td>
    </tr>
</table>

Since building this hardware on your own is a little bit tricky, we offer ready to use devices at [gundermann-software.de](https://gundermann-software.de/).
For all who wants to build their own pcb, we provide the needed schematic files at github as well.

