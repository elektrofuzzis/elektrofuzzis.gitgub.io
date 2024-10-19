---
title: Firmware & Updates
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-de
---

Für einen funktionierenden Swarm muss auf allen Swarm Membern und der Kelda die gleiche Softwareversion verwendet werden. Die Kelda erhält ihre Firmwareversion durch die verwendete ftSwarm-Bibliothek. Auf den Swarm Membern müssen Sie die dazu passende Firmware flashen.

In der Dokumentation zu den ftSwarm Controllern wird häufig auf "die Firmware" verwiesen. Technisch gesehen ist "die Firmware" nur ein kurzes Programm, das einen Swarm Member startet und dabei die aktuelle ftSwarm-Bibliothek verwendet.

Unter [Versionen](https://github.com/elektrofuzzis/ftSwarm/releases) finden Sie eine Übersicht der Änderungen in den jeweligen Versionen.

### Arduino IDE

Installieren Sie die neueste Version der ftSwarm-Bibliothek, indem Sie das passende ZIP-File auf github im Bereich Releases herunterladen und installeren. Bitte beachten Sie, dass es mittlerweile für die verschiedenen Gerätetypen jeweils eine eigene Bibliothek gibt. Eine detaillierte Anleitung zur Installation der Bibliothek und der Konfiguration der IDE finden Sie [hier](../ide).

Die Firmware für die Swarm Member ist ein Arduino-Sketch. Den passenden Sketch zu Ihrer Hardware können Sie von [github](https://github.com/elektrofuzzis/ftSwarm/tree/master/src/arduino/firmware) herunterladen, oder Sie rufen in einem eigenen Sketch das folgende Code-Snippet auf.

```cpp
void setup() {

  Serial.begin(115200);

  firmware();
  ESP.restart();
   
}
```

### PlatformIO

Die ftSwarm-Bibliotheken unter PIO aktualisieren sich selbständig. Das bedeutet, dass Sie mit dem Flashen Ihrer Programme auf der Kelda, automatisch die neueste Version des Frameworks und der Firmware einspielen. Die Swarm Member müssen jedoch manuell upgedatet werden.

**Achtung:** Sollte nach dem Einspielen eines neuen Steuerprogramms auf der Kelda der Swarm nicht mehr funktionieren - Member finden die Kelda nicht, fehlerhaftes Verhalten der Swarm Member - so sollten Sie unbedingt prüfen, ob die Kelda die gleiche Firmwareversion wie die Swarm Member verwendet. Nutzen Sie die "Watch"-Funktion am github-Repro um aktiv über Versionsänderungen informiert zu werden. 

Die Firmware für die Swarm Member ist ein PIO-Projekt. Das passende Projekt zu Ihrer Hardware finden Sie auf [github](https://github.com/elektrofuzzis/ftSwarm/tree/master/src) oder Sie rufen in einem eigenen Sketch das folgende Code-Snippet auf.

```cpp
void setup() {

  Serial.begin(115200);

  firmware();
  ESP.restart();
   
}
```