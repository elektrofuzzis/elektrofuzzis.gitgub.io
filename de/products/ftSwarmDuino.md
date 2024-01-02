---
title: ftSwarmDuino
layout: category
lang: de
classes: wide
sidebar:
    nav: products-de
---

Mit diesen beiden Controllern können Sie Ihre vorhandenen ftPwrDrive- oder ftDuinos-Controller in den Swarm integrieren. 

Dabei wird der eigentliche ftSwarmPwrdrive- bzw. ftSwarmDuino-Controller auf die I²C-Schnittstelle des ftPwrDrive bzw. des ftDuinos aufgesteckt und extern mit 9V versorgt. 

|---------------|------|------|
| | **ftSwarmDuino** |
| **Pinout**    | <img alt="ftSwarm Pinout" src="/assets/img/ftSwarmDuinoPinout.png" width="250"> |
| **CPU**             | esp32-S3 |
| **Speicher**        | 2 MB RAM, 4MB Flash |
| **Anschlüsse**      | Schraubklemmen (ftSwarmDuino)<br>4mm Bananenbuchsen (über ftDuino-Controller) |
| **Motor Ausgänge**  | 4 x DC Motoren oder Lampen (über ftDuino-Controller) |
| **Sensor Eingänge** | 8 x analoge oder digitale Sensoren (über ftDuino-Controller) |
| **RGB LEDs**        | 2 onboard LEDs|
| **I²C Interface**   | 5V Interface für die Kommunikation zwischen ftSwarmDuino und ftDuino|
| **Kommunikation**   | wifi oder RS485 |
| **USB Anschluß**    | USB-C |

Der Aufsteck-Controller benötigt eine externe 9V Stromversorgung. Wird nur die USB-Buchse verwendet, so können nur die Firmware oder Programme geflashed werden; die Kommunikation it dem ftPwrDrive bzw. ftDuino funktioniert dann nicht.

Um Schäden an der Hardware zu vermeiden, trennen Sie an den verwendeten Controller vor dem Zusammenstecken Stromversorgung und USB-Anschluss. Stecken Sie die Controller vorsichtig und in der abgebildeten Orientierung.   