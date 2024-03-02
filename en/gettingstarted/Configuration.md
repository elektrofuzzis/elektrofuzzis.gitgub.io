---
title: Configuration
layout: category
lang: en
classes: wide
sidebar:
    nav: gettingstarted-en
---
Your controller needs some settings, e.g. a wifi profile or swarm parameters. Some settings have already been used in the tutorial. This chapter describes all configuration options in detail.

To configure the controller, the "Configuration Menu" can be started in the standard firmware at any time. For this purpose, a terminal program must be connected and any key pressed. The configuration menu can be started by

```cpp
firmware();
```

at any time in your own code.

<hr>
### Main Menu

**Main Menu** is the top level of the configuration menus. **(0) exit** terminates the configuration mode, using the standard firmware the controller will reboot afterwards. If the **Main Menu** was called with **ftSwarm.setup();** from a program, program will just continue.

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

The *ftSwarmControl* has an additional menu item for setting the display type and calibrating the joysticks.

<hr>
### Wifi & Web UI

In this area, the WLAN settings are made and the status page of the controller is configured.

```
***** Wifi & WebUI *****

hostname:           ftSwarm100
ip-address:         192.168.4.1

(1) wifi:           AP-Mode
(2) SSID:           ftSwarm100
(3) Password:       *****
(4) Web UI:         on
(5) ftPixels in UI: 2
```

To form a swarm, the individual controllers need to communicate with each other. Usually they use wifi - ftSwarmRS controllers could communicate additionally via RS485.

In addition, the status page of the controllers is called up via wifi.

Use **wifi** to select the type of wifi: 
- CLIENT-MODE uses an existing WLAwifiN. As a rule, this is the wifi of your internet router.
- AP-MODE does not need a router, a ftSwarm controller provides its own wifi network.
- OFF turns wifi off (ftSwarmRS only). This option reduces power consumption significantly.

If a wifi is already available, you should definitely use it. Select CLIENT-MODE and enter access data using **SSID** and **password**. Save the data by **exit** in the NVS. The controller will boot automattically and connect to your wifi afterwards.

Using AP-MODE is a little bit tricky:
- Select one controller and switch to AP-MODE there. With **SSID** you give the wifi a name. Due to restrictions of espressif, wifis in AP-MODE are always open. There is no password is required.
- In addition, you need to use option **wifi channel** to select the wifi channel. 
- All other controllers are set to CLIENT-MODE. Use the SSID above; set an empty password.
- Never put the Kelda in AP-MODE. As described in the tutorial, this will cause some problems during flushing your program.
- The AP-MODE has a high power consumption, the network is open for everyone (it has no password) and the transmission range is very limited.

The option **off** can only be set on the ftSwarmRS. In this case your swarm must communicate completely via RS485.

