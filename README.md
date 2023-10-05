# Monitoring System in the Field of Genomics

<summary><h2>Context</h3></summary>

The group works on the data engineering team at HealthGen, a leading company in the field of genomics and personalized medicine research. Genomics, which is the in-depth investigation of an organism's complete genome, serves as a cornerstone in personalized medicine and advanced biomedical initiatives. Through it, it is possible to dissect DNA, discovering genetic variants and mutations that may be linked to various diseases, providing a path to shaping treatments that specifically align with the patient's genetic profile.

With this in mind, this project uses modern tools such as Apache Kafka for real-time data streaming, the Databricks platform for collaborative analysis and the power of Apache Spark for distributed processing of big data. This system is capable of collecting, processing and analyzing the latest information and news about genomics and personalized medicine.

Api: https://newsapi.org/v2/everything

<summary><h2> Cluster management - Databricks</h2></summary>
version_cluster: 14.0 (includes Apache Spark 3.5.0, Scala 2.12)

To run the producer and consumer it is necessary to perform a few steps first, in the project files.


## Kafka_Management

1 - To install the `kafka`, rotate the first cell of the notebook:

```bash
  %sh 
  sudo wget https://downloads.apache.org/kafka/3.4.1/kafka_2.12-3.5.1.tgzv
```

2 - Extract the downloaded file

```bash
  %sh 
  tar -xvf kafka_2.12-3.5.1.tgz
```

3 - Initialize Kafka

```bash
  %sh 
  ./kafka_2.12-3.5.1/bin/kafka-server-start.sh ./kafka_2.12-3.5.1/config/server.properties
```


## ZooKeeper_Configuration

1 - Run `zookeeper-server-start`, you need to install kafka before performing this step.

```bash
  %sh 
  ./kafka_2.12-3.5.1/bin/zookeeper-server-start.sh ./kafka_2.12-3.5.1/config/zookeeper.properties
```


## Kafka_Producers

1 - After kafka server and zookeeper are initialized, install `kafka-python`.

```bash
  %pip install kafka-python
```

2 - Rotate the topic creation cell.

```bash
  %sh
  ./kafka_2.12-3.5.1/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic topic_news --partitions 1 --replication-factor 1
```

