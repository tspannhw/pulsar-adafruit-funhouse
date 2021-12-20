# pulsar-adafruit-funhouse

AdaFruit Funhouse publishing Temperature, Humidity and Pressure to MQTT / Apache Pulsar

## Device

![Adafruit Funhouse](https://raw.githubusercontent.com/tspannhw/pulsar-adafruit-funhouse/main/IMG-6527.jpg)

## Get your own from adafruit

* Adafruit is a great company in NYC, I highly recommend you buy one or buy an ADABOX.   My daughter and I love these.

* https://www.adafruit.com/product/4985


## Fork of adafruit Funhouse

* https://learn.adafruit.com/using-the-adafruit-funhouse-with-home-assistant/code-the-sensor

I removed the mqtt consume, as I just want to produce data.   I also lowered the time down to 10 seconds to get more data.

## Apache Pulsar / MQTT Server Setup

````
bin/pulsar-admin topics create persistent://public/default/funhousestate

bin/pulsar-admin topics create persistent://public/default/funhouselightstate

bin/pulsar-admin topics create persistent://public/default/funhouselightset

bin/pulsar-client consume "persistent://public/default/funhousestate" -s "fhs" -n 0

bin/pulsar-client consume "persistent://public/default/funhouselightstate" -s "fhs2" -n 0
````


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

## Device Output

````
Connecting to AP WiFi-SSiD
Attempting to connect to 192.168.1.230
Connected to MQTT! Subscribing...
Publishing to funhouselightstate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
Publishing to funhousestate
````

## Pulsar SQL (Trino/Presto) Against Our Topic

````
presto> describe pulsar."public/default".funhousestate;
      Column       |   Type    | Extra |                                   Comment                                   
-------------------+-----------+-------+-----------------------------------------------------------------------------
 __value__         | varbinary |       | The value of the message with primitive type schema                         
 __partition__     | integer   |       | The partition number which the message belongs to                           
 __event_time__    | timestamp |       | Application defined timestamp in milliseconds of when the event occurred    
 __publish_time__  | timestamp |       | The timestamp in milliseconds of when event as published                    
 __message_id__    | varchar   |       | The message ID of the message used to generate this row                     
 __sequence_id__   | bigint    |       | The sequence ID of the message used to generate this row                    
 __producer_name__ | varchar   |       | The name of the producer that publish the message used to generate this row 
 __key__           | varchar   |       | The partition key for the topic                                             
 __properties__    | varchar   |       | User defined properties                                                     
(9 rows)

Query 20211220_162305_00000_jb263, FINISHED, 1 node

presto> select from_utf8(__value__), __event_time__ from pulsar."public/default".funhousestate;
                                                                                                               _col0                                                                                                         
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4877, "temperature": 78.4426, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5187, "temperature": 78.3746, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5695, "temperature": 78.3619, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5451, "temperature": 78.4014, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5962, "temperature": 78.4419, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5153, "temperature": 78.4653, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4735, "temperature": 78.5113, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4802, "temperature": 78.5772, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4331, "temperature": 78.5614, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4751, "temperature": 78.5284, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4645, "temperature": 78.4927, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4821, "temperature": 78.5175, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4546, "temperature": 78.5806, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4349, "temperature": 78.5353, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4277, "temperature": 78.5181, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4441, "temperature": 78.5205, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.72, "button_sel": "off", "pir_sensor": "off", "humidity": 26.446, "temperature": 78.5514, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 8
 {"pressure": 1024.71, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4064, "temperature": 78.5587, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.71, "button_sel": "off", "pir_sensor": "off", "humidity": 26.445, "temperature": 78.489, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 86
 {"pressure": 1024.7, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4509, "temperature": 78.4745, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 8
 {"pressure": 1024.7, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4372, "temperature": 78.5597, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9
 {"pressure": 1024.69, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4294, "temperature": 78.5689, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.69, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3617, "temperature": 78.6016, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.68, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3444, "temperature": 78.629, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.67, "button_sel": "off", "pir_sensor": "off", "humidity": 26.408, "temperature": 78.6046, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.67, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3903, "temperature": 78.6146, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.67, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3998, "temperature": 78.594, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3886, "temperature": 78.5878, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3589, "temperature": 78.5954, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4276, "temperature": 78.5999, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4165, "temperature": 78.593, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.65, "button_sel": "off", "pir_sensor": "off", "humidity": 26.44, "temperature": 78.572, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 192
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3759, "temperature": 78.5319, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4074, "temperature": 78.5562, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4225, "temperature": 78.5463, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4137, "temperature": 78.5587, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4313, "temperature": 78.6417, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3575, "temperature": 78.7125, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.66, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3391, "temperature": 78.6949, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.65, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3239, "temperature": 78.7299, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.65, "button_sel": "off", "pir_sensor": "off", "humidity": 26.2817, "temperature": 78.7293, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.64, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3036, "temperature": 78.7842, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.64, "button_sel": "off", "pir_sensor": "off", "humidity": 26.2396, "temperature": 78.8216, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1025.05, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1458, "temperature": 77.8455, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.98, "button_sel": "off", "pir_sensor": "off", "humidity": 27.0822, "temperature": 77.9334, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.151, "temperature": 77.8507, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9
 {"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1309, "temperature": 77.8442, "button_down": "on", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 9
 {"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 27.1309, "temperature": 77.8442, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.91, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7443, "temperature": 78.4608, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.93, "button_sel": "off", "pir_sensor": "off", "humidity": 26.8115, "temperature": 78.1902, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.92, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7218, "temperature": 78.364, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.88, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7223, "temperature": 78.4419, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.83, "button_sel": "off", "pir_sensor": "off", "humidity": 26.691, "temperature": 78.4127, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.78, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7081, "temperature": 78.2891, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.8562, "temperature": 78.217, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 1
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.8162, "temperature": 78.2222, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.79, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7946, "temperature": 78.1611, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.79, "button_sel": "off", "pir_sensor": "off", "humidity": 26.7673, "temperature": 78.3159, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.78, "button_sel": "off", "pir_sensor": "off", "humidity": 26.6741, "temperature": 78.3077, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.6788, "temperature": 78.2239, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.5748, "temperature": 78.3468, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4924, "temperature": 78.5672, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4867, "temperature": 78.7173, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3744, "temperature": 78.8199, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.2759, "temperature": 78.8206, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.2799, "temperature": 78.8103, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "on", "captouch8": "off", "light": 3
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.2799, "temperature": 78.8103, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.78, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3747, "temperature": 78.8141, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.78, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3929, "temperature": 78.7966, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.78, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4026, "temperature": 78.7694, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3921, "temperature": 78.7409, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4369, "temperature": 78.7111, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.77, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4217, "temperature": 78.7327, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4199, "temperature": 78.6538, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4199, "temperature": 78.6538, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "on", "captouch8": "off", "light": 7
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4199, "temperature": 78.6538, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "on", "pir_sensor": "off", "humidity": 26.4277, "temperature": 78.6932, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 2
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4277, "temperature": 78.6932, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.76, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4091, "temperature": 78.7592, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.75, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4165, "temperature": 78.7471, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.75, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4155, "temperature": 78.7636, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.75, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3756, "temperature": 78.7626, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.75, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3491, "temperature": 78.7262, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.74, "button_sel": "off", "pir_sensor": "off", "humidity": 26.3958, "temperature": 78.7001, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4425, "temperature": 78.5669, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4686, "temperature": 78.5387, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
 {"pressure": 1024.73, "button_sel": "off", "pir_sensor": "off", "humidity": 26.4582, "temperature": 78.5126, "button_down": "off", "captouch6": "off", "captouch7": "off", "button_up": "off", "captouch8": "off", "light": 
(87 rows)

Query 20211220_163025_00001_jb263, FINISHED, 1 node
Splits: 18 total, 18 done (100.00%)
0:01 [87 rows, 36KB] [82 rows/s, 34.1KB/s]

````
