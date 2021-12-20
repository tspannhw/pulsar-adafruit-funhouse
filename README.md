# pulsar-adafruit-funhouse

AdaFruit Funhouse publishing Temperature, Humidity and Pressure to MQTT / Apache Pulsar

## Device

![Adafruit Funhouse](https://raw.githubusercontent.com/tspannhw/pulsar-adafruit-funhouse/main/IMG-6527.jpg)

## Get your own from adafruit

* Adafruit is a great company in NYC, I highly recommend you buy one or buy an ADABOX.   My daughter and I love these.

* https://www.adafruit.com/product/4985


## Fork of adafruit Funhouse

* https://learn.adafruit.com/using-the-adafruit-funhouse-with-home-assistant/code-the-sensor

## Example Consuming 

````

11:02:47.628 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConnectionPool - [[id: 0x3ec5ce7d, L:/127.0.0.1:59610 - R:localhost/127.0.0.1:6650]] Connected to server
11:02:47.628 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ClientCnx - [id: 0x3ec5ce7d, L:/127.0.0.1:59610 - R:localhost/127.0.0.1:6650] Connected through proxy to target broker at 127.0.0.1:6650
11:02:47.630 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerImpl - [persistent://public/default/funhousestate][fhs] Subscribing to topic on cnx [id: 0x3ec5ce7d, L:/127.0.0.1:59610 - R:localhost/127.0.0.1:6650], consumerId 0
11:02:47.642 [pulsar-client-io-1-1] INFO  org.apache.pulsar.client.impl.ConsumerImpl - [persistent://public/default/funhousestate][fhs] Subscribed to topic on localhost/127.0.0.1:6650 -- consumer: 0
11:02:47.673 [pulsar-client-io-1-1] INFO  com.scurrilous.circe.checksum.Crc32cIntChecksum - SSE4.2 CRC32C provider initialized
----- got message -----
key:[null], properties:[], content:{"pressure": 1025.05, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1458, "temperature": 77.8455, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 7049}
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.98, "button_sel": "off", "pir_sensor": "off", "humidity": 27.0822, "temperature": 77.9334, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 7784}
11:03:47.607 [pulsar-timer-5-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - [persistent://public/default/funhousestate] [fhs] [940a9] Prefetched messages: 0 --- Consume throughput received: 0.03 msgs/s --- 0.00 Mbit/s --- Ack sent rate: 0.03 ack/s --- Failed messages: 0 --- batch messages: 0 ---Failed acks: 0
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.151, "temperature": 77.8507, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9234}
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1309, "temperature": 77.8442, "button_down": "on", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9413}
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1309, "temperature": 77.8442, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9413}
11:04:47.608 [pulsar-timer-5-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - [persistent://public/default/funhousestate] [fhs] [940a9] Prefetched messages: 0 --- Consume throughput received: 0.05 msgs/s --- 0.00 Mbit/s --- Ack sent rate: 0.05 ack/s --- Failed messages: 0 --- batch messages: 0 ---Failed acks: 0
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.91, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7443, "temperature": 78.4608, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 11180}
11:05:47.609 [pulsar-timer-5-1] INFO  org.apache.pulsar.client.impl.ConsumerStatsRecorderImpl - [persistent://public/default/funhousestate] [fhs] [940a9] Prefetched messages: 0 --- Consume throughput received: 0.02 msgs/s --- 0.00 Mbit/s --- Ack sent rate: 0.02 ack/s --- Failed messages: 0 --- batch messages: 0 ---Failed acks: 0
----- got message -----
key:[null], properties:[], content:{"pressure": 1024.93, "button_sel": "off", "pir_sensor": "off", "humidity": 26.8115, "temperature": 78.1902, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 13365}

````
