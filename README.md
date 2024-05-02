# UCSD Global TIES: ENG 100L Baja Solar Thermal Water

This repository contains the code that runs on our custom PCB with ESP32-S3 Arduino controller.

Below are the basic steps for setting up and compiling all necessary sources for the Arduino IDE to implement the program on the ESP32 controller.

Once the setup is complete, read on for details of how the code works and how to run the Baja Solar program.

## Basic Guide to Arduino Setup

Begin by setting up the Arduino IDE for use with the ESP32-S3. The easiest way to do this will be to install Arduino-ESP32 directly from the Arduino IDE, located at the following link:

```
https://www.arduino.cc/en/software
```

Choose the most recent stable download (probably will be v2.3.X or later).

Arduino allows installation of platform packages using Boards Manager, which are available on Windows, macOS and Linux.

Once the Arduino IDE is downloaded, start the program and open Preferences.

Here you will find a Settings menu, with an option to add "Additional Boards Manager URLs" at the bottom.

Enter the following release link into this field:

```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

Next, open `Boards Manager` from `Tools > Board Menu` and install `esp32` platform. 

After installing, return to Tools > Board Menu and select the `ESP32-S3` board after installation.

## Adding Libraries to Arduino IDE for Baja Solar program

In order for the program to compile successfully, the following additional libraries must be added to your Arduino IDE:

```
Wire
Adafruit_GFX
Adafruit_SSD1306
OneWire
DallasTemperature
WiFi
WebServer
```

At the beginning of the program code, you will see these libraries referenced as follows. This can potentially help debug issues in the case of the program failing - one thing to check should be that all libraries in your Arduino IDE are properly downloaded and installed.

```cpp
#include <Wire.h> 
#include <Adafruit_GFX.h> 
#include <Adafruit_SSD1306.h> 
#include <OneWire.h> 
#include <DallasTemperature.h> 
#include <WiFi.h> 
#include <WebServer.h>
```

To add these libraries, you can use the Library Manager in your Arduino IDE. 

Open the IDE and go to the `Sketch` menu. From there, navigate to `Library > Manage Libraries.`

Here you will find a list of all libraries that are already installed or ready for installation. Select and install all of the libraries listed above.

*Note: When the Arduino IDE upgrades itself, all files in Programs/Arduino (or the new folder where you installed the IDE) are deleted and a new folder is created with fresh content. Because of this, it is recommended that you ***only install libraries to the sketchbook folder so they are not deleted during the Arduino update process.****

## Setting Up the Hardware

Now that you have installed all the necessary dependencies in your Arduino IDE, you are ready to flash the ESP32-S3 controller with your code to run your program.

The ESP32-S2 board has 2 USB-C ports. One is labeled `COMM` and the other `USB`. 

When flashing program to the ESP32, you will use the port labeled `USB`. To run the program itself and begin receiving communications from the board, you will connect to the `COMM` port.

[]