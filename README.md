# BIG-DATA-THEORY
I will dedicate this repository to share with you everything you need about Big Data.

# ARCHITECTURES IN BIG DATA
---------
They arise due to companies' need to work with increasingly large volumes of data. Before delving into the different types of data, let's understand the types of processing.

* Batch: Batch processing is a way to process large volumes of data in blocks or batches, rather than processing them continuously or in real-time. This approach is particularly useful when dealing with large datasets that do not require immediate responses, such as periodic reports, historical analysis, or tasks that do not depend on the latest available information.

* Stream: Stream processing, or real-time processing, is an approach used to analyze and process data as it is generated, rather than in blocks or batches as in batch processing.

<img width="1183" alt="Arqui" src="https://github.com/celesteg21/celesteg21/assets/112521035/a5b7c760-8954-41d2-82c9-85d269a6baf5">

## LAMBDA ARCHITECTURE:
The distinctive feature of the Lambda architecture is the combination of two processing layers:
* Batch Layer: This layer is responsible for batch processing and performs operations on large sets of historical data. It uses a durable storage system (such as a data warehouse) and batch processing tools (like Apache Hadoop) to perform analysis on historical data and generate reports.
* Speed Layer: This layer is responsible for real-time processing and handles continuous streams of data as they enter the system. It uses real-time processing systems (like Apache Storm or Apache Flink) to perform analysis and generate results in real-time.
Both layers are connected by a component called the "coordinator" or "master," which ensures that the results of real-time and batch processing are integrated and available for analytical queries.
<img width="675" alt="Captura de Pantalla 2024-01-19 a la(s) 13 35 02" src="https://github.com/celesteg21/celesteg21/assets/112521035/02d4e617-d1dd-4bb6-8236-677a991d149b">

## Key Features and Components of the Lambda Architecture:
* Raw Data: Original and unprocessed data is stored in a large-scale data repository, commonly known as a Data Lake. This repository serves as the primary data source for both batch processing and real-time processing.
* Batch Layer: It uses batch processing tools (like Apache Hadoop and MapReduce) to perform analysis on large sets of historical data stored in the Data Lake.
* Speed Layer: It uses real-time processing systems (like Apache Storm, Apache Flink, or Spark Streaming) to perform real-time analysis of data streams entering the system.
Coordinator: Ensures that the results from both layers are integrated and available for analytical queries. There may be an additional storage layer to consolidate the results.

## KAPPA ARCHITECTURE:
It is an alternative design model to the Lambda architecture in the realm of real-time data processing. The Kappa architecture was proposed by Jay Kreps, one of the creators of Apache Kafka, as a simplification of the Lambda architecture, eliminating the distinction between real-time processing and batch processing. Unlike Lambda, which has separate layers for batch and real-time processing, Kappa addresses both types of processing using a single real-time data stream.

<img width="814" alt="Captura de Pantalla 2024-01-19 a la(s) 13 36 28" src="https://github.com/celesteg21/celesteg21/assets/112521035/914e33b0-f5a2-40c8-9846-944243c3548c">

- Data Ingestion:
Data is ingested into the system through an input channel. Apache Kafka is commonly used in Kappa architectures as a messaging system for event ingestion. Kafka enables the real-time publication and subscription of events.

- Real-Time Processing:
Events enter the real-time processing system, which can be implemented using technologies like Apache Flink, Apache Samza, or Apache Storm. These systems process events continuously as they arrive, performing operations such as filtering, transformation, and real-time analysis.

Results of real-time processing are emitted and can be stored in a durable storage system or simply in a changelog, such as Kafka.

- Result Storage:
Results of real-time processing are stored in a durable storage system, which can be a distributed file system, a database, or any other persistent medium. It's essential to note that in Kappa, the durable storage system can also be used as a source for future processing, creating a closed loop in the data flow.

- Query and Analysis:
Stored results can be queried and analyzed to generate reports or feed applications that require access to historical or real-time data. With a single data stream, there's no need to differentiate between batch and real-time processing at this stage. All analysis is performed on the same dataset.

## APACHE KAFKA:
Apache Kafka is a distributed streaming platform designed to manage real-time data streams. Originally developed by LinkedIn, it later became an open-source project of the Apache Software Foundation. Kafka provides a robust and scalable architecture for the ingestion, storage, and processing of real-time data. Here are some key aspects of Apache Kafka:

