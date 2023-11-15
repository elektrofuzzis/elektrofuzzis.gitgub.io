---
title: Version History
layout: category
lang: en
classes: wide
sidebar:
nav: advanced-en
---
### Version 0.5.0 11/2023

In the previous versions, the controller on which the control program was started with ``ftSwarm.begin`` was the Kelda.
However, this led to some communication problems.
Therefore, the Kelda controller is now already defined at firmware level.

(1) Kelda upgrade

- First carry out the upgrade on your Kelda controller and install the normal firmware there.
- Switch to the interactive firmware menu. In **(2) swarm configuration**, use the **(1) Kelda** menu item to set this controller to Kelda mode.
- After restarting the Kelda, it will no longer automatically switch to the configuration menu. Enter the command ``setup``.
- Now create a new swarm with **(3) create a new swarm**.

(2) Upgrade swarm members

- Now carry out the upgrade on all Swarm members in turn by installing the new firmware version.
- In the interactive firmware menu, select **(2) swarm configuration** and join the new swarm with **(3) join to existing swarm**.

(3) Upgrade your existing programs

- Please note that ftSwarm, ftSwarmRS and ftSwarmControl now have their own libraries. Use the corresponding include statements in your project - ftSwarmRS ``#include <ftSwarmRS.h>``, ftSwarm ``#include <ftSwarm.h>``, ftSwarmControl ``#include <ftSwarmControl.h>``  
- Previously, the Kelda was defined by starting the swarm with ``ftSwarm:begin``. This is now done at firmware level, as described above. If you now run your program on a swarm member, you will receive an error message and the swarm will stop.
- The optional parameter ``verbose`` at ``ftSwarm:begin`` determines whether detailed information is to be output when the swarm is started.

The swarm members in the swarm only "know" their Kelda. This is why the swarm members only display swarms with 2 members.
The Kelda must of course know all swarm members and displays the correct number of controllers in the swarm in the firmware.

In the Web UI, the entire Swarm is only displayed on the Kelda. The other controllers only show their own status.

**New in this version:**

- Support for ftSwarmRS.
- Python integration [ftSwarm.py](https://bloeckchengrafik.de/ftswarm.py/)
- Direct control of the IOs in the CLI via the serial interface. For detailed information, type ``help`` in the interactive mode of the serial port.
- New web UI.  
- The ftSwarm protocol has been improved. Therefore upgrade to version 0.5.0 for all controllers in Swarm!
- Many stability bug fixes.

### Version 0.4.2 11/2022

- new OLED type support

### Version 0.4.1 11/2022

- remote motors couldn't handle negative speed values
- remote led's didn't work properly
- supress "ghost" toggles on ftSwarmControl buttons during startup
- ESP Board defintion V2.0.5 is stable now. Future development will be based on 2.0.5.
- Arduino IDE 2.0.2 is stable now.

### Version 0.4.0 07/2022

Please use ESP32 Board definition V2.0.4. New 2.0.5 isn't stable with ftSwarm.

- Servo's alias name is now saved in NVS.
- Support of 2 internal and 16 external RGB LEDs.
- Showing the IP address correctly.
- Negative speed switches rotation movement.
- wifi won't go to sleep mode
- Changed AP mode parameters

### Version 0.3.0 07/2022

- [Remote control:](../setup/configure_your_device/remote_control) Use your swarm without any line of code.
- [Event Controlled Programming.](../cpp/YourFirstApplication/EventControlled)
- Bugfix: Speedup sensor readings.

### Version 0.2.0 05/2022

- Redesign of ftSwarm Web-UI.
- Support of ftSwarmControls OLED display.
- Up to 14 ftRGBLeds could be connected externally.
- Detailed swarm & device status at ftSwarmControl's OLED display.
- New class FtSwarmLightBarrier.
- New class FtSwarmXMMotor.
- New class FtSwarmValve.
- New class FtSwarmCompressor.
- New class FtSwarmBuzzer.
- Extended swarm communication using flexible packet sizes.
- Bugfix: Sending alias names to Kelda.

### Version 0.11.0 04/2022

Some bugfixes.

### Version 0.10.0 03/2022

First official version.