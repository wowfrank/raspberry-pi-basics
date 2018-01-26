###### 几个硬件区别和主要应用方:
- [x] Arduino Uno;

可以看作是一台微型控制器，是一台电脑系统的组成部分，在电子应用领域有着极强的优势。它并不需要特别的操作系统或者软件的支持来运行，仅仅物理连接后写几行简单的代码即可使用。

Arduino的优势：

* **简单** - 和传感器之类的设备间的通讯的代码更为简单；
* **稳健** - 即插即用，支持热插拔，无需开关机；
* **能耗** - 低电压，且可以使用电池供电；
* **价格** - 价格便宜很多；

**Arduino更适合那些重复性的场景；**
- [x] NodeMCU ESP8266;

带无线及网络功能的微型控制器，更适合收集各种传感器数据，然后发送给主机；
- [x] Raspberry Pi;

可以看作是一台微型电脑，拥有各种齐全的零件，可以安装各种操作系统，例如：Rasbian。

Raspberry Pi的优势：

* **强大** - 多任务同时运行，可从网页访问，可从互联网访问，其运行速度是ARDUINO的40倍；
* **网咯** - 拥有内置网卡，无需额外的设备和程序来添加网络功能；
* **无需电工专业知识** - 无需像Arduino那般学习专门的编程语言，也无需了解电器的具体参数；

**Raspberry Pi更适合复杂度相对较高的场景；**

对比

Parameters | Arduino Uno | Raspberry Pi B+ | ESP-8266
--- | --- | --- | --- 
Processor | ATMega328P | Quad-core ARM Cortex A53 | -
GPU | - | Broadcom VideoCore IV with 400 MHz | -
Operating Voltage | 5V | 5V | 3.3V
Clock Speed | 16MHz | 1.2GHz | 26MHz - 52MHz
system Memory | 2KB | 1GB | <45KB
Flash Memory | 32 KB | - | up to 128MB
EEPROM | 1KB | - | - | -
Communication Supported | IEEE 802.11b/g/n IEEE802.15.1 433RF BLE 4.0 via Shield | IEEE 802.11b/g/n IEEE802.15.1 433RF BLE 4.0 Ethernet Sierial | IEEE 802.11 b/g/n 
Development Environments | Arduino IDE | Any linux compatible IDE | Arduino IDE, Lua Loader
Programming Language | Wiring | Python C/C++ Java Scratch Ruby | Wiring, C, C++
I/O Connectivity | SPI I2C UART GPIO | SPI DSI UART SDIOCSI GPIO | UART, GPIO

###### 传感器主要有：
1. 温度和湿度传感器（Temperature & Humidity Sensor - DHT11）;
1. 瓦斯传感器（Gas Sensor - MQ2）;
1. <del>土壤适度传感器（Soil Moisture Sensor）;</del>
1. 人体热释电红外传感器（PIR Sensor）;
1. 微波传感器（Microwave Sensor）；
1. 射频识别读写器（RFID Reader - MFRC 522）;
1. 指纹识别器（Fingerprint Sensor)；
1. 声音传感器（Sound Sensor）；

``` php
<?php
   $today = 'wednesday';
   echo $today;
?>
```
