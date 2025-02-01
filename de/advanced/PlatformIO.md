---
title: PlatformIO mit VSCode
layout: category
lang: de
classes: wide
sidebar:
    nav: manual-de
---
### Installation

Downloaden und installieren Sie die IDE [Visual Studio Code](https://code.visualstudio.com/)

Downloaden und installieren Sie die neueste Version von [PlatformIO](https://platformio.org/install/ide?install=vscode).

Als VSCode Neuling, empfiehlt es sich den [quick start guide](https://docs.platformio.org/page/ide/vscode.html#quick-start) zu lesen.

Erzeugen Sie ein neues PlatformIO Project (verwenden Sie den Home-Button in der lila VS Code's Status Bar)

Board: **Espressif ESP 32 Dev Module**
Framework: **Arduino Framework**

Warten Sie bis VSCode Ihr projekt erzeugt hat.

Abhängig von Ihrer ftSwarm Hardware muss nun die Datei `platformio.ini` geändert werden:

**ftSwarmRS:**

```ini
[env:firmware-rs]
platform =espressif32
board = esp32-s3-devkitc-1
board_build.mcu = esp32s3

lib_deps =
    elektrofuzzis/ftSwarm-rs

board_upload.flash_size = 4MB
framework = arduino

build_flags =
    -DARDUINO_EVENT_RUNNING_CORE=0
    -DARDUINO_RUNNING_CORE=1
    -DCORE_DEBUG_LEVEL=1

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


**ftSwarmControl:**

```ini
[env:firmware-control]
platform = espressif32
board = esp32dev
board_build.mcu = esp32
framework = arduino
lib_deps = 
	elektrofuzzis/ftSwarm-control

build_flags = 
	-DARDUINO_EVENT_RUNNING_CORE=1 
	-DARDUINO_RUNNING_CORE=0
	-DBOARD_HAS_PSRAM
	-mfix-esp32-psram-cache-issue
	-DCORE_DEBUG_LEVEL=0

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


**ftSwarmDuino:**

```ini
[env:firmware-duino]
platform =espressif32
board = esp32-s3-devkitc-1
board_build.mcu = esp32s3

lib_deps =
    elektrofuzzis/ftSwarm-duino

board_upload.flash_size = 4MB
framework = arduino

build_flags =
    -DARDUINO_EVENT_RUNNING_CORE=0
    -DARDUINO_RUNNING_CORE=1
    -DCORE_DEBUG_LEVEL=1

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


**ftSwarmPwrDrive:**

```ini
[env:firmware-pwrdrive]
platform =espressif32
board = esp32-s3-devkitc-1
board_build.mcu = esp32s3

lib_deps =
    elektrofuzzis/ftSwarm-pwrdrive

board_upload.flash_size = 4MB
framework = arduino

build_flags =
    -DARDUINO_EVENT_RUNNING_CORE=0
    -DARDUINO_RUNNING_CORE=1
    -DCORE_DEBUG_LEVEL=1

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


**ftSwarmXL:**

```ini
[env:firmware-xl]
platform =espressif32
board = esp32-s3-devkitc-1
board_build.mcu = esp32s3

lib_deps =
    elektrofuzzis/ftSwarm-xl

board_upload.flash_size = 4MB
framework = arduino

build_flags =
    -DARDUINO_EVENT_RUNNING_CORE=0
    -DARDUINO_RUNNING_CORE=1
    -DCORE_DEBUG_LEVEL=1

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


**ftSwarm:**

```ini
[env:firmware-jst]
platform = espressif32
board = esp32dev
board_build.mcu = esp32
framework = arduino
lib_deps = 
	elektrofuzzis/ftSwarm-jst

build_flags = 
	-DARDUINO_EVENT_RUNNING_CORE=1 
	-DARDUINO_RUNNING_CORE=0
	-DBOARD_HAS_PSRAM
	-mfix-esp32-psram-cache-issue
	-DCORE_DEBUG_LEVEL=0

monitor_filters = esp32_exception_decoder
monitor_speed = 115200
upload_speed = 921600
board_build.partitions = no_ota.csv
```


### Programme schreiben

Sie können nun mit dem Schreiben Ihres Programms beginnen.

<style>
img { vertical-align: middle;important! }
</style>

- ![Home](/assets/img/vs_home.png) öffner PlatformIO Home. 
- ![build](/assets/img/vs_build.png) compiliert Ihr Programm.
- ![upload](/assets/img/vs_upload.png) flashed Ihr Programm auf den Controller.
- ![clean](/assets/img/vs_clean.png) löscht gecachte Dateien.
- ![serial](/assets/img/vs_serial.png) startet den seriellen Monitor.
- ![terminal](/assets/img/vs_terminal.png) startet ein Terminal.
- ![switch](/assets/img/vs_switch.png) schaltet zwischen Ihren Projekten hin und her.
