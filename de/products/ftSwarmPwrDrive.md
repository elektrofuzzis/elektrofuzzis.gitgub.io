---
title: ftSwarmPwrDrive
layout: category
lang: de
classes: wide
sidebar:
    nav: products-de
---

Mit diesen beiden Controllern können Sie Ihre vorhandenen ftPwrDrive- oder ftDuinos-Controller in den Swarm integrieren. 

Dabei wird der eigentliche ftSwarmPwrdrive- bzw. ftSwarmDuino-Controller auf die I²C-Schnittstelle des ftPwrDrive bzw. des ftDuinos aufgesteckt und extern mit 9V versorgt. 

|---------------|------|------|
| | **ftSwarmPwrDrive** |
| **Pinout**    | <img alt="ftSwarm Pinout" src="/assets/img/ftSwarmPwrDrivePinout.svg" width="50%"> |
| **CPU**             | esp32-S3                                          | 
| **Speicher**        | 2 MB RAM, 4MB Flash                               | 
| **Anschlüsse**      | Schraubklemmen (ftSwarmPwrDrive)<br>4mm Bananenbuchsen (über ftPwrDrive-Controller) |
| **Motor Ausgänge**  | 4 x Schrittmotoren (über ftPwrDrive-Controller)  |
| **Sensor Eingänge** | 4 x digitale Endschalter, 1 x Notaus (über ftPwrDrive-Controller) |
| **RGB LEDs**        | 2 onboard LEDs                                    |
| **I²C Interface**   | 5V Interface für die Kommunikation zwischen ftSwarmPwrDrive und ftPwrDrive   | 
| **Kommunikation**   | wifi oder RS485                                   |
| **USB Anschluß**    | USB-C                                             | 

Der Aufsteck-Controller benötigt eine externe 9V Stromversorgung. Wird nur die USB-Buchse verwendet, so können nur die Firmware oder Programme geflashed werden; die Kommunikation it dem ftPwrDrive bzw. ftDuino funktioniert dann nicht.

Um Schäden an der Hardware zu vermeiden, trennen Sie an den verwendeten Controller vor dem Zusammenstecken Stromversorgung und USB-Anschluss. Stecken Sie die Controller vorsichtig und in der abgebildeten Orientierung.   