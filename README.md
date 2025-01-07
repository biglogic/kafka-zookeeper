# kafka-zookeeper
a kafka-zookeeper docker compose for quick setup with kafka ui


## Kafka and Zookeeper Cluster with Docker Compose

🚀 This repository contains a docker-compose.yml file for setting up a Kafka and Zookeeper cluster, along with Kafka UI for cluster management.

### 📖 Overview

   The setup consists of the following components:

 - ##### Kafka UI: A web-based interface to manage and monitor the Kafka cluster.

 - ##### Zookeeper: A quorum of two Zookeeper instances for managing Kafka cluster metadata.

 - ##### Kafka Brokers: Two Kafka broker instances configured for replication and high availability.

### ✅ Prerequisites

  - Docker and Docker Compose installed on your system.

  - Sufficient disk space to store Kafka and Zookeeper data.


### 🏗️ Architecture

#### Components

- #### Kafka UI: Accessible on http://localhost:8089. It connects to the Kafka brokers using the bootstrap servers.

- #### Zookeeper:
    - zoo1 (Port: 2181)

    - zoo2 (Port: 2182)

- #### Kafka Brokers:

  - kafka1 (Ports: 9092, 29092, JMX: 9999)

  - kafka2 (Ports: 9093, 29093)

### Data Persistence

  - Data for Zookeeper and Kafka brokers is persisted using mounted volumes:

  - Zookeeper data: ./zookeeper_data, ./zookeeper_data_2

  - Kafka data: ./kafka_data, ./kafka_data_2



# 🚀 Getting Started

#### Step 1: Clone the Repository

- git clone [https://github.com/biglogic/kafka-zookeeper.git](https://github.com/biglogic/kafka-zookeeper.git)

- cd kafka-zookeeper

#### Step 2: Start the Cluster

 - Run the following command to start all services:

    - docker-compose up -d

#### Step 3: Access Kafka UI

 - Kafka UI is available at:

``` 
http://localhost:8089
```

### Use the UI to explore topics, consumer groups, and other Kafka configurations.

#### Step 4: Interact with Kafka

You can interact with Kafka brokers using the kafka-console-producer and kafka-console-consumer tools or any Kafka client library.

## ⚙️ Configuration Details

 - Kafka Broker Configuration

 -  KAFKA_ADVERTISED_LISTENERS:

    - INTERNAL: Internal communication between brokers.

    - EXTERNAL: Exposed to clients on the host.


#### DOCKER: Used by Kafka UI.

 - KAFKA_ZOOKEEPER_CONNECT: Points to the Zookeeper quorum (zoo1:2181, zoo2:2182).

Replication Factor and ISR (In-Sync Replica) settings ensure durability.

- #### Zookeeper Configuration

     - ZOOKEEPER_CLIENT_PORT: Port used by Kafka brokers to connect to Zookeeper.

    -  ZOOKEEPER_SERVERS: Defines the Zookeeper quorum.

## Kafka UI Configuration

DYNAMIC_CONFIG_ENABLED: Allows dynamic updates to the Kafka cluster configuration.

- KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: Bootstrap servers for Kafka UI to connect to the Kafka cluster.


## ✨ Notes

Ensure that Docker has enough allocated memory to run the cluster smoothly.

You can scale the Kafka brokers by adding more services in the docker-compose.yml file.
