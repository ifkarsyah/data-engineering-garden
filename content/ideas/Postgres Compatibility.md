---
title: Postgres Compatibility
---

> [!success] From Syntax to Runtime Levels

PostgreSQL compatibility means that a database should work seamlessly with applications and tools originally developed for use with a PostgreSQL database.  It achieves this compatibility by mirroring the original PostgreSQL’s features, functions, and syntax.

## Why is PostgreSQL compatibility important?

PostgreSQL [was ranked this year as the #1 database](https://survey.stackoverflow.co/2023/#section-most-popular-technologies-databases) by over 90,000 developers. Its meteoric rise—in terms of popularity—has led to the development of many different PostgreSQL-compatible databases. The goal? To make it easier to use [PostgreSQL](https://www.yugabyte.com/postgresql/) in the cloud or introduce new capabilities that are not available in the standard database distribution.

![[postgresql-popularity.png]]

PostgreSQL is considered the gold standard for transactional databases thanks to its proven feature set that is known and loved by technologists. It supports a number of  “post-relational” database concepts, including in-database functions. It is highly functional for many use cases and applications.

PostgreSQL offers advanced functionality in the form of stored procedures, user defined functions, triggers, and more, and is supported by a rich ecosystem of extensions, tools, connectors, drivers, and frameworks. 

A truly PostgreSQL-compatible database should integrate seamlessly with those frameworks and tools, as well as any applications developed for PostgreSQL. 

## PostgreSQL Compatibility Levels

Many databases claim to be PostgreSQL-compatible. However, it is important to understand that a claim of compatibility does not necessarily mean that the database is fully compatible. There are, in fact, four levels of PostgreSQL compatibility. Compatibility is not an all-or-nothing sport. 

There can be degrees of compatibility since databases can lay anywhere along a level’s spectrum.  Therefore, even if a database claims compatibility, updates may still be necessary to ensure that existing applications run smoothly.

### Wire-Protocol Compatibility

A PostgreSQL database reads a set of commands and queries off the network. These commands and queries are written in a sequence of bytes and serialized. A “wire-protocol compatible” database can understand this same data sequencing and serialization. Wire-protocol compatibility allows PostgreSQL client drivers to communicate with the database. 

This means that developers experienced with PostgreSQL can easily build their applications. They can write the application using a variety of programming languages—Java, JDBC, Python, Go, etc—and can use command-line tools (psql, for example) to connect to the database and explore a large number of schemas or queries.

### Syntax Compatibility

Syntax compatibility relates to how a database parses the PostgreSQL syntax. In other words, if a valid PostgreSQL snippet is sent to the database, it should create a table, execute a SQL statement, and return a valid result. 

With proper syntax, developers can use some of PostgreSQL’s tools and frameworks. They send the necessary commands, and the database understands and follows them.

### Feature Compatibility

With feature compatibility, a database can support the advanced features in PostgreSQL— beyond the ANSI SQL standard—to help you get the most out of your data. Some of these advanced features include [triggers, partial indexes, and stored procedures](https://www.yugabyte.com/blog/are-stored-procedures-and-triggers-anti-patterns-in-the-cloud-native-world/). 

On the other hand, an equivalent feature can have a different Postgres syntax to work. In this scenario, developers who rely on a specific Postgres feature would need to get up to speed with equivalent feature sets and make application modifications.

### Runtime Compatibility

Runtime compatibility is the highest level of PostgreSQL compatibility. It ensures that a database will match PostgreSQL execution semantics at runtime. More specifically, runtime-compatible databases should support queries to the system catalog, error messages, and error codes. 

Having runtime compatibility automatically implies that the other three compatibility metrics—wire, syntax, and feature—are in place. As a result, developers who know PostgreSQL will feel at home from start to finish.


More: https://www.yugabyte.com/postgresql/compare-postgresql-compatibility/