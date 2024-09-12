---
title: Different Kind of Latency Requirements
---
Latency requirements can vary greatly depending on the use case and how time-sensitive the operations are. Here’s a breakdown based on different latency categories:

## 1. Daily Latency (~24 hours)
### Use Case  
 - **Batch Processing**: Jobs that run once a day, such daily report or backups.
 - **Data Warehousing**: ETL processes that update data sets once per day.
### Example 
- Sales reports
- Daily customer data syncs
- Financial reporting
### Technologies
- **Data Processing**: 
	- [[Apache Hadoop]]
	- [[Apache Spark]] (Batch mode)
	- [[AWS Glue]]
- **Data Warehousing**: 
	- [[Google BigQuery]]
	- Amazon Redshift
	- Snowflake
	- Databricks (Batch)
- **[[Scheduler and Workflow Orchestration]]**: 
	- [[Apache Airflow]]
	- [[Prefect]]
	- [[Cron jobs]]
   
## 2. Hourly Latency (~1 hour)
### Use Case
**Periodic Monitoring**: Status checks or reporting that occur once every hour.
**IoT Monitoring**: Aggregated data from sensors that don’t need real-time updates but are still frequent.
### Example
- Hourly website traffic reports
- IoT sensor data aggregation.
### Technologies
- **[[Stream Processing]]** (with hourly windows): 
	- [[Apache Kafka]] (with hourly windowing)
	- [[Apache Flink]] (with tumbling windows)
- **Scheduled Jobs**: 
	- [[Apache Airflow]]
	- Jenkins (for data jobs)
	- Lambda with scheduled events
- **ETL Tools**: 
	- Fivetran
	- Stitch
	- Apache NiFi
- **Data Storage**: AWS S3 for hourly updates, Google Cloud Storage

## 3. Minute-Level Latency (~1-10 minutes)
### Use Case
- **Near-Real-Time Analytics**: Use cases where insights need to be available within minutes, like social media trend tracking.
- **Batch Job Alerts**: Sending alerts based on aggregated metrics every few minutes.
### Example
- Online ad performance metrics
- Fraud detection in financial transactions.
### Technologies
- **[[Stream Processing]]**: 
	- [[Apache Kafka]]
	- [[Apache Flink]]
	- [[Spark Streaming]]
	- [[Apache Pulsar]]
- **Real-Time Databases**: 
	- [[Apache Druid]]
	- [[ClickHouse]]
	- [[Google BigQuery]] (with streaming inserts)
- **Event-Driven Platforms**: 
	- [[AWS Kinesis]]
	- [[Google PubSub]]
- **Monitoring & Alerting**: 
	- [[Prometheus]]
	- [[Grafana]]
## 4. Second-Level Latency (~1-60 seconds)
### Use Case
**Real-Time Monitoring**: Dashboards and systems that require updates every few seconds to track real-time activity.
**Event Processing**: Handling events such as user actions or service requests in applications.
### Example
- Stock market data tracking
- Website analytics
- Real-time user notifications.
### Technologies
- **Stream Processing**: 
	- [[Apache Flink]] (with small window sizes)
	- [[Spark Streaming]]
	- [[Kafka Streams]]
- **Event Processing**: 
	- AWS Lambda
	- Google Cloud Functions
	- Apache Pulsar
- **Websockets for Real-Time**: 
	- Socket.io
	- Firebase Realtime Database
	- Pusher
- **Message Brokers**: 
	- RabbitMQ
	- Redis Pub/Sub
	- NATS
	- Apache Kafka

## 5. Millisecond-Level Latency (~1-1000 ms)
### Use Case
- **Interactive Applications**: Applications where user interaction must feel instantaneous.
- **Real-Time Game Servers**: Multiplayer game servers that require extremely low-latency for smooth gameplay.
### Example
- Online gaming
- High-frequency trading
- Real-time bidding for ads.
### Technologies
- **Real-Time Databases**: 
	- [[Redis]] (in-memory)
	- [[Aerospike]]
	- [[ScyllaDB]]
	- [[Memcached]]
- **Low-Latency Message Brokers**: 
	- [[Apache Kafka]]
	- [[RabbitMQ]]
	- Redis Streams
- **Load Balancers**: 
	- [[NGINX]]
	- [[HAProxy]]
- **Fast Web Frameworks**: 
	- Go (Gorilla Mux)
	- Node.js
	- FastAPI (Python)
- **Networking**: 
	- TCP-based communication
	- WebSockets
	- gRPC (low-latency RPC framework)

## 6. Microsecond-Level Latency (~1-1000 µs)
### Use Case
**Financial Systems**: High-frequency trading where every microsecond matters for decision-making and transaction speed.
**Hardware-Level Communication**: Low-level communication between hardware components.
### Example  
- Ultra-low latency trading
- CPU-to-memory communication.
### Technologies
- **Low-Latency Networking**: 
	- RDMA (Remote Direct Memory Access)
	- DPDK (Data Plane Development Kit)
- **Ultra-Fast Message Brokers**: 
	- ZeroMQ
	- Aeron
	- Chronicle Queue (for low-latency messaging)
- **Custom Hardware**: 
	- FPGA (Field Programmable Gate Arrays)
	- ASIC (Application-Specific Integrated Circuits)

Each latency level represents a different need for responsiveness, driven by how critical time sensitivity is to the success of the application or system.