* Producer: Responsible for sending messages to Kafka topics. It can be an application or a system that generates events.
* Topic: A category or channel of messages in Kafka. Producers send messages to a topic, and consumers read messages from a specific topic.
* Consumer: An application or system that subscribes to a topic and processes messages sent to that topic. Consumers can be grouped to scale and share the load.
* Message Persistence:
Kafka stores messages in an immutable and sequential log. This provides data persistence, meaning messages are not lost even if all consumers have processed the message.
* Scalability and Fault Tolerance:
Kafka can be horizontally scaled to handle large volumes of events and provides fault tolerance. Data replication between nodes ensures message availability and durability.
* Streams and Event Processing:
Kafka Streams is a built-in library in Kafka that enables real-time event processing. It allows developers to build applications that can process and transform event streams directly within the system.
* Integration with Big Data Ecosystem:
Kafka integrates well with other big data technologies such as Apache Hadoop and Apache Spark. This enables a Lambda or Kappa architecture for batch or real-time data processing.
* Order and Time Guarantees:
Kafka ensures the order of messages within a partition and allows consumers to process events in a specified order. It also provides features to manage time-based events.
* Community and Enterprise Support:
Kafka has a large community of users and developers. Additionally, there are vendors offering enterprise support for critical implementations.
Moreover, we can add features such as its development in Scala, availability of connectors for integration with JMS, support for implementing producers/consumers in different languages like Java, Scala, Python, Ruby, C++, etc.

<img width="602" alt="Captura de Pantalla 2024-01-19 a la(s) 13 38 35" src="https://github.com/celesteg21/celesteg21/assets/112521035/328c3257-43e2-4c4f-9247-3197c994da89">

## APACHE FLINK
Apache Flink is a framework for real-time and batch data processing designed to perform advanced analytics and event processing in distributed environments. Unlike Apache Kafka, which is an event messaging and streaming system, Apache Flink focuses on processing and analyzing real-time data streams and also supports batch processing.
Some key features of Apache Flink include:
Data Stream Programming Model:
   - Flink uses a stream processing-based programming model. This means it can process data as it arrives, enabling real-time analysis of events.
Real-Time and Batch Data Processing:
   - Flink is known for its ability to handle both real-time data streams and batch datasets. This provides flexibility for developers to perform analysis on historical and real-time data using the same platform.
Machine Learning (ML) Library:
   - Flink ML provides a library for performing machine learning tasks on real-time data streams and batch datasets.
Low Latency and High Fault Tolerance:
   - Flink is designed to offer low latency and high fault tolerance. It can scale horizontally to handle large volumes of data and provides recovery mechanisms in case of failures.
Integration with Big Data Ecosystem:
   - Flink integrates with the big data ecosystem, including storage systems like Apache Hadoop Distributed File System (HDFS) and messaging systems like Apache Kafka.
Java and Scala APIs:
   - Flink provides APIs in Java and Scala, making it easy for developers to build real-time and batch data processing applications.
Compatibility with SQL and Table API:
   - Flink supports SQL queries through Flink SQL and the Table API, allowing users to perform analysis using familiar query languages.
State Persistence:
   - Flink efficiently manages the intermediate state of operations, allowing applications to recover state in case of failure and continue processing data without loss of information.
Apache Flink is used in various applications, such as real-time data analytics, streaming event processing, anomaly detection, time series data processing, and more. Its flexibility and advanced capabilities make it a popular choice for use cases that require complex data processing and real-time analysis.

# Now, let's talk about Databases.
--------------------

Databases are organized systems designed to collect, store, manage, and access large amounts of structured data. They are used to efficiently store information and enable its quick and precise retrieval and manipulation. Databases play a crucial role in a wide variety of applications and computer systems. Here are some key concepts related to databases:

1. Data:
   - Data are objective facts that describe events, entities, or information. They can be of different types, such as text, numbers, dates, images, etc.

2. Database:
   - A database is an organized collection of data stored electronically in a computer system. It is designed to be efficient in retrieving and manipulating data.

3. Database Management System (DBMS):
   - A DBMS is software that provides an interface to interact with the database. It facilitates the creation, updating, and management of databases. Examples include MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server, and MongoDB.

4. Tables:
   - In a relational database, data is organized into tables, consisting of rows and columns. Each row represents a record, and each column represents an attribute.

5. Records:
   - A record is a row in a table containing specific data. Each record represents an individual data instance.

