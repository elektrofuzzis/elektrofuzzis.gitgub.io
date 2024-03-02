---
title: Installation der IDE 
layout: category
lang: de
classes: wide
sidebar:
    nav: gettingstarted-de
---

Für die Programmierung der ftSwarm-Controller in c++ gibt es die beiden Möglichkeiten Arduino und PlattformIO. Für Anfänger ist die Arduino-IDE am besten: einfach in der Installation und Bedienung, sowie eine sehr große Internet Community.

- [Arduino](https://www.arduino.cc/)
   ist die verbreiteste IDE für DIY Projekte. 2005 wurde sie in einem Projekt zur Entwicklung eines Open-Source-Mikrocontroller-Boards entwickelt, heute unterstützt die Plattform alle gängigen Mikrocontroller. 

- [PlattformIO](https://platformio.org)
   ist ein Plugin für Standard IDEs wie [Visual Studio Code](https://code.visualstudio.com/) zur Entwicklung von Embedded Systems. Das Einrichten von PlattformIO ist etwas komplizierter, die IDEs sind jedoch deutlich besser und das Compilieren der Software deutlich schneller. Die Benutzung von VSCode wird im [Advanced-Bereich](/de/advanced/plattformIO) erklärt.

Die Arduino IDE gibt es in zwei Versionen. Unterstützt werden 1.8.19 oder die jeweils neueste 2.x Version. Version 1.8.19 ist auf älteren PCs schneller.

Für die Installation sind mehrere Schritte notwendig. Die Anleitung bezieht sich auf Version 2.x der IDE. Die Konfigurationsschritte in der alten Version sind die gleichen, die Menüführung ist etwas anders.

### 1. Download der IDE

Download und Installation der Arduino IDE von [arduino.cc](https://www.arduino.cc/en/software).

### 2. Eintrag der Boardverwalter-URLs

Öffnen Sie den Arduino IDE den Voreinstellungen-Dialog *Datei/Einstellungen öffnen*.

In *Zusätzliche Boardverwalter-URLs* müssen die folgenden URLs eintragen werden:
   - https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   - https://raw.githubusercontent.com/harbaum/ftduino/master/package_ftduino_index.json

Zu *Werkzeuge/Board/Boardverwaltung* wechseln and die neueste Version von *esp32 by espressif systems* installieren. Sollten nur 1.x-Versionen angezeigt werden, die Einstellung der Boardverwalter URL aus dem vorherigen Schritt überprüfen.

### 3. Bibliotheken installieren

Unsere ftSwarm Firmware benötigt einige Drittbibliotheken. Diese werden über *Werkzeuge\Bibliotheken verwalten* installiert:

- *Adafruit GFX Library* Version 1.10.12 oder neuer
- *Adafruit SSD1306* Version 2.5.3 oder neuer
- *FastLED by Daniel Garcia* Version 3.4.0 oder neuer

Um die ftSwarm Bibliothek zu installieren, muss die neueste Version von ftswarm.zip von <a href="https://github.com/elektrofuzzis/ftSwarm/releases">github</a> geladen und über *Sketch\Bibliothek einbinden\ZIP Bibliothek hinzufügen* installiert werden.

### 4. Board konfigurieren

Nun muss noch das richtige Board unter *Werkzeuge* eingestellt werden:

<table>
   <tr>
      <td>Controller</td>
      <td>ftSwarm<br>ftSwarmControl<br>ftSwarmCAM</td>
      <td>ftSwarmRS<br>ftSwarmPwrDrive<br>ftSwarmDuino</td>
   </tr>
   <tr>
      <td>Tools\Board\ESP32 Arduino</td>
      <td>ESP32 Dev Module</td>
      <td>ESP32S3 Dev Module</td>
   </tr>
   <tr>
      <td>Tools\PSRAM</td>
      <td>Enabled</td><td>Enabled</td>
   </tr>
   <tr>
      <td>Tools\Core Debug Level:</td>
      <td>none</td>
      <td>none</td>
   </tr>
   <tr>
      <td>Tools\Arduino Runs On:</td>
      <td>core 0</td>
      <td>core 0</td>
   </tr>
   <tr>
      <td>Tools\Events Run On:</td>
      <td>core 1</td>
      <td>core 1</td>
   </tr>
   <tr>
      <td>Tools\Port:</td>
      <td>virtuellen COM-Port auswählen</td>
      <td>virtuellen COM-Port auswählen</td>
   </tr>
</table>
 
### 5. Compile & Upload:

Arduino Programme werden Sketch genannt und als *.ino* Dateien gespeichert. Es kann in einem Verzeichnis immer nur ein Sketch gespeichert werden, da der Verzeichnisname identisch zum Sketchnamen sein muss.

<style>
img { vertical-align: middle;important! }
</style>

- ![build](/assets/img/arduino_compile.png) compiliert den Sketch.
- ![upload](/assets/img/arduino_upload.png) flashed den Sketch auf den ftSwarm.
- ![serial](/assets/img/arduino_serial.png) startet eine Serielle Konsole.

Die Beispiele aus dem Tutorial können über *Datei/Beispiele/ftSwarm* aufgerufen werden.
