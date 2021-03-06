pentaho-kafka-consumer
======================

Apache Kafka consumer step plug-in for Pentaho Kettle.

[![Build Status](https://travis-ci.org/RuckusWirelessIL/pentaho-kafka-consumer.png)](https://travis-ci.org/RuckusWirelessIL/pentaho-kafka-consumer)


### Screenshots ###

![Using Apache Kafka Consumer in Kettle](https://raw.github.com/RuckusWirelessIL/pentaho-kafka-consumer/master/doc/example.png)


### Apache Kafka Compatibility ###

The consumer depends on Apache Kafka 0.8.1.1, which means that the broker must be of 0.8.x version or later.

If you want to build the plugin for a different Kafka version you have to
modify the values of kafka.version and kafka.scala.version in the properties
section of the pom.xml. 

### Maximum Duration Of Consumption ###

Note that the maximum duration of consumption is a limit on the duration of the
entire step, *not* an individual read. This means that if you have a maximum
duration of 5000ms, your transformation will stop after 5s, whether or
not more data exists and independent of how fast each message is fetched from
the topic. If you want to stop reading messages when the topic has no more
messages, see the section on _Empty topic handling_.

### Empty topic handling ###

If you want the step to halt when there are no more messages available on the
topic, check the "Stop on empty topic" checkbox in the configuration dialog. The
default timeout to wait for messages is 1000ms, but you can override this by
setting the "consumer.timeout.ms" property in the dialog. If you configure a
timeout without checking the box, an empty topic will be considered a failure
case.

### Installation ###

1. Download ```pentaho-kafka-consumer``` Zip archive from [latest release page](https://github.com/RuckusWirelessIL/pentaho-kafka-consumer/releases/latest).
2. Extract downloaded archive into *plugins/steps* directory of your Pentaho Data Integration distribution.


### Building from source code ###

```
mvn clean package
```
这个是适配kafka_2.11-0.9.0.1这个版本的插件，本新增了从最开始方式读数据，后续会新增该部分代码的注释
