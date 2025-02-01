---
title: PlatformIO with VSCode
layout: category
lang: en
classes: wide
sidebar:
    nav: manual-en
---
### Installation

Download and install the IDE [Visual Studio Code](https://code.visualstudio.com/)

Download and install the latest version of [PlatformIO](https://platformio.org/install/ide?install=vscode).

If you are a VS Code beginner, read the [quick start guide](https://docs.platformio.org/page/ide/vscode.html#quick-start)

Create a new PlatformIO project (use the home button in VS Code's purple status bar)

Board: **Espressif ESP 32 Dev Module**
Framework: **Arduino Framework**

Wait for VSCode setting up your project.

Depended on your ftSwarm Hardware, change the content of `platformio.ini` to the following content:


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



### Writing Code

Start writing your code. Use the following elements of the blue statusbar:

<style>
img { vertical-align: middle;important! }
</style>

- ![Home](/assets/img/vs_home.png) opens platformIO home. 
- ![build](/assets/img/vs_build.png) builds your software.
- ![upload](/assets/img/vs_upload.png) uploads/flashes your software.
- ![clean](/assets/img/vs_clean.png) cleans up your cached files.
- ![serial](/assets/img/vs_serial.png) opens the serial monitor.
- ![terminal](/assets/img/vs_terminal.png) opens a terminal.
- ![switch](/assets/img/vs_switch.png) switches between your projects.
