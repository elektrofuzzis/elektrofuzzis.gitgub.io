---
title: Konfiguration
layout: category
toc: true
toc_sticky: true
lang: de
classes: wide
sidebar:
    nav: gettingstarted-de
---
Die Controller benötigen einige Einstellungen, wie z.B. ein WLAN-Profil oder auch die Konfiguration des Swarms. Einige Einstellungen wurden bereits im Tutorial verwendet. Dieses Kapitel beschreibt alle Konfigurationsmöglichkeiten im Detail.

Zur Konfiguration des Controllers kann in der Standardfirmware jederzeit das "Configuration Menu" gestartet werden. Dazu muss nur ein Terminal Programm verbunden werden nur eine Taste gedrückt werden. Das Configuration Menu kann mit

```cpp
firmware();
```

jederzeit aufgerufen werden.

<hr>
### Main Menu

Das **Main Menu** ist die oberste Ebene der Konfigurationsmenüs.  **(0) exit** beendet den Konfigurationsmodus, in der Standardfirmware bootet danach der Controller neu. Wurde das **Main Menu** mit **ftSwarm.setup();** aus einem Programm heraus aufgerufen, so werden nun die nächsten Kommandos im Programm ausgeführt.

```
***** Main Menu *****

( 1) wifi & Web UI
( 2) swarm configuration
( 3) alias names
( 4) factory reset
( 5) remoteControl
( 6) extention port

( 0) exit
```

Beim *ftSwarmControl* gibt es einen zusätzlichen Menüpunkt um den Displaytyp einzustellen und die Joysticks zu kalibrieren.

<hr>
### Wifi & Web UI

In diesem Bereich werden die WLAN-Einstellungen vorgenommen und die Statusseite der Controller konfiguriert.

```
***** Wifi & WebUI *****

hostname:           ftSwarm100
ip-address:         192.168.4.1

( 1) wifi:           AP-Mode
( 2) SSID:           ftSwarm100
( 3) Password:       *****
( 4) Web UI:         on
( 5) ftPixels in UI: 2
```

Um einen Swarm zu bilden, müssen die einzelnen Controller miteinander über WLAN oder RS485 kommunizieren. In der Regel kommunizieren sie über WLAN - nur die ftSwarmRS können zusätzlich kabelgebunden über RS485 kommunizieren.

Außerdem kann über WLAN die Statusseite der Controller aufgerufen werden.

Mit der Option **(1) wifi** wird der WLAN-Typ festgelegt: 
- CLIENT-MODE nutzt ein vorhandenes WLAN. Im Regelfall ist dies das WLAN Ihres Internetrouters.
- AP-MODE benötigt keinen Router, der ftSwarm-Controller erzeugt ein eigenes WLAN Netzwerk.
- OFF schaltet WLAN aus (nur ftSwarmRS) und reduziert deutlich den Stromverbrauch.

Ist ein WLAN bereits vorhanden, so sollten Sie dieses unbedingt verwenden. Wählen Sie dazu CLIENT-MODE und setzen Sie mit **SSID** und **password** die Zugangsdaten zu Ihrem WLAN. Mit **exit** speichern Sie die Daten im NVS des Controllers und er verbindet sich mit Ihrem WLAN indem er neu startet. 

Der **AP-MODE** ist ein wenig tricky:
- Wählen Sie einen Controller im geplanten Swarm aus und schalten Sie dort auf AP-MODE. Mit **SSID** geben Sie dem WLAN einen Namen. Aufgrund von Einschränkungen von espressif, sind WLANs im AP-MODE immer offene WLANs und es wird kein Passwort benötigt.
- Zusätzlich müssen Sie mit Option **wifi channel** den Kanal auswählen, auf dem Ihre SSID arbeitet.
- Alle anderen Controller werden auf CLIENT-MODE gestellt. Die SSID ist die des obigen Controllers; setzen Sie ein leeres Password.
- Setzen Sie nie die Kelda in den AP-MODE. Wie im Tutorial beschrieben, führt dies zu einigen Problemen beim flushen Ihres Programms.
- Der AP-MODE hat einen hohen Stromverbrauch, das Netzwerk ist für jeden offen (es hat kein Password) und der Sendebereich ist sehr beschränkt.

