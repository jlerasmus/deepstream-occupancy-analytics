**People count application With Deepstream SDK and Transfer Learning Toolkit**

* [Description](#description)
* [Prerequisites](#prerequisites)
* [Getting Started](#Getting Started)
* [Build](#build)
* [Run](#run)
* [Output](#output)
* [References](#references)
<p align="center">
  <img src="images/test.png">
</p>

## Description 

This is a demo project for "People Count Application" using NVIDIA Deepstream SDK and Transfer Learning Toolkit (TLT).The application is based on deepstream-test5 application. It takes the input source data, uses PeopleNet model for inferencing and sends the people count data to cloud. 

## Prerequisites


- Install Deepstream: [https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html#page/DeepStream_Development_Guide/deepstream_quick_start.html#]

- Download PeopleNet model: [https://ngc.nvidia.com/catalog/models/nvidia:tlt_peoplenet]

- This application is based on deepstream-test5 application. More about test5 application: [https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html#page/DeepStream_Development_Guide/deepstream_reference_app_test5.html]

- Install Kafka: [https://kafka.apache.org/quickstart] and create the kafka topic:

  `tar -xzf kafka_2.13-2.6.0.tgz`

  `cd kafka_2.13-2.6.0` 

  `bin/zookeeper-server-start.sh config/zookeeper.properties`

  `bin/kafka-server-start.sh config/server.properties`

  `bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092`

## Getting Started

- Preferably clone the repo in $DS_SDK_ROOT/sources/apps/sample_apps/ 
- Download peoplnet model: `cd demo/config && ./model.sh`
- For Jetson use:  bin/jetson/libnvds_msgconv.so
- For x86 use: bin/x86/libnvds_msgconv.so
	 

## Build

 `cd demo && make`

## Run 

 `./deepstream_test5 -c configs/test5_config_file_src_infer_tlt.txt`

  In another terminal run this command to see the kafka messages:

 `bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092`


## Output

  The output will look like this: 

  ![alt-text](https://gitlab-master.nvidia.com/mjhuria/demo/-/raw/master/images/kafka_messages.gif)

  Where you can see the kafka messages for entry and exit count.
  

## References

- CREATE INTELLIGENT PLACES USING NVIDIA PRE-TRAINED VISION MODELS AND DEEPSTREAM SDK: [https://info.nvidia.com/iva-occupancy-webinar-reg-page.html?ondemandrgt=yes]
- Deepstream SDK: [https://developer.nvidia.com/deepstream-sdk]
- Deepstream Quick Start Guide: [https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html#page/DeepStream_Development_Guide/deepstream_quick_start.html#]
- Transfer Learning Toolkit: [https://developer.nvidia.com/transfer-learning-toolkit]
