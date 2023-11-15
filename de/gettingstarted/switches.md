---
title: Switches & Buttons
layout: category
lang: de
classes: wide
sidebar:
    nav: gettingstarted-de
---

Der ftSwarm kennt Switches und Buttons, ist das nicht das Gleiche? Switches sind externe, an die Eingänge A1 bis A6 angeschlossene Taster. Buttons gibt es nur beim *ftSwarmControl* - die fest verbauten Taster werden über eine eigene Klasse angesprochen.

### Normally closed & normally open

*fischertechnik* mini switches haben 3 Anschlüsse. Im Standard werden Pin 1 und Pin 3 am mini switch angeschlossen. Der Taster ist "normally open". Beim Drücken des Tasters wird der Schalter geschlossen. Verwendet man Pin  1 & 2 ist der Taster "normally closed" und öffnet beim Tastendruck. Diese Variante ist z.B. bei Notabschaltungen besser, da ein gebrochenes Kabel oder ein schlechter Stecker ebenfalls die Notabschaltung auslöst.

```cpp
normallyOpen   = FtSwarmSwitch( 4711, FTSWARM_A1 );
normallyClosed = FtSwarmSwitch( 4711, FTSWARM_A2, false );
```

### Toggles

In den meisten Fällen ist das Signal eines Eingangs bzw. eines Tasters egal, nur der Statuswechsel ist von interesse. Mit

```cpp
while (switch.isReleased());
```

kann man aktiv darauf warten, dass der Taster gedrückt wird. Aber durch die Schleife wird ein Core belegt und der Controller kann keine anderen Aktionen ausführen, während er auf den Taster wartet. Die Firmware liest im Hintergrund die Eingänge regelmäßig aus und kann so Statuswechse erkennen. Der Code

```cpp
void loop() {

  if (switch.hasToggledUp()) motor.setSpeed(100);
  if (switch.hasToggledDown()) motor.setSpeed(0);
  
  // use the time and do someting else
```

ist cleverer, da die CPU beim Warten nicht blockiert wird.

**Achtung:** Jeder Aufruf der *Toggle* Befehle setzt den Togglestatus zurück. Dies ist notwendig, damit nur die Signalwechsel erkannt werden. Die führt aber dazu, dass

```cpp
if ( (switch.hasToggeledDown()) || (switch.hasToggeledUp()) ) led.setColor( CRGB:Green );
```

nur auf Toggle-Up-Events reagiert. Wird die Bedingung ausgewertet, so wird zunächst ``switch.hasToggeledDown()`` ausgeführt.

- Gab es ein Toggle-Down-Event, so ist die Bedingung wahr und die led wird grün.
- Gab es kein Toggle-Down-Event, so führt aber ``switch.hasToggeledDown()`` dazu, dass der Toggle-Status zurückgesetzt wird. Ein vorhandenes Toggle-Up-Event wird also gelöscht, ``switch.hasToggeledUp()`` ist deshalb immer false.

Durch das Drücken des Tasters wird die Led nicht auf grün schalten.

