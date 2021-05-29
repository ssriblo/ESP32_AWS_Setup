# ESP32_AWS_Setup

## This is helper to setup ESP32-AWS service and run first MQTT Test. It takes two evening to examine and googling to overcome all issues

## Prerequires:
* Ubuntu 18.04
* All utilities 

### Steps:
* Amazon provide own ESP32 board with crypto-chip. But - this is not necessary. 
Any ESP32 board is OK. My board named **ESP32-WROOM32-D**. But at this setup we will use **esp32_devkitc** instead
* Clone https://github.com/aws/amazon-freertos
* Run vendors/espressif/esp-idf/install.sh
    * There was issue: **no such option: --no-warn-script-location**
    * Solution: delete all at folder: 
    ``` 
    /home/user/.espressif/python_env
    ```
    * Anoter issue: **ERROR: Board is not supported: vendor.board**
    * Solution - run:
    ```
    cmake -DVENDOR=espressif -DBOARD=esp32_wrover_kit -DCOMPILER=xtensa-esp32 -S . -B build -GNinja
    ```
* source vendors/espressif/esp-idf/export.sh

