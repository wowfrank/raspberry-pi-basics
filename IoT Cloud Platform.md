此处将对IoT的各种云平台进行对比和分析。

Platform | Data store | Services integration | Data visualization | SDK API | Event/rule mngt | Free account
--- | --- | --- | --- | --- | --- | ---
Temboo | No | Yes (about 2000 choreos) | No | Yes | Yes | Yes
Carriots | Yes | Yes(Email, SMS, Twitter) | No | Yes | Yes | Yes
NearBus\*	| No	| No	| No	| Yes	| Yes	| Yes
**_Ubidots_**	| Yes	| Yes(Email, SMS, Twitter, Webservvice)	| Yes	| Yes	| Yes\*\*	| Yes

IoT平台将来将成为一个竞争核心，那么到底什么是IoT平台？

###### 首先来看看一个完整的IoT生态体系是什么样的

1. 硬件，例如感应器或者摄像头，这些硬件从外部环境收集相关数据；
1. 连接，所有的硬件需要通过某种途径相互连接以传达信息；
1. 软件，部署在云端的软件，收集、处理、并发送相应信息；
1. 用户界面，用户通过界面来控制这整个系统；

而IoT平台就是上面提到的软件。

###### IoT平台的主要功能在于：

1. 连接所有硬件；
1. 处理各种通讯协议；
1. 提供安全以及认证功能；
1. 收集、分析、处理及可视化数据；
1. 集成其他页面服务；

###### 什么情况下需要用到IoT平台？

当你没有足够的资金和技术团队去自己创建一套可以处理IoT系统的软件的时候，你可以考虑使用IoT平台；

然而，长期的付费却会是一个让人头疼的事情，你需要考量的仅仅是时间和金钱之间的关系。

###### 以DeviceHive这个IoT云平台为例子

这里记录一下如何安装远程控制温度感应器和LED。所需材料如下：

* Raspberry Pi 1 Model B, 2, 3
* DS18B20感应器
* LED
* 510ohm电阻（给LED）和4.7k ohm电阻（给DS18B20）
* 电路板

<img src="Images/80995d1-dsc.png" title="电路图" width="600px">

##### 好，开始配置Raspberry Pi

1. 下载Raspbian镜像，安装
1. 电源5V
1. 连接电脑和RASPBERRY PI
1. 连接LED/感应器（如图）
1. 启用1-wire kernel模块
    1. echo "dtoverlay=21-gpio" | sudo tee -a /boot/config.txt
    1. sudo reboot
    1. sudo modprobe w1-gpio && sudo modrobe w1_therm(optional)
1. 找到感应器的文件： ls /sys/bus/w1/devices/ （类似 28-00000393268a)
1. 测试： cat /sys/bus/w1/devices/28-00000393268a/w1_slave
   会返回如下结果：
   
     pi@raspberrypi:~ $ cat /sys/bus/w1/devices/28-0314685df7ff/w1_slave 
     8f 01 55 00 7f ff 0c 10 a0 : crc=a0 YES
     8f 01 55 00 7f ff 0c 10 a0 t=24937

##### 在Raspberry Pi上安装DeviceHive

1. 用ssh连接到你的RasPi
1. 下载最新的python库： 
   ```bash
   sudo pip install devicehive
   ```
1. 复制下面的代码: 
   ```bash
   wget https://github.com/devicehive/devicehive-python/raw/stable/examples/raspi_led_thermo.py
   ```
1. 用vim或者nano打开下载下来的文件，修改'SERVER_REFRESH_TOKEN'的值（在Admin版面的refresh token值）
1. 运行： python raspi_led_thermo.py

##### 访问设备

1. 运行代码后，你可以发现设备；
1. 也可以远程开关；

Open source IoT Platform Comparison Table

IoT Software Platform	| Device management?|	Integration	| Security	| Protocols for data collection	| Analytics	| Support for visualizations?	| DB
--- | --- | --- | --- | --- | --- | --- | --- 
<font color='orange'>Kaa IoT Platform | Yes | Portable SDK available to integate any particular platfrom, REST API	| Link Encryption (SSL), RSA key 2048 bits,  AES key 256 bits | 	MQTT, CoAP, XMPP, TCP, HTTP	| Real time IoT Data Analytics and Visualization with Kaa, Apache Cassandra and Apache Zappelin	| Yes	| MongoDB, Cassandra, Hadoop, Oracle NoSQL</font>
SiteWhere	| Yes	| REST API, Mule AnyPoint, and more	| Link Encryption (SSL), Spring Security	| MQTT, AMQP, Stomp, WebSockets, and direct socket connections	| Real-time analytics (Apache Spark)	| No	| MongoDB, HBase , InfluxDB
ThingSpeak	| No	| REST and MQTT APIs	| Basic Authentication	| HTTP	MATLAB | Analytics	| No	| MySQL
DeviceHive	| *Unknown	 | REST AP, MQTT APIs	| Basic Authentication using JSON Web Tokens (JWT)	| REST API, WebSockets or MQTT	| Real-time analytics (Apache Spark)	| Yes	| PostgreSQL ,SAP Hana DB
Zetta	| No	| REST APIs	| Basic Authentication	| HTTP	| Using Splunk	| No	| Unknown
Distributed Services Architecture (DSA)	| NO	| REST APIs	| Basic Authentication	| HTTP	| No	| No	| ETSDB – Embedded Time Series
Thingsboard.io	| Yes	| REST APIs	| Basic Authentication	| MQTT, CoAP and HTTP	| Real time analytics(Apache Spark, Kafka)	| No	| Cassandra
Thinger.io	| Yes	| REST APIs	| Link Encryption (SSL/TLS) and basic authentication	| MQTT, CoAP and HTTP	| Yes	| No	| MongodB
<font color='orange'>WSo2	| Yes	| REST APIs	| Link Encryption (SSL) and basic authentication	| HTTP, WSO2 ESB, MQTT	| Yes, WSO2 Data Analytics Server| 	Yes	| Oracle, PostgreSQL, MySQL, or MS SQL</font>

*Unknown means we are not able to find that.
