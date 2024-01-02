---
title: FtSwarmFrequencymeter
layout: category
lang: de
classes: wide
sidebar:
    nav: cppapi-de
---
<div class="apicontainer">
    <div class="apileft">
        Alle Eingänge können zur Frequenzmessung verwendet werden. Es können Frequenzen zwischen 0 und 1kHz gemessen werden.
    </div>
    <div class="apiright apiimg"><img title="Bildnachweis: fischertechnik" src="/assets/img/switches/frequency-api.png">Frequenzzähler</div>
</div>

Als Sensor eignen sich Reedkontakte, Fototransistoren und Encodermotoren. Auch das seltene Walzenrad 32367 kann in Kombination mit der Lichtschranke CNY 37 verwendet werden. 

Die fischertechnik-Taster sind als Sensoren für die Zählerklasse ungeeignet, da sie zu sehr prellen.
{: .notice--info}

Ist das Eingangssignal für die Frequenzmessung wesentlich höher als 1kHz, so belastet das Signal die CPU der ftSwarm-Controller so stark, dass der Controller langsam oder fehlerhaft reagiert.  
{: .notice--info}

#### FtSwarmFrequencymeter(FtSwarmSerialNumber_t serialNumber, FtSwarmPort_t port)

Constructor um ein FtSwarmFrequencymeter Objekt zu erzeugen. Ist der angesprochene Controller nicht online, so wartet die Firmware solange bis der entsprechende Controller gestartet wird.

- serialNumber: Seriennummer des ftSwarm-Controllers.
- port: Portnummer, **FTSWARM_A1**, **FTSWARM_A2**, ..., **FTSWARM_A6**.

#### FtSwarmFrequencymeter(const char *name)

Constructor um ein FtSwarmFrequencymeter Objekt zu erzeugen. Ist der angesprochene Controller nicht online, so wartet die Firmware solange bis der entsprechende Controller gestartet wird.

- name: Aliasname des IO-Ports.

#### int16_t getFrequency()

Gibt die Frequenz in Hz zurück.

