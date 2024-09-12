---
title: How to Think about Many Tools in Data Engineering Space
---
## Background

The data engineering (DE) landscape is crowded with tools, and it can be overwhelming to understand their purpose. Is Kafka just a messaging system, or is it also a storage engine? Is Trino a database, or just a query engine? Even familiar databases like Postgres and MySQL have subtleties: Postgres is both a database and a storage engine, while MySQL uses InnoDB as its default storage engine. With so many tools, how do we categorize them?

## Compute and Storage Engine

At a high level, all data engineering tools can be divided into two categories: **compute engines** (also known as query engines) and **storage engines**. While each tool may blur these lines, understanding this basic division is key to thinking about their roles and selecting the right tools for your stack.
- **Compute Engine:** This refers to systems designed to process and compute data. Query engines like Trino, Spark, or Flink are in this category.
- **Storage Engine:** These are systems focused on persisting and managing data. Tools like HDFS, S3, and databases like Postgres, Cassandra, or even Kafka in some cases, serve this role.

### Example

#### PostgreSQL: Traditional Database with Coupled Compute and Storage

PostgreSQL is both a **storage engine** and a **compute engine**.

1. **Storage Engine**: PostgreSQL manages data storage directly, handling how data is written to and retrieved from disk. It provides ACID (Atomicity, Consistency, Isolation, Durability) guarantees for transactions and uses its own storage formats (tables, indexes, etc.) to store data efficiently on disk.
2. **Compute Engine**: PostgreSQL also functions as a **compute engine**, executing SQL queries, handling complex joins, aggregations, indexing, and data transformations. It processes and computes results directly on the data it stores.

Unlike decoupled systems, PostgreSQL **couples** both storage and compute in a single system, making it a traditional database management system (DBMS).

#### Spark: Distributed Compute for Batch and Streaming

Apache Spark is primarily a **compute engine**.

It is designed for large-scale distributed data processing, handling both **batch** and **stream processing**. Spark excels at in-memory computation, making it highly efficient for iterative algorithms and complex transformations across massive datasets. However, Spark does not have its own built-in storage system.

Instead, it relies on external **storage engines** (such as HDFS, S3, or databases like Cassandra) to read data from and write data to. During processing, Spark loads data into memory, performs computations, and then writes the results back to external storage.

So, while Spark is a powerful **compute engine**, it depends on external systems for **storage**.

#### Flink: Stream Processing as a Compute Engine

Apache Flink is primarily a **compute engine**.

It is mainly designed for **stream processing** and treat **batch processing** a special cases, enabling real-time and complex event processing across distributed systems. Flink excels in scenarios requiring low-latency, high-throughput data processing and supports a variety of advanced features like event time processing, state management, and fault tolerance.

**Key Points about Flink**:
- **Compute Engine**: Flink processes data in memory and performs complex transformations and aggregations on streaming or batch data. It handles the computation aspects but does not manage data storage directly.
- **External Storage**: Flink relies on external storage systems (like HDFS, S3, or databases) for storing data. It reads from and writes to these storage systems but does not have its own built-in storage layer.

In summary, Flink is a powerful **compute engine** that handles data processing and analytics but depends on external systems for data storage.

#### Kafka: Messaging, Storage, and More

Kafka is primarily a **storage engine** but also has some lightweight **compute** capabilities.

1. **Storage Engine**: Kafka is designed as a distributed log storage system. It stores streams of records in a fault-tolerant and durable manner, making it a reliable storage layer for event data. Data is written to partitions and stored persistently, often for long retention periods, depending on the configuration. Kafka’s append-only log structure allows it to act as a storage engine for streaming data.

2. **Compute Engine (Limited)**: Kafka is not a full-fledged compute engine like Spark or Flink, but it does offer some compute-like functionalities through:
   - **Kafka Streams**: A library that allows real-time stream processing directly within Kafka, enabling transformation, filtering, and aggregation of data as it flows through Kafka topics.
   - **ksqlDB**: A SQL-like abstraction over Kafka Streams, providing an interface for performing lightweight transformations and aggregations on Kafka data without needing an external processing system.

In summary, Kafka is primarily focused on **storage** but provides some basic **compute** features for stream processing.

#### ClickHouse

ClickHouse is both a **storage** and **compute** engine.

It is a **columnar database management system** (DBMS) designed for **online analytical processing (OLAP)**. ClickHouse handles data storage internally using a highly optimized, columnar storage format, which is ideal for large-scale analytical queries. At the same time, it provides its own query processing and execution engine (compute), allowing for fast and efficient execution of SQL queries directly on the stored data.

In essence, ClickHouse **couples** compute and storage within a single system, like traditional databases, but with optimizations for large-scale analytics and real-time querying.

## Compute Engine Subcategories

Certainly! Here’s an explanation of different types of compute engines and their typical use cases:

### 1. Batch Processing Engines
Batch processing engines handle large volumes of data in discrete chunks or batches. They are designed for processing large datasets that don't require real-time analysis.

