---
title: Das ftSwarm Projekt
Lang: de
layout: category
classes: wide
sidebar:
    nav: sitebar-de
---

Ziel des ftSwarm-Projekts ist es, kleine vernetzte Steuerungen für DIY- und Spielzeugmodelle zu bauen. Da sie miteinander vernetzt sind, können sie als Schwarm zusammenarbeiten. 

So können mehrere unabhänge Roboter gemeinsam eine Aufgabe lösen. Bei größeren Modellen können die Steuerungen an verschiedenen Positionen im Modell, jeweils in der Nähe der Aktoren und Sensoren verbaut werden - zusammen steuern sie dann das gesamte Modell.

Ursprünglich enstand das Projekt als möglichst kleine *fischertechnik*-Controller. Da die Montagenuten am Controller jedoch mit Makerbeam-Profilen kompatibel sind, können ftSwarms in vielen DIY-Projekten verwendet werden.

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
            Obwohl der ftSwarmRS (rechts im Bild) mit nur 45,0 x 37,5 x 23.0 mm fast so klein wie eine Streichholzschachtel ist, kann er zwei 9V-DC-Motoren, bis zu sechzehn RGB-LEDs, zwei Servos ansteuern und sechs analoge oder digitale Sensoren auslesen.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            Der ftSwarmXL ist für die ganz großen Projekte gedacht. Mit seinen 8 Eingängen für analoge und digitale Sensoren sowie den 8 Ausgängen für 9V-DC-Motoren hat er eine extrem hohe Portdichte in einem nur 75,0 x 45,0 x 14 mm großen Gehäuse. 
        </td>
        <td style="vertical-align: top; text-align: justify;">
            Mit dem ftSwarmCAM können Bilder und Videos aus dem Modell übertragen werden. Nebenbei steuert er noch zwei Motoren, einen Servo und hat drei digitale Eingänge. Zwei direkt anschließbare LiPo-Akkus machen den Controller mobil.
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
            Als Bedienfeld verfügt der ftSwarmControl neben zwei Joysticks, acht Tasten und einem LCD-Display über die Möglichkeit zwei DC-Motoren zu steuern und vier digitale Sensoren auszulesen. Im Fernbedienungsmodus können
            einfache Modelle ohne Programmierung gesteuert werden. 
        </td>
        <td style="vertical-align: top; text-align: justify;">
            Mit dem ftSwarmPwrDrive lassen sich Schrittmotoren im Swarm integrieren. Der Controller wird auf einen 
            ftPwrDrive-Controller aufgesteckt und integriert so die vier Schrittmotoren und fünf Endschalter des ftPwrDrive
            in den Swarm.
        </td>
        <td style="vertical-align: top; text-align: justify;">
            Upcycling für den ftDuino. Der ftSwarmDuino wird auf den I²C-Stecker des ftDuino-Controllers gesteckt und schon
            lassen sich die acht Eingänge und vier Ausgänge des ftDuino-Controllers im Swarm nutzen.
        </td>
    </tr>
</table>

Aufgrund der geringen Größe ist es schwierig die Hardware nachzubauen. Deshalb bieten wir fertige Geräte unter [gundermann-software.de](https://gundermann-software.de/) an. Für alle die ihre eigene Platine herstellen wollen, stehen die benötigten Schaltplan-Dateien auch auf github zur Verfügung.

