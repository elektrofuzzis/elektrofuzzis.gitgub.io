---
title: FtSwarmCounter
layout: category
lang: de
classes: wide
sidebar:
    nav: cppapi-de
---
<div class="apicontainer">
    <div class="apileft">
        Alle Eingänge können als Zähler verwendet werden. Als Sensor eignen sich Reedkontakte, Fototransistoren und Encodermotoren. Auch das seltene Walzenrad 32367 kann mit der Lichtschranke CNY 37 verwendet werden. 
    </div>
    <div class="apiright apiimg"><img title="Bildnachweis: fischertechnik" src="/assets/img/switches/counter-api.png">Zähler</div>
</div>


Die fischertechnik-Taster sind als Sensoren für die Zählerklasse ungeeignet, da sie zu sehr prellen.
{: .notice--info}


#### FtSwarmCounter(FtSwarmSerialNumber_t serialNumber, FtSwarmPort_t port)

Constructor um ein FtSwarmCounter Objekt zu erzeugen. Ist der angesprochene Controller nicht online, so wartet die Firmware solange bis der entsprechende Controller gestartet wird.

- serialNumber: Seriennummer des ftSwarm-Controllers.
- port: Portnummer, **FTSWARM_A1**, **FTSWARM_A2**, ..., **FTSWARM_A6**.

#### FtSwarmCounter(const char *name)

Constructor um ein FtSwarmCounter Objekt zu erzeugen. Ist der angesprochene Controller nicht online, so wartet die Firmware solange bis der entsprechende Controller gestartet wird.

- name: Aliasname des IO-Ports.

#### int16_t getCounter()

Gibt die Anzahl der gezählten Impulse zurück.

#### void resetCounter()

Setzt den Zähler auf 0 zurück.

