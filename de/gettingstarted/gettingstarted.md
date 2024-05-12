---
title: Manual
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-de
---

Dieses Manual erklärt die grundlegende Benutzung und Programmierung der ftSwarm-Controller. Wir empfehlen deshalb, zunächst das Manual Kapitel für Kapitel zu lesen und die Beispiele nachzustellen. In der [API-Referenz](../cpp-api/index) werden die verschiedenen Klassen im Detail sowie das Anschlussschema der verschiedenen Sensoren und Aktoren erklärt.

1. Inbetriebnahme
- [Lerne die Anschlüsse der ftSwarm-Familie kennen.](../pinout)
- [Den ftSwarm-Controller über USB mit dem PC verbinden](../serial)
- [Das WLAN konfigurieren und die Statusseite benutzen](../WebUI)


2. Programmierung in C++
- [Installation der IDE](../programming/ide)
- [Das erste Programm auf einem ftSwarm Controller](../programming/MotorSwitch)
- [Das Kelda Prinzip](../programming/kelda)
- [Der erste Schwarm](../programming/MotorSwitchSwarm)
- [Aliasnamen machen das Programm lesbarer](../programming/MotorSwitchAlias)
- [Buttons, Switches und Toggles](../programming/switches)
- [Eine Fernbedienung ohne eine Zeile Code](../programming/RemoteControl)
- [Einfache Programmierung durch Events](../programming/EventControlled)
- [RGB LEDs & ftPixel](../programming/FtSwarmPixel)
- [OLED Display](../programming/FtSwarmOLED)

3. [Den ftSwarm über RS485 verbinden](../rs485/rs485)

4. Extension Port
- [Einführung](../extensionPort/index)
- [I²C Breakout Boards](../extensionPort/I2CMaster)
- [I²C TX-/TXT-Kommunikation](../extensionPort/I2CSlave)
- [Gyro](../extensionPort/gyro)
- [Motorausgänge](../extensionPort/outputs)

5. Firmware & Versionen
- [Konfiguration komplett](../Configuration)
- [Firmware & Updates](../firmware)
- [Versionen](../versions)

4. Advanced
- [Programmierung mit PlatformIO & VSCode](../PlatformIO)
- [Programme auf dem ftSwarm debuggen](../debugging)

### Einsatzgebiet & Gewährleistung

Die ftSwarm Controller sind dafür gedacht, kleine vernetzte Steuerungen für DIY- und Spielzeugmodelle zu bauen:

- DIY Projekte sollten niemals unbeobachtet laufen.
- Bauen Sie keine Roboter, die Menschen, Tiere oder Gegenstände schädigen könnten.
- ftSwarm Controller sind nicht für professionelle Roboter geeignet.
- Bitte testen Sie die zur Verfügung gestellte Soft- und Hardware um sicherzustellen, dass sie den Anforderungen Ihres Projektes gerecht werden.

Die ftSwam Controller sind als Hobbyprojekt entstanden. Entsprechend gibt es Einschränkungen und Fehler. Jede Gewährleistung auf die hier vorgestellte Soft- und Hardware ist ausgeschlossen.
{: .notice--info}
