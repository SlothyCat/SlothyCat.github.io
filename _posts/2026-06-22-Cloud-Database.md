---
title: "Cloud Database"
date: 2026-06-22 20:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_database.jpg
    alt: Cloud Database
---

# Introduction
It is time to see what database services AWS provides. I did make use of Amazon's `DynamoDB` in my internship, so let's see if it will be mentioned.

The main benefit of AWS database is that it is **fully managed** and it handles heavy lifting tasks like **backups, patches, and high availability**. This lets the development team focus on building application features that drive business value.

We can also lift off databases and migrate them to the cloud using AWS Database Migration Service.

### Relational Database Services
Relational databases store data in a way that relates it to other pieces of data, and they use structured query language, or SQL, to manage and query data.  

#### Amazon Relational Database Service (Amazon RDS)
`RDS` handles routine database tasks such as backups, patching, and hardware provisioning. `RDS` supports multiple database engines such as `Amazon Aurora`, `MySQL`, `PostgreSQL`, `Microsoft SQL Server`, `MariaDB`, and `Oracle Database`.

#### Amazon Aurora
Amazon's own relational database is designed to help **reduce unnecessary I/O operations**. It is compatible with MySQL and PostgreSQL, providing high performance and availability. Auto scales too, normally good for games, and real-time stuff.


>Aurora provides a **high-performance, highly available** storage architecture that offers up to five times the throughput of standard MySQL.
{: .prompt-info}


### NoSQL Database Services
Ah, so here we have `DynamoDB`. Instead of row and column relationships, **NoSQL** databases build a structure for the data that they contain using _key-value pairs_ instead.

#### DynamoDB
It is a fully managed NoSQL database service. It's a powerful and incredibly fast database option for use cases that require a **flexible schema**, and is ideal for applications that require high performance and seamless scaling.


### In-Memory Cache
high-speed storage layer that _temporarily stores frequently accessed data in_ a computer's main memory, or _RAM_.

#### Amazon ElastiCache
A fully managed in-memory caching service that was built to help reduce the complexity of administering in-memory caching systems.

**Benefits**:
- High performance for `Redis`, `Valkey` or `Memcached` instances
- High Availability
- Multiple AZs
- Data Encryption


### Other Database Services

#### Amazon DocumentDB
 designed to handle **semi-structured data**, which is information that doesn't conform to rigid relational schemas. It is good for J**SON-like documents**

**Use Cases:** content management systems, catalogue and inventory management, and user profile and personalisation systems.

**Benefits:** MongoDB Compatible, Performance, Scalability, Increased read throughput


#### AWS Backup
**streamlines data protection** across various AWS resources and on-premises deployments by providing a single dashboard for monitoring and managing backups.

**Use Cases:** centralised disaster recovery, consistent backup policies for compliance requirements, and consolidating multiple backup processes through a single interface.

**Benefits:** Centralised Backup Management, Cross-Region backup redundancy, Streamlined Regulatory Compliance


#### Amazon Neptune
**manages highly connected data sets**, like those used in social networking applications. It excels at understanding complex relationships that are difficult to identify in traditional relational databases.

**Use Cases:**  social network user connection mapping, fraud detection systems, and search and recommendation systems.

**Benefits:** Built for complex relationships, high performance and scalability


# Summary
Managed to cover DynamoDB, but other than that, I also came across the relational database version and services to power the databases. There are multiple types of database services for different use cases covered here, good to know!

![alt](/assets/images/hk_pastry.jpeg)
nomnom with night city view~