---
title: Firmware & Updates
Lang:  de
layout: category
classes: wide
sidebar:
    nav: manual-en
---

For a functioning Swarm, the same software version must be used on all Swarm members and the Kelda. The Kelda receives its firmware version from the ftSwarm library used. You must flash the appropriate firmware on the Swarm members as well.

The documentation often refers to "the firmware". Technically speaking, "the firmware" is just a short program that starts a Swarm member and uses the current ftSwarm library.

Under [Versions](../versions) you will find an overview of the changes in the respective versions.

### Arduino IDE

Install the latest version of the ftSwarm library by downloading and installing the appropriate ZIP file from github in the releases section. Please note that there is now a separate library for each of the different device types. Detailed instructions for installing the library and configuring the IDE can be found [here](../ide).

The firmware for the Swarm Member is an Arduino sketch. You can download the appropriate sketch for your hardware from [github](https://github.com/elektrofuzzis/ftSwarm/tree/master/src/arduino/firmware), or you can call up the following code snippet in your own sketch.

```cpp
void setup() {

  Serial.begin(115200);

  firmware();
  ESP.restart();
   
}
```

### PlatformIO

The ftSwarm libraries under PIO update themselves automatically. This means that when you flash your programs on the Kelda, you automatically install the latest version of the framework and firmware. However, the Swarm members must be updated manually.

**Attention:** If the Swarm no longer works after installing a new control program on the Kelda - members cannot find the Kelda, incorrect behavior of the Swarm members - you should definitely check whether the Kelda is using the same firmware version as the Swarm members. Use the "Watch" function on the github repro to be actively informed about version changes.

The firmware for the Swarm Member is a PIO project. You can find the appropriate project for your hardware on [github](https://github.com/elektrofuzzis/ftSwarm/tree/master/src) or you can call up the following code snippet in your own sketch.

```cpp
void setup() {

  Serial.begin(115200);

  firmware();
  ESP.restart();
   
}
```