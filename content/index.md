---
title: Data Engineering Garden
---

Welcome! I’m excited to share this space with you—a place where ideas bloom, knowledge grows, and curiosity thrives. This Knowledge Garden is more than just a collection of information; it’s a living, breathing ecosystem where I cultivate and nurture my thoughts, experiences, and learnings.
## Conceptual
- [[How to Think about Many Tools in Data Engineering Space]]
- [[Different Kind of Latency Requirements]]
## References
- [[Different Kind of Data Sources]]
- [[Different of Roles or Specializations]]
- [[List of Tools]]
- [[List of Tools Categories]]


```mermaid
graph LR

de[DE Tools]

  

storage[storage engine]

compute[compute engine]

  

de --> storage

de --> compute

  

spark["[[Apache Spark]]"]

flink

kafka

trino

bigquery

  

batch[batch processing]

stream[stream processing]

  

compute --> batch

compute --> stream

batch --> spark

batch --> trino

batch --> bigquery

  

stream --> flink

stream --> kafka

  

storage --> storage-format

storage-format

storage-format --> row-based

storage-format --> columnar

  

storage --> data-model

data-model --> relational

data-model --> key-value

data-model --> wide-table

data-model --> g["graph"]

  

storage --> persistence-level

persistence-level --> in-memory

persistence-level --> persistent

  

in-memory --> caching

  

storage --> structure

structure --> block-store

structure --> object-store

structure --> filesystem

  

row-based --> RDBMS

relational --> RDBMS

RDBMS --> Postgres

RDBMS --> MySQL

  

columnar --> clickhouse

relational --> clickhouse

  

key-value --> redis

wide-table --> cassandra

wide-table --> scyllaDB

  

R:server
```