---
title: A first Swarm
layout: category
lang: en
classes: wide
sidebar:
    nav: gettingstarted-en
---

In the "[The first program](../MotorSwitch)" you have written a simple program and started it on a controller. But how does an application work in a swarm? In this example, the same task - controlling a motor using a pushbutton - is implemented with two controllers.

1st Controller:
- Connect a switch to input A1.
- Connect a 9V power supply to PWR.
- Your control program will run on this controller.

2nd Controller:
- Connect a motor or a lamp to output M2 of your ftSwarm.
- Connect a 9V power supply to PWR.
- The standard firmware will run on this controller.

### Build a swarm

In the last example, you have already configured a controller as a Kelda. This has already created a swarm. Your second controller now only needs to join this swarm.    

If you want to change the name of your swarm again, you need to start the firmware menu on the Kelda controller. To do this, you must flash the standard firmware from **Examples\ftSwarm\firmware**.

To include the second controller in the Swarm, you must connect it to your PC via USB. First configure the WLAN via **(1) wifi & Web UI**. Then switch to **(2) swarm configuration**:

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

Now add this controller to the swarm with **(3) join another swarm**. To do this, you must enter the swarm name that you have assigned on the Kelda and the swarm pin. The Kelda controller must of course be switched on. 

Both controllers are now displayed on the Kelda's web UI. The second controller only displays its own inputs and outputs.

### Run a swarm based program

If both controllers are connected to the same swarm, you could use "Examples\ftSwarm\MotorSwitchSwarm":

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

Basically, the application is the same as [Your First Application](../MotorSwitch). There are only two changes:

- **#define remote 2** sets the serial number of your 2nd device. Please change the serial number to your 2nd device serial number.
- **FtSwarmMotor( remote, FTSWARM_M2 );** now uses the remote device serial number instead of the local serial number.


### What happens, if the 2nd controller isn't online?

Start the serial monitor and unplug the 9V power supply from the second device. Restart the first one. 
With **FtSwarmMotor( remote, FTSWARM_M2 );** you will get the debug output **Waiting on device**. Both RGB leds of this controller will be blue.
The firmware waits for the motor joining the swarm.
Add the 9V power supply again. Once the second device is started, your application will continue.
