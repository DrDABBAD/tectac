---
title: Garden safari with an ESP32
date: 2017-09-12 00:00:00 +0300
description: Plans for building webcams with ESP32 and NVIDIA # Add post description (optional)
img: ./how-to-start.jpg # Add image post (optional)
tags: [ESP32 Programming, IOT] # add tag
---

ESP32 a low-cost & low-power device, with inbuilt Wi-Fi module MCU, got into the top 10 emerging tech skills 2020, competing with Software Technologies. [Source : forbes.com] so is this an indicator its worth using in your next the Internet of Things project?.

## transport layer

Transport Layer Security (TLS) version 1.2 is the de-facto standard used on the web for secure connections including banking and financial institute. ESP32 is one of the MCUS that support it.

## Devices available


## Devices

Difference between Firmware and filesystem.



## breaking project in to steps.

Part I - Connect your device (ESP32) to  cloud.
Part Ia - Connect your device (ESP32) to  Nvidia jetson.
Part II - Use Device Shadow Service (AWS IoT) to control ESP32 inbuilt led using MQTT client.
Part III - Create a secure web client hosted in Node-RED to control ESP32 inbuilt led.
Part IV - The Real Deal: Create an automated system to connected to the web using [], an ESP32 board and a [].

## Firmware updater (cloud)

The new word is OTA update (Over the air)
SEE [Over-the-air_programming](SEE https://en.wikipedia.org/wiki/Over-the-air_programming)
with ESP32 two ways wen and arduino software.

How does it work in layman's terms?

**prerequisite tasks**

Create an MCU app, compile to bin file place in update directory within a server app.

The factory image in ESP32 doesn’t have an OTA Upgrade capability. So, you need to load the OTA firmware on the ESP32 through serial interface first.

0. Create a server program
1. Create client to get the bin file upload serially.
2. MCU device polls for update flag or Server push
3. Update the module depending to the latest version number

But how is the bin app started /installed ?

Does ESP32 support websockets signalr etc?

### Example code for Azure firmware update
https://docs.microsoft.com/en-us/azure/iot-hub/tutorial-firmware-update

## Wifi over air security

SSID and password


## Connecting to IOTHub

1. Use Azure portal
    a. Create IOTHub
    b. add device
    c. generate symmetric key

### Generate SAStoken

Description of this process is here.
    (https://docs.microsoft.com/azure/iot-hub/iot-hub-dev-guide-sas?tabs=node?WT.mc_id=AZ-MVP-5003764)
    (https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az_iot_hub_generate_sas_token?WT.mc_id=AZ-MVP-5003764)
## resources

[OTA expressif docs](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/system/ota.html)
[OTA 8266](https://arduino-esp8266.readthedocs.io/en/2.6.3/ota_updates/readme.html)
[OTA ESP32](https://lastminuteengineers.com/esp32-ota-web-updater-arduino-ide/) No polling.
[ESP32 OTA (Over-the-Air) Updates – AsyncElegantOTA] (https://randomnerdtutorials.com/esp32-ota-over-the-air-arduino/)
[resilient over-the-air update solution](https://techcommunity.microsoft.com/t5/internet-of-things/how-to-build-a-resilient-over-the-air-update-solution/ba-p/2163991)
[OTA at scale Azure IOT](https://azure.microsoft.com/en-gb/blog/azure-iot-automatic-device-management-helps-deploying-firmware-updates-at-scale/)
[ESP32 nanoframework Clifford Agius](https://techcommunity.microsoft.com/t5/internet-of-things/connect-an-esp32-to-azure-iot-with-net-nanoframework/ba-p/2731691)
[wildernesslabs](https://store.wildernesslabs.co/products/meadow-f7)
[ESP32 nanoframework](https://www.cliffordagius.co.uk/post/connectesp32toiothub/)

[Azure ESP ](https://docs.microsoft.com/en-us/samples/azure-samples/esp-samples/esp-samples/)

### Kit
(https://store.wildernesslabs.co/products/meadow-f7)