6. Fields or Attributes:
   - Fields or attributes are the columns of a table and represent the properties or characteristics of stored data.

7. Primary Keys:
   - A primary key is a field or set of fields that uniquely identifies each record in a table. It helps ensure data integrity and uniqueness.

8. Queries:
   - Queries are instructions used to retrieve, update, or manipulate data in a database. They are performed using query languages like SQL (Structured Query Language).

10. Normalization:
    - Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity.

11. Transactions:
    - A transaction is a sequence of operations performed as a single, indivisible unit. Databases ensure the atomicity, consistency, isolation, and durability (ACID) of transactions.

Databases are essential in a variety of applications, from business systems and websites to mobile applications and content management systems. They provide an efficient and structured means to store and retrieve data, facilitating the management and analysis of information in computer systems.

There are various types of databases, and the choice of database type depends on the specific requirements of the application and the characteristics of the data. Some of the most common types of databases include:

### Relational Databases (RDBMS):
In a relational database, data is organized into tables with rows and columns. Each table has a primary key that uniquely identifies each record. Examples of relational database management systems (RDBMS) include MySQL, PostgreSQL, Oracle Database, and Microsoft SQL Server.

### Non-Relational Databases (NoSQL):
NoSQL databases are used to store and manage data that doesn't fit well into a relational model. These can include document databases, key-value databases, graph databases, and column databases. Examples of NoSQL systems are MongoDB, Cassandra, Redis, and Neo4j.

- Key-Value Databases:
Store pairs of keys and values. They are efficient for fast read and write operations. Examples include Redis and DynamoDB.

- Column Databases:
Store data in columns rather than rows, which is efficient for analytical operations and aggregation queries. Apache Cassandra is an example of a column database.

- Graph Databases:
Store data in the form of nodes and relationships, useful for modeling and querying related data. Examples include Neo4j and Amazon Neptune.

SQL (Structured Query Language) and NoSQL (Not Only SQL) databases are two main categories of database management systems with distinctive approaches and features. Here are some key differences between SQL and NoSQL databases:

**SQL Databases:**
1. **Data Model:**
   - SQL is based on a relational model, where data is organized into tables with rows and columns. Each table has a primary key to uniquely identify each record.

2. **Fixed Schema:**
   - SQL databases have a fixed and predefined schema, meaning the structure of the database (tables, fields, and data types) must be defined before inserting data.

3. **Referential Integrity:**
   - They maintain referential integrity using foreign keys to establish relationships between tables.

4. **ACID Transactions:**
   - Adherence to ACID properties (Atomicity, Consistency, Isolation, Durability) to ensure data consistency.

5. **SQL Language:**
   - Uses SQL as a query language to perform operations such as SELECT, INSERT, UPDATE, and DELETE.

6. **Vertical Scalability:**
   - Vertical scalability (increasing capacity on a single server) is a common option to improve performance.

7. **Examples:**
   - MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server.

**NoSQL Databases:**
1. **Varied Data Model:**
   - NoSQL encompasses various data models such as document, key-value, columnar, and graph databases, offering flexibility in data representation.

2. **Dynamic Schema:**
   - NoSQL generally allows a dynamic schema, meaning data can be inserted without the need to define the database structure beforehand.

3. **Horizontal Scalability:**
   - Designed to scale horizontally, meaning additional nodes can be added to handle increasing volumes of data and traffic.

4. **No ACID Guarantee:**
   - NoSQL does not guarantee all ACID properties in all operations. Some NoSQL databases choose to offer less strict guarantees in favor of improved performance and scalability.

5. **Proprietary Query Languages:**
   - There is no standard query language like SQL for NoSQL. Each system may have its own set of operations and commands.

6. **Examples:**
   - MongoDB (document), Cassandra (key-value), Redis (key-value), Neo4j (graph).

**Considerations for Choosing:**
- **Data Complexity:** If the data is structured, and relationships are clear, a SQL database may be suitable. If the data is more varied and lacks a fixed structure, NoSQL might be more appropriate.

- **Scalability:** If horizontal scalability is anticipated, NoSQL is often a preferred choice.

- **Schema Flexibility:** If schema requirements change frequently or if working with semi-structured or unstructured data, NoSQL can be more flexible.

- **Consistency vs. Performance:** SQL databases tend to prioritize consistency, while some NoSQL databases may prioritize performance and availability.