You share the wifi channels with the surrounding wifis. Therefore it is important to select the "right" channel. The ESP32 processors use the 2.4 GHz band. This band is divided into 11 channels, with adjacent channels overlapping. If two adjacent channels are used by a WLAN, they will interfere with each other. For this reason, it is best in the 2.4 GHz band if all WLANs only use channels 1, 6 and 11. Optimally, there is one unused channel. If this is not available, use an already used channel whose neighboring channels are not in use. You can see which channels are already in use on most Internet routers. With the app [wifiman](https://play.google.com/store/apps/details?id=com.ubnt.usurvey&hl=de&gl=US&pli=1) you can also analyze this via your smartphone.
{: .notice--info}

The last two options define the behavior of the status page.

- **WebUI: on/off** enables or disables the controllers status page.
- **Show X ftPixels in UI** defines the number of ftPixels which are displayed on the status page. It's used in the menu "Alias Names" as well. This value has no side effekt on the programming of ftPixels via the port number, all ports **FTSWARM_LED1** to **FTSWARM_LED18** can always be addressed.

<hr>
### Swarm Configuration

Within this menu, your swarm is formed. Before you can form a swarm, all controllers need be able to communicate with each other. For this purpose, all controllers need either be logged into the same wifi profile or connected via RS485.

The shown information depends on the controllers mode. A Kelda screen will be like:

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
In the Kelda mode, the Kelda shows all swarm members including herself. This list is stored in the Kelda's NVS storage. "NW Age" shows the time difference in ms, since the Kelda received the last status of a remote controller.

Every controller sends its status every 25 ms. Since there could be dropped packets, everyting less than 100ms is "online".

The Kelda's NW age value shows the elapsed time since the last reading of her sensors. 

A swarm member shows less options:

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

**swarm communication** sets the medium which the swarm uses to communicate.
- **wifi**: all controllers use wifi.
- **RS485**: all controllers user RS485. This option is available on ftSwarmRS only. A mixed mode wifi/RS485 isn't possible. 

**swarm speed** sets the communication speed in RS485 mode. 4 is the highest speed, allowing up to 32 controllers and a max. of 50 m cabling. If you're running into cable length problems, reduce the speed value step by step. 0 can drive up to 4.000m, but with a max. of 4 controllers.

**create a new swarm** is creates a new swarm and invokes Kelda mode at this controller . The new swarm's name and PIN are requested. Subsequently, this controller is the first and only controller within the new swarm.

**join another swarm** is used to join an existing swarm. Swarm's name and PIN are requested. Since the controller will try to connect to the swarm, the Kelda of the swarm must be online. If you choose this option on a Kelda, it will destroy it's own swarm and join the new one.

**invite a controller to my swarm** asks another controller to join my swarm. The asked controller will accept the request, if the controller is not connected to other controllers in a swarm.

**reject a controller from my swarm** will kick the listed controller out of my swarm.

<hr>
### Alias Names Settings

With this menu the ports alias names could be set. Named IO ports could be addressed via their name instead of the port number. Read [Alias Names](../gettingstarted/MotorSwitchAlias/) in the turorial for a detailed explanation.

To assign an alias name to an IO port, select the number of the desired IO. The name can be up to 30 characters long and must not contain spaces.

Within your swarm, all alias names must be unique. This is not checked during configuration since not all controllers in the swarm may be online. If a name is assigned to multiple ports, it is a coincidence which IO port is addressed when using the alias name.
{: .notice--info}

<hr>
### Factory Reset

This menu item resets the controller to factory settings. Since confidential information like wifi parameters are stored in the flash memory, you should reset a controller to factory settings before passing it on to third parties.

<hr>
### Remote Control Settings

With this menu a swarm can be programmed without a line of code. Therefore the used IO ports get alias names, afterwards they are addressed by the ftSwarmControl. For this purpose events are defined on buttons and joysticks to control the IO ports.

A detailed description is available at [Remote control](../gettingstarted/RemoteControl/).

<hr>
### Extention Port

The controllers have an extension port to which external hardware can be connected. 

Unlike the other connections on the controller, this connection is not protected against overvoltage or reverse polarity.

**ftSwarm:** The extension port is the connector strip on the top of the controller. 
- The optional MC6040 gyro can be connected to this port. 
- Alternatively, the port can be operated as an I²C bus (as a master or slave). 
- As a third option, the two IO pins can be switched as logical "motor outputs". Please note that these are pure GPIO pins and cannot switch a load. Additional external power drivers are required to connect motors, relays or lamps.

**ftSwarmRS:** The extension port is the 4-pin connector on the top of the controller.
- The port can be operated as an I²C bus (as master or slave). 
- As a second option, the two IO pins can be switched as logical "motor outputs". Please note that these are pure GPIO pins and cannot switch a load. To connect motors, relays or lamps, you will need additional external power drivers.    

The internal gyro of the ftSwarmRS uses its own I²C bus.

**ftSwarmControl**: 
The port can only be operated as an I²C bus. As the OLED display and the optional gyro are also connected to this bus, it can only be operated in master mode. In contrast to the other two controllers, both 3.3V and 5V sensors can be connected.

**Mode** defines the operating mode of the extension port.
- **off** switches the port off.
- **I2C master** switches the port as an I²C bus. The controller is the bus master. Use this option if you want to connect I²C sensors.
- **I2C slave** also switches the port as an I²C bus. In this case, the controller is the slave. This function can be used, for example, to exchange data with a TXT controller.
- **Gyro MCU6040** activates the optional gyro for *ftSwarmControl* or *ftSwarm*.
- **Outputs** is only possible with *ftSwarm* and *ftSwarmRS*. The two IO pins of the extension port can then be addressed as motor outputs by the software. The IO pins then supply a PWM signal corresponding to the set speed value of the motor output. Please note that the IO pin only supplies a 3.3V logic level and cannot switch any actuators without additional hardware.

**Gyro** enables/disables the gyro. Enable it only, if you actually want to use it in the application. Unused gyros have an unnecessary power consumption and a high communication need in the swarm.

**I2C Address** sets the I²C address of the controller in SLAVE mode. This option is not available in MASTER mode.

<hr>
### ftSwarmControl

The ftSwarmControl has two device specific settings.

**Display Type**: Depending on the used OLED display the firmware needs some differnt parameters. The first ftSwarmControls need display type 0, the newer ones type 1. If the display of the ftSwarmControl does not work, choose the other value.  

**Calibrate Joysticks**: calibrates zero position of the joysticks.


