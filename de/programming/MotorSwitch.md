---
title: Das erste Programm
layout: category
lang: de
classes: wide
sidebar:
    nav: manual-de
---
Das erste Programm gibt nicht "Hello World" auf dem Bildschirm aus. Es wird einen Motor mit einem einfachen Taster steuern. 
Dazu werden ein ftSwarm, ein Taster, ein Motor oder eine Lampe sowie eine 9V-Stromversorgung benötigt.

Der Versuchsaufbau ist einfach:

- Am Ausgang M2 des ftSwarm wird der Motor oder eine Lampe angeschlossen.
- Der Taster wird am Eingang A1 angeschlossen.
- Ein 9V Netzteil wird an PWR angeschlossen.
- Der ftSwarm-Controller wird mit einem USB Kabel am PC angeschlossen.

Damit Ihr Controller Programme ausführen kann, muss zunächst der Kelda-Modus aktiviert werden. Starten Sie über die serielle Schnittstelle in das interaktive Firmware Menu. Wechseln Sie im Main Menu nach **(2) swarm configuration**:

```
swarm configuration

This device is connected to swarm "ftSwarm100" with 1 member(s) online.
Swarm PIN is 100.
(1) Kelda:               none
(2) swarm communication: wifi
(3) join another swarm
(4) list swarm members

(0) exit
swarm configuration>
```

Wählen Sie **(1) Kelda** um den Kelda Modus zu aktivieren. Zum Aktivieren der Änderung bootet Ihr Controller.

Beim Neustart zeigt der Controller nun an, dass er im Kelda-Modus betrieben wird:

```
ftSwarmOS 0.5.0

(C) Christian Bergschneider & Stefan Fuss

Press any key to enter bios settings.
I am KELDA!
Boot ftSwarm100 (SN:100).
```

Da der Controller im Kelda-Modus gestartet wurde, wechselt er nicht mehr automatisch in das interaktive Firmwaremenu. Geben Sie **setup** ein, das Menu wird gestartet. Wechseln Sie erneut zu **(2) swarm configuration**. Geben Sie nun mit **(3) create a new swarm** Ihrem Swarm - auch wenn er erst aus einem Controller besteht - Ihren Liebingsnamen.



Schreiben Sie den folgenden Sketch oder verwenden Sie die Beispieldatei *MotorSwitch* und flashen ihn auf Ihrem ftSwarm-Controller. Wird der Taster gedrückt, so startet der Motor. Lässt man den Taster los, stoppt der Motor.

Setzen Sie anstatt eines ftSwarmRS einen ftSwarmControl oder einen ftSwarm ein? Tauschen Sie dafür ``#include <ftSwarmRS.h>`` mit ``#include <ftSwarmControl.h>`` oder ``#include <ftSwarm.h>`` aus.

```cpp
#include <ftSwarmRS.h>

FtSwarmSwitch *sw;
FtSwarmMotor  *mot;

void setup( ) {

  Serial.begin(115200);

  // start the swarm
  FtSwarmSerialNumber_t local = ftSwarm.begin( );
	
  // get switch and motor instances
  sw  = new FtSwarmSwitch( local, FTSWARM_A1 );
  mot = new FtSwarmMotor( local, FTSWARM_M2 );

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
Der Sketch ist sehr einfach. Wie alle Arduino-Programme basieren sie auf den beiden Funktionen **`setup`** und **`loop`**. 

- Die **`setup`** Funktion wird beim Start des Sketches automatisch aufgerufen. In dieser Funktion wird normalerweise die Hardware initialisiert.
- Danach wird die **`loop`** Funktion ausgeführt. Wird diese beendet, startet der Sketch diese immer wieder von neuem. In der **`loop`** findet die eigentliche Steuerung des Modells statt. 

**`#include "ftSwarm.h"`** lädt die  ftSwarm-Bibliothek um die ftSwarm Firmware zu verwenden. 
Danach werden die IOs **`switch`** und **`motor`** definiert.

In **`setup`** wird zunächst die serielle Console initialisiert. Darüber können Debug- und Fehlermeldungen auf dem PC ausgegeben werden:

```cpp
Serial.begin(115200);
```

Danach wird der Schwarm initialisiert:

```cpp
// start the swarm
FtSwarmSerialNumber local = ftSwarm.begin( );
```

Es wird die Seriennummer des lokalen Controllers zurückgegeben. Mit der Seriennummer werden nun Instanzen für Taster und Motor erzeugt:

```cpp
sw  = new FtSwarmSwitch( local, FTSWARM_A1 );
mot = new FtSwarmMotor( local, FTSWARM_M2 );
```

* **Achtung:** * Es muss immer zuerst der Schwarm gestartet werden, bevor ein IO genutzt werden kann. Wird ein IO angesprochen, der noch nicht im Schwarm online ist, so wartet die Firmware bis der IO vorhanden ist. Ist der Schwarm noch nicht initialisiert, wartet das Programm in einer Endlosschleife.

Um die IOs global zu definieren, müssen sie deshalb als Pointer implementiert werden. So können Sie initialisiert werden, nachdem der Schwarm gestartet wurde.

In **`loop`** wird der Taster abgefragt und der Motor gestartet und wieder angehalten.

```cpp
if ( sw->isPressed() )
  mot->setSpeed(255);
else
  mot->setSpeed(0);
```

