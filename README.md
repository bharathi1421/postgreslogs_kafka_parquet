====>PostgreSQL and Kafka Integration with Python
====>This project demonstrates how to integrate PostgreSQL with Kafka, collect logs from PostgreSQL, and save them to a Parquet file using Docker and Python.

OVERVIEW
1]Docker PostgreSQL Setup:
  I]Installed Docker PostgreSQL.
  II]Created, altered, updated, and dropped tables using a Python script.
  III]Connected the Python script with PostgreSQL.
  IV]Kafka Setup:

2]Installed and configured Kafka on the terminal.
  I]Created a Kafka topic named quickstart.
  II]Collected PostgreSQL logs into Kafka using a Python script.
  III]Log Processing:
  IV]Processed real-time data logs from Kafka.
  V]Saved the logs into a Parquet file for further analysis.
3]PREREQUISITIES
Docker
PostgreSQL
Kafka
Python
Kafka Python client
Pandas library
PyArrow library
Setup Instructions
Docker PostgreSQL

COMMANDS:
*INSTALL POSTGRES IN DOCKER
bash
Copy code
docker run --name postgres_db -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
Python Script for PostgreSQL Operations: [postgresfile]==> see my document file
Created tables, altered, updated, and dropped tables using the script. The script connects to the PostgreSQL database and performs these operations.

*KAFKA SETUP
=>Install Kafka:
      docker exec -it <kafka_conatiner_id> /bin/sh  [TO CREATE A KAFKA CONTAINER]==> [docker_compose.yml] see my document file

=>Go inside kafka installation folder
      cd /opt/kafka_<version>/bin
=>Create Kafka Topic:
bash
Copy code
      kafka-topics.sh --create --topic quickstart --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

=>Create consumer
      kafka-console-consumer.sh --topic quickstart --from-beginning --bootstrap-server localhost:9092

Python Script for Log Collection:

The script collects PostgreSQL logs and sends them to the quickstart Kafka topic. [refer my files]

Log Processing
Python Script for Log Processing:  [refer my files]

Reads logs from the quickstart Kafka topic.
Saves the logs into a Parquet file using Pandas and PyArrow.
