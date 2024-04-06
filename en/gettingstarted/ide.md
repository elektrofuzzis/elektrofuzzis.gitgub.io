---
title: Install your IDE 
layout: category
lang: en
classes: wide
sidebar:
    nav: gettingstarted-en
---

There are different platforms and IDEs to write your C++ code. If you are a beginner please use the Arduino IDE as described below.

1. [Arduino](https://www.arduino.cc/)
   is the most common platform for DIY projects. It started 2005 as a project to design an open source microcontroller board, 
   today the platform supports all common types of microcontrollers. The Arduino environment is an IDE with integrated framework for embedded systems.

2. [PlattformIO](https://platformio.org)
   is a framework to develop embedded systems, too. This framework is not part of an IDE like Arduino and you could choose among different editors/IDEs. In the first time, PlatformIO is a bit more complicated than Arduino IDE, but it has many advantages. See [PlattformIO & VSCode](/en/gettingstarted/PlatformIO.md) in advanced for more information.

The are two Arduino IDE versions available. Supported versions are 1.8.19 or the latest 2.x version. Version 1.8.19 is faster on older PCs.

There are several necessary steps to installation install your environment. The instructions refer to version 2.x of the IDE. The configuration steps in the old version are the same, the menu navigation is slightly different.

### 1. Download IDE

Download and install Arduino IDE from [arduino.cc](https://www.arduino.cc/en/software).

### 2. Add Boardverwalter-URLs

Open *File/Preferences* in your Arduino IDE.

Please add at *additional boards manager URLs*:
   - https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   - https://raw.githubusercontent.com/harbaum/ftduino/master/package_ftduino_index.json

Please goto *Tools/Board/Boards Manaager* and install the newest version of *esp32 by espressif systems*. If you just see 1.x-version please check the added URLs above.

### 3. Install Libraries

You ftSwarm Firmware needs some additional 3rd-party-libraries. You could install them using *Tools\Manage libraries":

- *Adafruit GFX Library* Version 1.10.12 or newer
- *Adafruit SSD1306* Version 2.5.3 or newer
- *FastLED by Daniel Garcia* Version 3.4.0 or newer
- *STM32duino LSM6DSR by SRA* Version 2.1.0 or neuer

### 4. Install ftSwarm Libraries

Dependend on your ftSwarm Hardware, you need to download the belonging library at <a href="https://github.com/elektrofuzzis/ftSwarm/releases">github</a>:

|:---:|:---:|:---:|:---:|
| <img alt="ftSwarmRS" src="/assets/img/ftSwarmRS.png" width="100"><br>ftSwarm-rs.zip | <img alt="ftSwarmControl" src="/assets/img/ftSwarmControl.png" width="100"><br>ftSwarm-control.zip | <img alt="ftSwarmXL" src="/assets/img/ftSwarmXL.png" width="100"><br>ftSwarm-xl.zip | <img alt="ftSwarmJST" src="/assets/img/ftSwarm.png" width="100"><br>ftSwarm-jst.zip | 
| <img alt="ftSwarmCAM" src="/assets/img/ftSwarmCAM.png" width="100"><br>ftSwarm-cam.zip| <img alt="ftSwarmPwrDrive" src="/assets/img/ftSwarmPwrDrive.png" width="100"><br>ftSwarm-pwrdrive.zip| <img alt="ftSwarmDuino" src="/assets/img/ftSwarmDuino.png" width="100"><br>ftSwarm-duino.zip| |

ZIP-FIles are installed via *Sketch\Include Library\Add .ZIP Library*. You could install different ftSwarm libraries at the same time.

### 5. Board Configuration

Please set the correct board settings in *Tools*:

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
 
### 6. Compile & Upload:

Arduino programs are called sketches and are saved as *.ino* files. Only one sketch can be saved in a directory at a time, as the directory name must be identical to the sketch name.

<style>
img { vertical-align: middle;important! }
</style>

- ![build](/assets/img/arduino_compile.png) compiles your ketch.
- ![upload](/assets/img/arduino_upload.png) flashes the sketch at your controller.
- ![serial](/assets/img/arduino_serial.png) starts a serial console..

Checkout the tutorial's examples at *File/Examples/ftSwarm*.
