---
title: Anschlüsse
layout: category
lang: de
classes: wide
sidebar:
    nav: gettingstarted-de
---
Jeder Controller hat einen USB-Anschluß, über den Sie die Firmware oder Ihr Steuerprogramm flashen können. Dies wird auf der nächsten Seite im Detail beschieben.

Der Controller kann zwar über den USB-Port gebootet werden; um die Ein- und Ausgänge des Controllers nutzen zu können, muss unbedingt die externe 9V-Versorgung aktiv sein. 

Die Sensoren im Modell werden an die Eingänge A1 bis A8 der Controller angeschlossen. An diese Anschlüsse können verschiedene analoge oder digitale Sensoren angeschlossen werden (z.B. Taster, Reedkontakte, Fototransistoren, Temperatursensoren ). Der Sensor wird einfach an die <span class="plus">rote</span> und die <span class="minus">grüne</span> Klemme angeschlossen. Bei einigen Sensoren muss auf die Polung geachtet werden, dann wird das am Sensor markierte Kabel an die <span class="plus">rote</span> Klemme aufgelegt. Die <span class="minus">grün</span> markierten Klemmen sind GND bzw. der fischertechnik "-"-Anschluss.

Die meisten Sensoren können an allen Eingängen angeschlossen werden. Je nach Controller und Eingang gibt es einzelne Einschränkungen - so kann z.B. ein Ultraschallsensor nur an A1 der Controllertypen ftSwarm und ftSwarmRS angeschlossen werden. Dies können Sie im Detail bei der Beschreibung der einzelnen Sensorklassen in der API-Referenz nachlesen.

Normale Aktoren (z.B. DC-Motoren, Lampen, Elektroventile) werden an die Motorausgänge M1 bis M8 angeschlossen. Für Servo-Motoren gibt es eigene Stecker.

Einige Controller verfügen über einen RS485-Anschluss um die Swarm-Kommunikation alternativ über Kabel abzubilden. Das Anschlussschema ist in einem eigenenen [RS485-Kapitel](../../advanced/rs485) beschrieben.

<div class="flex-container">
  <div>
    <div><a href="../../products/ftSwarm">ftSwarm</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmJSTPinout.png"></div>
    <div><p class="pdetail">An dem I²C/Gyro-Stecker kann ein MPU6050-Gyro angeschlossen werden.<br><br>Für den Anschluß von ftPixel gibt es einen eigenen Adapter der die Stiftleiste auf einen fischertechnik-Buchse umsetzt.<br><br>SD-Karten können in den seitlichen Schlitz am Gehäuse gesteckt werden.</p></div>
  </div>
  <div>
    <div><a href="../../products/ftSwarmRS">ftSwarmRS</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmRSPinout.png"></div>
    <div><p class="pdetail">Im Gegensatz zum Vorgängermodell können ftPixel direkt an der Klemmleiste ohne Adapter angeschlossen werden.<br><br>SD-Karten können in den seitlichen Schlitz am Gehäuse gesteckt werden.</p></div>
  </div>
  <div>
    <div><a href="../../products/ftSwarmXL">ftSwarmXL</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmXLPinout.png"></div>
    <div><p class="pdetail">Um genügend Leistung für die 8 Motorausgänge zur Verfügung zu stellen, gibt es drei 9V-Spannungsversorgungen, die alle angeschlossen werden müssen. Je nach Strombedarfkann dies über ein oder über mehrere Netzteile erfolgen.<br><br>Bitte beachten Sie in Ihrem Modell, dass der Motorausgang M7 beim Bootenund beim Flashen der Firmware eingeschaltet ist.</p></div>
  </div>
  <div>
    <div><a href="../../products/ftSwarmControl">ftSwarmControl</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmControlPinout.png"></div>
    <div><p class="pdetail">Neben den normalen Eingängen hat der ftSwarmControl zusätzlich die beiden Joysticks J1 und J2 sowie die Buttons S1 bis S4.<br><br>Um die Batterie zu schonen, hat der ftSwarmControl einen Einschalter. Als Batterie können sowohl 9V-Blöcke als auch Akkus eingesetzt werden.<br><br>Um eine SD-Karte zu stecken, muss der untere Gehäuseteil aufgeschraubt werden.</p></div>
  </div>
  <div>
    <div><a href="../../products/ftSwarmPwrDrive">ftSwarmPwrDrive</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmPwrDrivePinout.png"></div>
    <div><p class="pdetail">Der Controller wird auf den I²C-Bus des ftPwrDive aufgesteckt und stellt dann die Schrittmotoren als Step1 bis Step4 im Swarm bereit.<br><br>An die Endschalter (ES1 bis ES4) und den Notaus (EM) können nur digitale Sensoren (Taster, Fototransistoren, Reddkontakte) angeschlossen werden.</p></div>
  </div>
  <div>
    <div><a href="../../products/ftSwarmDuino">ftSwarmDuino</a></div>
    <div><img class="zoom" src="/assets/img/ftSwarmDuinoPinout.png"></div>
    <div><p class="pdetail">Der Controller wird auf den I²C-Bus des ftPwrDive aufgesteckt und stellt dann die Motorausgänge des ftDuino als M1 bis M4 und die Eingänge als A1 bis A8 im Swarm bereit.<br><br>Für die 9V-Stromversorgung reicht es aus, die <span class="plus">rote 9V-Klemme</span> mit dem daneben liegenden 9V-Ausgang des ftDuino zu verbinden. Der GND/Minusanschluß erfolgt automatisch über den I²C-Stecker</p></div>
  </div>
</div>