Die Option **off** kann nur am ftSwarmRS gesetzt werden. In diesem Fall muss Ihr Swarm komplett über RS485 kommunizieren.

Die WLAN-Kanäle teilen Sie mit anderen WLANs. Deshalb ist es wichtig, den "richtigen" Kanal auszuwählen. Die ESP32-Prozessoren verwenden das 2.4 GHz-Band. Dieser Bereich ist in 11 Kanäle aufgeteilt, dabei überlappen sich benachbarte Kanäle. Werden zwei benachbarte Kanäle durch ein WLAN verwendet, so stören diese sich gegenseitig. Deshalb ist es im 2.4GHz-Band am Besten, wenn alle WLANs nur die Kanäle 1, 6 und 11 verwenden. Optimalerweise gibt es einen nicht verwendeten Kanal. Ist dieser nicht verfügbar, so nutzen Sie einen bereits verwendeten Kanal dessen Nachbarkanäle nicht in Verwendung sind. Welche Kanäle bereits verwendet sind, können Sie sich auf dem meisten Internetroutern anzeigen lassen. Mit der App [wifiman](https://play.google.com/store/apps/details?id=com.ubnt.usurvey&hl=de&gl=US&pli=1) können Sie das auch über Ihr Smartphone analysieren.
{: .notice--info}

Die letzten beiden Optionen legen das Verhalten der Statusseite fest.

- **WebUI: on/off** schaltet den WEB-Server für die Statuspage ein bzw aus.
- **Show X ftPixels in UI** legt die Anzahl der ftPixel fest, die auf der Statuspage angezeigt werden, bzw. die im Menu "Alias Names" einen Namen zugewiesen bekommen können. Für die Programmierung von ftPixel über die Port-Nummer hat dieser Wert keinen Einfluss, es können immer alle Ports **FTSWARM_LED1** bis **FTSWARM_LED18** angesprochen werden.

<hr>
### Swarm Configuration

In diesem Menü wird der Swarm gebildet. Bevor Sie einen Swarm bilden können, müssen alle Controller untereinander kommunizieren können. Dazu müssen entweder alle Controller im gleichen WLAN angemeldet sein, oder über RS485 verbunden sein.

Die angezeigten Informationen hängen vom Betriebsmodus des Controllers ab. Als Kelda sieht der Bildschirm folgendermaßen aus:

```
***** swarm configuration *****

ftSwarm100 is Kelda running swarm "mySwarm" using Pin 666:

SN  NW Age Hostname
100 000014 ftSwarm100
101 000012 ftSwarm101

( 1) swarm communication: wifi
( 2) swarm speed:         4
( 3) create a new swarm
( 4) join another swarm
( 5) invite a controller to my swarm
( 6) reject a controller from my swarm

( 0) exit
```` 
In diesem Modus zeigt die Kelda alle Swarm Member einschließlich sich selbst an. Diese Liste der Teilnehmer im Swarm ist  im NVS-Speicher der Kelda gespeichert. "NW Age" zeigt die Zeitdifferenz in ms an, wann die Kelda die letzte Statusmeldung des Controllers erhalten hat.

Jeder Controller sendet seinen Status alle 25 ms. Da es zu Paketverlusten kommen kann, sind alle Werte unter 100ms "online".

Der NW-Age-Wert der Kelda zeigt die verstrichene Zeit seit dem letzten Auslesen ihrer Sensoren an. 

Als Swarm Member stehen weniger Optionen zur Verfügung:

```
***** swarm configuration *****

ftSwarm101 is connected to swarm "mySwarm".
Swarm PIN is 66.

( 1) swarm communication: wifi
( 2) swarm speed:         4
( 3) create a new swarm
( 4) join another swarm

( 0) exit
```` 
**swarm communication** stellt ein, über welches Medium die ftSwarm miteinander kommunizieren.
- **wifi**: die Controller nutzen WLAN. 
- **RS485**: die Controller nutzen die RS485-Schnittstelle. Diese Option steht nur am fTSwarmRS zur Verfügung. Ein Mixed-Mode mit WLAN und RS485 ist nicht möglich. 

**swarm speed** stellt die Übertragungsrate im RS485-Modus ein. 4 ist die höchste Geschwindigkeit, die bis zu 32 Controller bei einer maximale Kabellänge von 50 m ermöglicht. Bei Problemen mit der Kabellänge reduzieren Sie sie Swarm Speed schrittweise. Bei einem Wert von 0 können Sie bis zu 4.000 m Kabellänge verwenden, sind aber auf 4 Controller beschränkt.

**create a new swarm** erzegt einen neuen Schwarm und stellt den Kelda-Modus an diesem Controller ein. Der Name und die PIN des neuen Schwarms werden abgefragt. Anschließend ist dieser Controller der erste und einzige Controller innerhalb des neuen Schwarms.

**join another swarm** fügt den Controller zu einem existierenden Swarm hinzu. Es werden der Name des Swarms und die PIN abgefragt. Der Controller versucht sich dann mit dem Swarm zu verbinden, dazu muss der Kelda Controller des Swarms online sein. War der Controller zuvor im Kelda-Modus wird er durch die Aktion zum Swarm Member.

**invite a controller to my swarm** fügt einen anderen meinem Swarm hinzu. Der angefragte Controller nimmt die Anfrage an, solange er nicht mit anderen Controllern in einem Swarm verbunden ist.

**reject a controller from my swarm** löscht den Controller aus meinem Swarm.

<hr>
### Alias Names Settings

Mit diesem Menü können Aliasnamen für die Ports eingestellt werden. Anschließend können die IO-Ports über den logischen Namen anstatt der Portnummer angesprochen werden. Im Tutorial ist dies im Kapitel [Alias Names](../gettingstarted/MotorSwitchAlias/) näher erklärt.

Um einen Aliasnamen für einen IO Port zu vergeben, wählen Sie die Nummer des gewüschten IOs aus. Der Name darf bis zu 30 Zeichen lang sein und darf keine Leerzeichen enthalten.

In einem Swarm muss ein Aliasname eindeutig sein. Dies wird bei der Konfiguration nicht geprüft - es müssen nicht alle Controller im Swarm online sein. Wird ein Name mehrfach vergeben, so ist es Zufall welcher IO-Port beim Benutzen des Aliasnamens angesprochen wird.
{: .notice--info}

<hr>
### Factory Reset

Dieser Menüpunkt stellt den Controller auf Werkseinstellungen zurück. Da im Flash evtl. vertrauliche Informationen wie die wifi-Parameter gespeichert sind, sollten Sie einen Controller auf Werkseinstellungen zurücksetzten, bevor sie ihn an Dritte weitergeben.

<hr>
### Remote Control Settings

Mit diesem Menü kann ein Swarm ohne eine Zeile Code programmiert werden. Dazu bekommen die einzelnen IO-Ports Aliasnamen, die dann über den ftSwarmControl angesprochen werden. Dazu werden auf den Buttons und Joysticks des ftSwarmControl EVents definiert, die die IO Ports steuern.

Eine detaillierte Beschreibung ist im Tutorial unter [Fernbedieung](../gettingstarted/RemoteControl/) zu finden.

<hr>
### Extention Port

Die Controller verfügen über einen Extention Port, an den externe Hardware angeschlossen werden kann. 

Der Anschluß ist im Gegensatz zu den anderen Anschlüssen des Controllers nicht gegen Überspannung oder Verpolung geschützt.

**ftSwarm:** Der Extention Port ist die Steckerleiste an der Oberseite des Controllers. 
- An diesem Port kann der optionale MC6040-Gyro angeschlossen werden. 
- Alternativ kann der Port als I²C-Bus (als Master oder als Slave) betrieben werden. 
- Als dritte Möglichkeit können die beiden IO-Pins als logische "Motorausgänge" geschaltet werden. Bitte beachten Sie, dass es reine GPIO-Pins sind die keine Last schalten können. Um Motoren, Relais oder Lampen anzuschließen benötigen Sie zusätzliche externe Leistungstreiber.    

**ftSwarmRS:** Der Extention Port ist die 4-polige Stiftleister an der Oberseite des Controllers.
- Der Port kann als I²C-Bus (als Master oder als Slave) betrieben werden. 
- Als zweite Möglichkeit können die beiden IO-Pins als logische "Motorausgänge" geschaltet werden. Bitte beachten Sie, dass es reine GPIO-Pins sind die keine Last schalten können. Um Motoren, Relais oder Lampen anzuschließen benötigen Sie zusätzliche externe Leistungstreiber.    

Der interne Gyro des ftSwarmRS verwendet einen eigenen I²C-Bus.

**ftSwarmControl**: 
Der Port kann nur als I²C-Bus betrieben werden. Da an diesem Bus auch das OLED-Display und der optionale Gyro angeschlossen sind, kann er nur im Master-Mode betrieben werden. Im Gegensatz zu den beiden anderen Controllern können sowohl 3.3V- als auch 5V-Sensoren angeschlossen werden.


**Mode** legt den Betriebsmodus des Extention Ports fest.
- **off** schaltet den Port aus.
- **I2C-Master** schaltet den Port als I²C-Bus. Der Controller ist Busmaster. Verwenden Sie diese Option, wenn Sie I²C-Sensoren anschließen wollen.
- **I2C-Slave** schaltet den Port ebenfalls als I²C-Bus. Der Controller ist in diesem Fall Slave. Diese Funktion kann z.B. dazu verwendet werden um Daten mit einem TXT-Controller auszutauschen.
- **Gyro MCU6040** aktiviert beim *ftSwarmControl* bzw. beim *ftSwarm* den optionalen Gyro.
- **Outputs** ist nur beim *ftSwarm* und *ftSwarmRS* möglich. Die beiden IO-Pins des Extention Ports können dann softwareseitig als Motorausgänge angesprochen werden. An den IO-Pins liegt dann ein PWM-Signal entsprechend dem eingestellten Speed-Wert des Motorausgangs an. Bitte beachten Sie, dass der IO-Pin nur ein 3.3V-Logikpegel liefert und ohne Zusatzhardware keine Aktoren schalten kann.

**Gyro** schaltet die Verwendung des Gyros ein bzw. aus. Schalten Sie den Gyro nur ein, wenn Sie ihn in der Anwendung auch nutzen wollen. Ungenutzte Gyros haben einen unnötigen Stromverbrauch und im Swarm einen hohen Kommunikationsbearf.

**I2C Address** legt die I²C-Adresse des Controllers im SLAVE-Modus fest. Diese Option steht im MASTER-Modus nicht zur Verfügung.

<hr>
### ftSwarmControl

Der ftSwarmControl hat zwei spezifische Einstellungen.

**Display Type**: Je nach verwendetem OLED-Display unterscheidet sich die Ansteuerung der OLEDs auf Firmwareebene ein wenig. Die ersten ftSwarmControl benötigen den Display Typ 0, die neueren Typ 1. Sollte das Display des ftSwarmControl nicht funktionieren, stellen Sie hier einen anderen Wert ein.  

**Calibrate Joysticks**: Die Joysticks liefern ein analoges Signal. Mit Calibrate Joysticks kann die mittlere Stellung des Joysticks kalibriert werden.


