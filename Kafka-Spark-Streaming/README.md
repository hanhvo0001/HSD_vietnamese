# Streaming using Kafka + Spark
## Requirements:
- Python 3.7.x
- kafka-python
- confluent_kafka
- kafka_2.13-2.8.1
- spark 3.1.1 or 3.1.2 - hadoop 2.7
- transformers 4.3.0
- google-api-python-client
## Implementation:
To clone this folder:\
```git clone https://github.com/davione112/HateSpeechDetection/trunk/Kafka-Spark-Streaming```
1. Start Zookeeper and Kafka server on command line:
  - cd <kafka-folder>
  - ```.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties``` to start Zookeeper.
  - ```.\bin\windows\kafka-server-start.bat .\config\server.properties``` to start Kafka server.\
  **Note**: Run 2 lines above in 2 command prompts, start Zookeeper first.
2. Create *hsd* and *detected* topics:
  - Run on another command prompt:
  - ```.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic hsd```
  - ```.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic detected```
3. Run ```producer_utube_data.ipynb``` notebook to start get data from Youtube and producing data to Kafka topic (hsd topic). 
  - You can change ```video_link``` to get comment data from another video. 
4. Run ```detection.ipynb``` notebook to start consume data from producer, do Hate Speech Detection, then produce processed data to Kafka topic (detected topic).
5. Run ```spark-kafka.ipynb``` notebook to get streaming data using Spark Structure Streaming. \
  **Note** Due to initializing time, we recommend you run 5 -> 3 -> 4 if you run from the beginning.
