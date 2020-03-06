Title: AIoT on the edge
Date: 2019-11-02
Category: Blog
Status: draft

### The Artificial Intelligence of Things (AIoT)

I spotted a nifty little board on Adafruit that promises facial recognition on chip! As it was $24.95 I added it to another order and now I have it in my hot little hands and want to do something with it.


[<img src="{static}/images/esp_eye.jpg" width="600">](https://www.adafruit.com/product/4095)


I find this a fascinating development in AI and ML. If you've ever tried facial recognition with neural networks, a thumb sized board that does it without sending data to be processed elsewhere is a bit mind blowing.

Anyway, it's arrived so I best get something going to try it out!


### Tutorials

I found some tutorials

[Maker-advisor](https://makeradvisor.com/esp-eye-new-esp32-based-board/)

[esp-who getting started]({static}/pdfs/espressif_esp-who)

[espressif docs](https://docs.espressif.com/projects/esp-idf/en/stable/get-started-cmake/index.html)

[acoptex.com](http://acoptex.com/project/10804/basics-project-86a-meet-the-espressif-esp-eye-development-board-v21-at-acoptexcom/#sthash.ZqunaSHs.dpbs)

# ESP-EYE Getting Started Guide

[[中文]](../../zh_CN/get-started/ESP-EYE_Getting_Started_Guide.md)

## What You Need

* 1 × ESP-EYE V2.1 board
* 1 × Micro USB cable
* 1 × PC with Windows, Linux or Mac OS

## Overview

ESP-EYE is an ESP32-based development board that integrates a digital microphone, an 8 MB PSRAM and a 4 MB flash, while also providing an external 2-Megapixel camera. These features make the board ideal for applications relating to face detection, face recognition and speech recognition. Besides, the board can also support image transmission over Wi-Fi and debugging through a Micro USB port, which enables the development of advanced AI solutions.

## Hardware Preparation

The list and figure below describe the key components, interfaces and functions of the ESP-EYE development board:

![ESP-EYE image]({static}/images/esp-eye_callout.png)

* **3D_PIFA Antenna**

	A 3D PIFA antenna. With the R14 resistor users can select the external IPEX antenna, whereas with the R15 resistor they can select the 3D antenna.

* **IPEX Connector**

	Used for connecting the external IPEX antenna. With the R14 resistor users can select the external IPEX antenna, whereas with the R15 resistor they can select the 3D antenna.
	
* **ESP32 Chip**

	A 2.4 GHz Wi-Fi and Bluetooth combo chip.
	
* **Crystal Oscillator**

	Provides an external clock to ESP32.

* **Flash & PSRAM**

	Provides memory for storing applications.

* **CP2102 USB-to-UART Chip**

	Converts the USB signals to UART signals.

* **USB Port**

	Provides power supply to the whole system.

* **LDO Power Supply**

	Provides the required power supply to the ESP32 chip, camera and LED indicators.

* **Side Tactile Button**

	A function key.

* **Top Tactile Button**

	Reset/Boot button. We recommend that you do not configure this button for other uses.

* **LED Indicators**

	The board has a red and a white indicator. Different flashing combinations of the red and white indicators reflect the different statuses of the board, e.g. waking up, networking, face detection, face recognition, face enrollment and face recognition.

* **Camera**

	An external 2-Megapixel camera module for face detection, face recognition and Face ID enrollment.

*  **Camera Connector**

	Used for connecting the external camera.

* **MIC**

	A digital microphone for voice control functions.

* **SPI Port**

	A reserved port for data transmission.