- **Characteristics**:
  - Processes data in batches or chunks.
  - Often used for ETL (Extract, Transform, Load) tasks.
  - Suitable for large-scale data processing that doesn’t require immediate results.

- **Examples**:
  - **Apache Spark**: Provides a unified analytics engine for large-scale data processing with support for batch processing, as well as stream processing and machine learning.
  - **Apache Hadoop MapReduce**: Processes large datasets by dividing them into smaller tasks and aggregating the results.

### 2. Stream Processing Engines
Stream processing engines process data in real-time as it flows into the system. They are designed to handle continuous streams of data, making them ideal for applications that require low-latency responses.

- **Characteristics**:
  - Handles real-time data with low latency.
  - Suitable for applications like fraud detection, real-time analytics, and monitoring.

- **Examples**:
  - **Apache Flink**: Provides real-time stream processing with strong support for event time processing and stateful computations.
  - **Apache Kafka Streams**: A library for building real-time stream processing applications on top of Apache Kafka.

### 3. Interactive Query Engines
Interactive query engines are optimized for executing ad-hoc queries on large datasets, providing fast response times for user interactions and exploratory data analysis.

- **Characteristics**:
  - Designed for low-latency query execution.
  - Ideal for interactive analytics and ad-hoc querying.

- **Examples**:
  - **Apache Presto** (now Trino): A distributed SQL query engine for running interactive queries across heterogeneous data sources.
  - **Google BigQuery**: A fully-managed, serverless data warehouse that enables fast SQL queries on large datasets.

### 4. Data Science and Machine Learning Engines
These engines are specialized for machine learning, statistical analysis, and data science tasks. They often provide tools and libraries for model training, evaluation, and deployment.

- **Characteristics**:
  - Focused on machine learning and statistical modeling.
  - Integrates with various data processing frameworks and storage systems.

- **Examples**:
  - **TensorFlow**: An open-source library for machine learning and deep learning.
  - **Apache Mahout**: A scalable machine learning library built on top of Apache Hadoop.

### 5. OLAP Engines
Online Analytical Processing (OLAP) engines are designed for complex analytical queries and multidimensional analysis. They are used for data warehousing and business intelligence.

- **Characteristics**:
  - Optimized for complex queries and data aggregation.
  - Supports multidimensional analysis and reporting.

- **Examples**:
  - **ClickHouse**: A columnar database that provides high performance for analytical queries.
  - **Apache Druid**: A real-time analytics database designed for fast aggregations and OLAP queries.

Each type of compute engine has specific strengths and use cases, and they are often used in combination to build comprehensive data processing and analytics platforms.

## Storage Engine Subcategories

Conceptually, storage engines can be divided into several categories based on different criteria. Here’s an overview of how they can be classified:

### 1. By Data Model or Modeling Pattern
- **Relational**: Data is organized in tables with rows and columns, and relationships between tables are defined using foreign keys. This model supports complex queries and transactions using SQL.
  - **Examples**: PostgreSQL, MySQL, Oracle Database

- **Key-Value**: Data is stored as simple key-value pairs. This model is highly performant for simple retrieval operations but lacks complex querying capabilities.
  - **Examples**: Redis, Amazon DynamoDB

- **Document**: Data is stored in semi-structured formats like JSON or BSON. Documents can contain nested structures and varying schemas, making this model flexible for hierarchical data.
  - **Examples**: MongoDB, Couchbase

- **Graph**: Data is represented as nodes and edges, where relationships between entities are as important as the data itself. This model is optimized for querying and traversing relationships.
  - **Examples**: Neo4j, Amazon Neptune

### 2. By Storage Format

- **Row-Based**: Data is stored row by row. This format is efficient for transactional operations where entire rows need to be retrieved or updated.
  - **Examples**: Traditional relational databases like PostgreSQL and MySQL

- **Columnar-Based**: Data is stored column by column. This format is optimized for read-heavy analytical queries and can provide better compression and retrieval performance for columns accessed in queries.
  - **Examples**: Apache Parquet (format), ClickHouse, Apache HBase (columnar mode)

### 3. By Persistence and Data Access

- **Object Storage**: Designed for storing large volumes of unstructured data such as files, images, and logs. Provides scalability and durability.
  - **Examples**: Amazon S3, Google Cloud Storage

- **File Systems**: A traditional method of storing and organizing files in directories, often used in conjunction with data processing frameworks.
  - **Examples**: HDFS (Hadoop Distributed File System), local file systems

### 4. By Transactional Properties

- **ACID-Compliant**: Ensures atomicity, consistency, isolation, and durability of transactions. Ideal for applications requiring strong data integrity and complex queries.
  - **Examples**: PostgreSQL, Oracle Database

- **Eventual Consistency**: Data is replicated across nodes with eventual consistency guarantees. Suitable for distributed systems where immediate consistency is less critical.
  - **Examples**: Amazon DynamoDB, Cassandra


Each of these categories helps in understanding the fundamental characteristics and suitable use cases for different storage engines. The choice of storage engine often depends on the specific requirements of the application, such as data structure, performance needs, and scalability.