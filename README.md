# ESP32_AWS_Setup

## This is helper to setup ESP32-AWS service and run first MQTT Test. It takes two evening to examine and googling to overcome all issues

## Prerequires:
* Ubuntu 18.04
* All utilities:
> sudo apt-get install git wget libncurses-dev flex bison gperf python python-pip python-setuptools python-serial python-cryptography python-future python-pyparsing cmake ninja-build ccache


### Steps:
* Amazon provide own ESP32 board with crypto-chip. But - this is not necessary. 
Any ESP32 board is OK. My board named **ESP32-WROOM32-D**. But at this setup we will use **esp32_devkitc** instead
* Clone https://github.com/aws/amazon-freertos
* Run 
> vendors/espressif/esp-idf/install.sh
> 
    * There was issue: **no such option: --no-warn-script-location**
    * Solution: delete all at folder: 
> /home/user/.espressif/python_env
> 
    * Anoter issue: **ERROR: Board is not supported: vendor.board**
    * Solution - run:
>    cmake -DVENDOR=espressif -DBOARD=esp32_devkitc  -DCOMPILER=xtensa-esp32 -S . -B build -GNinja
>    
* Run
> source vendors/espressif/esp-idf/export.sh

* After that build started. Run from root folder because test predefined there as **CONFIG_CORE_MQTT_MUTUAL_AUTH_DEMO_ENABLED** there:
> /home/user/esp/AWS/amazon-freertos/vendors/espressif/boards/esp32/aws_demos/config_files/aws_demo_config.h

* Setup AWS. Follow the best article [The non-primitive approach of Amazon: How AWS IoT meets IoT challenges](https://indeema.com/blog/the-non-primitive-approach-of-amazon--how-aws-iot-meets-iot-challenges) and use official site [Getting started with the Espressif ESP32-WROOM-32SE](https://docs.aws.amazon.com/freertos/latest/userguide/getting_started_esp32wroom-32se.html)
* What you should have after pass all AWS tutorial:
    *  IAM user
    *  IAM password
    *  Account ID (12 digits)
    *  Access key ID
    *  Secret access key
    *  Default region name
    *  certificat for thing (download)
    *  public key (download)
    *  private key (download)
* Pass through but never used: [Installing, updating, and uninstalling the AWS CLI version 2 on Linux
](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
* Run at Chrome file **/home/user/esp/AWS/amazon-freertos/tools/certificate_configuration/CertificateConfigurator.html**
    * UI dialog asks certificat and key files and generates .h file
* Install:
> pip install tornado nose
> 
> pip install boto3
> 
* Edit file **/home/user/esp/AWS/amazon-freertos/tools/aws_config_quick_start/configure.json** :
> {
>   "afr_source_dir":"../..",
>   "thing_name":"",
>   "wifi_ssid":"",
>   "wifi_password":"",
>   "wifi_security":"eWiFiSecurityWPA2"
>}
>






