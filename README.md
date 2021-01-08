# homebridge-mqtt-sonoffrf-receiver-2

Get Motion Sensor status via MQTT in Homebridge using [Sonoff RF Bridge 433](https://www.itead.cc/sonoff-rf-bridge-433.html) with [TasmOTA firmware](https://github.com/arendst/Sonoff-Tasmota/wiki).
Motion sensor is activated when received RF code matches for rfcode or RF key stored in Sonoff RF Bridge. Open Sonoff RF Bridge console to read out received RF codes as hexadecimal values in DATA field. Use these values in rfcode parameter or use rfkey if you have already defined RF codes in Sonoff RF Bridge. Value 'any' will activate the sensor if any RF code received. Use rfcodeon and rfcodeoff parameters if your sensor sends both on and off states.
Sensor can be [motion sensor](https://www.itead.cc/sonoff-rf-bridge-433.html) or [RF button](https://www.aliexpress.com/item/86-Wall-Panel-Wireless-Remote-Transmitter-1-2-3-Channel-Sticky-RF-TX-Smart-For-Home/32793117889.html?spm=a2g0s.9042311.0.0.nUq3pZ), [Contact sensor]( https://www.aliexpress.com/item/4000127476693.html?gps-id=pcDetail404&scm=1007.16891.96945.0&scm_id=1007.16891.96945.0&scm-url=1007.16891.96945.0&pvid=f3503857-0500-4c3b-bf09-8d957ea48bae&_t=gps-id:pcDetail404,scm-url:1007.16891.96945.0,pvid:f3503857-0500-4c3b-bf09-8d957ea48bae,tpp_buckets:668%230%23131923%235_668%23888%233325%232_668%232846%238110%231995_668%232717%237564%23616__668%233374%2315176%23759) or any other RF sensor.

Installation
--------------------
    /* you might need to issue a "sudo su -" when you get errormessages during install!!! */
    sudo npm install -g https://github.com/BluP62/homebridge-mqtt-sonoffrf-receiver-2


Sample HomeBridge Configuration
--------------------
    {
        "accessory": "mqtt-sonoffrf-receiver-2",
        "url": "mqtt://localhost",
        "topic": "tele/rf-bridge/RESULT",
        "username": "username",
        "password": "password",
        "rfcodeon": "2E1A11",
        "rfcodeoff": "2E1A12",
        "rfcodelowbattery": "2E1A14",
        "accessoryservicetype": "ContactSensor",
        "name": "Contact Sensor"
    },
    {
        "accessory": "mqtt-sonoffrf-receiver-2",
        "url": "mqtt://localhost",
        "topic": "tele/rf-bridge/RESULT",
        "username": "username",
        "password": "password",
        "rfcode": "2E1A21",
        "ondelay": "30000",
        "rfcodelowbattery": "2E1A22",
        "accessoryservicetype": "MotionSensor",
        "name": "Motion Sensor"
    },
    {
        "accessory": "mqtt-sonoffrf-receiver-2",
        "url": "mqtt://localhost",
        "topic": "tele/rf-bridge/RESULT",
        "username": "username",
        "password": "password",
        "rfcode": "2E1A21",
        "ondelay": "10000",
        "rfcodelowbattery": "2E1A22",
        "accessoryservicetype": "LeakSensor",
        "name": "Leak Sensor"
    },
    {
        "accessory": "mqtt-sonoffrf-receiver-2",
        "url": "mqtt://localhost",
        "topic": "tele/rf-bridge/RESULT",
        "username": "username",
        "password": "password",
        "rfcode": "2E1A21",
        "ondelay": "60000",
        "ondelaylowbattery": "120000",
        "rfcodelowbattery": "2E1A22",
        "accessoryservicetype": "SmokeSensor",
        "name": "Smoke Sensor"
    },
    {
        "accessory": "mqtt-sonoffrf-receiver-2",
        "url": "mqtt://localhost",
        "topic": "tele/rf-bridge/RESULT",
        "username": "username",
        "password": "password",
        "rfcode": "2E1A21",
        "ondelay": "10000",
        "rfcodelowbattery": "2E1A22",
        "accessoryservicetype": "StatelessProgrammableSwitch",
        "name": "RF Button 433"
    }

# References
Use [homebridge-mqtt-sonoffrf-transmitter](https://github.com/miskui/homebridge-mqtt-sonoffrf-transmitter) to control RF devices in Homebridge.
