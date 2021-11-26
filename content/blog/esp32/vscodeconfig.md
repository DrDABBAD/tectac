



##  Azure IoT Device Workbench

Install  [ardunino](https://www.arduino.cc/en/Main/Software)


In vscode:

0. Add the extension Azure IoT Device Workbench

1. Open File > Preference > Settings and add following lines to configure Arduino.
2. type Ardunino and open the seetings.json file search for ardunio
3. add  or ensure the following setting are in place

```json
    "arduino.path": "C:\\Program Files (x86)\\Arduino",
    "arduino.additionalUrls": "https://dl.espressif.com/dl/package_esp32_index.json"
```

4. Use F1 or Ctrl+Shift+P (macOS: Cmd+Shift+P) to open the command palette, type and select Arduino: Board Manager. Search for esp32 and install the latest version.




## Build project

Use F1 or Ctrl+Shift+P (macOS: Cmd+Shift+P) to open the command palette, type Azure IoT Device Workbench, and then select Open Examples.

Select ESP32 Arduino


Leave this here for know project to follow ...

## resources

[esp32 dev kit](https://docs.microsoft.com/en-us/samples/azure-samples/esp32-iot-devkit-get-started/sample/)
(https://docs.microsoft.com/en-us/samples/azure-samples/esp-samples/esp-samples/)
(https://docs.microsoft.com/en-us/azure/iot-hub/tutorial-firmware-update)
(https://techcommunity.microsoft.com/t5/internet-of-things/how-to-build-a-resilient-over-the-air-update-solution/ba-p/2163991)
(https://azure.microsoft.com/en-gb/blog/azure-iot-automatic-device-management-helps-deploying-firmware-updates-at-scale/)

https://raw.githubusercontent.com/espressif/esp-azure/master/README.md
https://www.espressif.com/en/products/devkits/esp32-azure-kit/overview
https://platformio.org/lib/show/5462/ESP32%20Azure%20IoT%20Arduino
https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html
