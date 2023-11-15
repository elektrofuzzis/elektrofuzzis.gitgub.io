---
title: Ein erster Schwarm
layout: category
lang: de
classes: wide
sidebar:
    nav: gettingstarted-de
---

In das "[Das erste Programm](../MotorSwitch)" haben Sie ein einfaches Programm geschrieben uns es auf einem Controller gestartet. Doch wie funktioniert eine Applikation im Schwarm? In diesem Beispiel wird nun die gleiche Aufgabe - die Steuerung eines Motors durch einen Taster - mit zwei Controllern realisiert. 

Erster Controller (Kelda):
- Der Taster wird am Eingang A1 angeschlossen.
- Ein 9V Netzteil wird an PWR angeschlossen.
- Auf diesem Controller wird Ihr Steuerprogramm laufen.

Zweiter Controller:
- Ein Motor oder eine Lampe werden am Ausgang M2 angeschlossen.
- Ein 9V Netzteil wird an PWR angeschlossen.
- Auf diesem Controller wird die Standardfirmware laufen.

### Einen Swarm bilden

Im letzten Beispiel haben Sie bereits einen Controller als Kelda konfiguriert. Dadurch ist bereits ein Swarm entstanden. Ihr zweiter Controller muss diesem Swarm jetzt nur noch beitreten.    

Wenn Sie den Namen Ihres Swarms nochmals ändern möchten, müssen Sie auf dem Kelda-Controller das Firmware Menü starten. Dazu müssen Sie die Standardfirmware aus **Examples\ftSwarm\firmware** flashen.

Um den zweiten Controller in dem Swarm aufzunehmen, müssen Sie Ihn via USB an Ihrem PC anschließen. Konfigurieren Sie zunächst das WLAN über **(1) wifi & Web UI**. Danach wechseln Sie zu **(2) swarm configuration**:

```
swarm configuration

This device is connected to swarm "ftSwarm101" with 1 member(s) online.
Swarm PIN is 101.
(1) Kelda:               none
(2) swarm communication: wifi
(3) join another swarm
(4) list swarm members

(0) exit
swarm configuration>
```

Fügen Sie nun diesen Controller mit **(3) join another swarm** dem Swarm hinzu. Dazu müssen Sie den Swarm Namen, den Sie auf der Kelda vergeben haben und den Swarm Pin eingeben. Der Kelda Controller muss selbstverständlich eingeschaltet sein. 

Auf der Web-UI der Kelda werden nun beide Controller angezeigt. Der zweite Controller zeigt nur seine eigenen Ein- und Ausgänge an. 

### Eine verteilte Anwendung

Sobald beide Controller einen Schwarm gebildet haben, kann das Biespiel **Examples\ftSwarm\MotorSwitchSwarm** gestartet werden:

```cpp
#include <ftSwarmRS.h>

// serial number of the second controller - change it to your 2nd device serial number
#define remote 2

FtSwarmSwitch *sw;
FtSwarmMotor  *mot;

void setup( ) {

  Serial.begin(115200);

  // start the swarm
  FtSwarmSerialNumber_t local = ftSwarm.begin( );
	
  // get switch and motor instances
  sw  = new FtSwarmSwitch( local, FTSWARM_A1 );
  mot = new FtSwarmMotor( remote, FTSWARM_M2 );

}

void loop( ) {

  // check if switch is pressed or released
  if ( sw->isPressed() )
    mot->setSpeed(255);
  else
    mot->setSpeed(0);
	
  // wait some time
  delay(100);

}
```

Das Programm unterscheidet sich kaum vom [ersten Programm](../MotorSwitch). Es gibt nur zwei kleine Änderungen:

- **#define remote 2** definiert die Seriennummer des zweiten Controllers. Ändern Sie diese entsprechend Ihrer Controller ab.
- **FtSwarmMotor( remote, FTSWARM_M2 );** nutzt nun die Sieriennummer des zweiten Controllers. 

### Was passiert, wenn der zweite Controller nicht online ist?

Verbinden sie ein Terminalprogramm mit dem ersten Controller und trennen Sie am zweiten Controller die Stromversorgung. Starten Sie nun den ersten Controller. Bei **FtSwarmMotor( remote, FTSWARM_M2 );** kommt es nun zu einer Warning: ***Waiting on device***. Beide onboard RGB Leds werden blau, da die Firmware darauf wartet, dass der zweite Controller mit dem Motor online geht.

Schalten Sie am zweiten Controller die Stromversorgung jetzt wieder ein. Sobald der zweite COntroller gestartet ist, registriert es sich bei der Kelda und das Programm kann fortgesetzt werden.
