# Day 5 — Databases on AWS

## Introduction
AWS offers a wide range of managed database services that eliminate the need to provision hardware, install software, or manage patching. Understanding **which database to use when** is a key exam topic.

---

## Amazon RDS (Relational Database Service)

### What Is RDS?
- Managed **relational database** service
- AWS handles: provisioning, patching, backups, monitoring
- You still choose the engine and manage the data

### Supported Engines
- MySQL, PostgreSQL, MariaDB, Oracle, Microsoft SQL Server
- **Amazon Aurora** (AWS's own high-performance engine)

### Amazon Aurora
- AWS-designed relational database — compatible with MySQL and PostgreSQL
- **5× faster than MySQL**, **3× faster than PostgreSQL**
- Storage automatically grows (up to 128 TB)
- Replicates 6 copies of data across 3 AZs
- **Aurora Serverless:** Auto-scales compute based on demand — good for unpredictable workloads

### RDS Key Features

| Feature | Description |
|---------|-------------|
| **Multi-AZ** | Standby replica in different AZ for high availability (failover) |
| **Read Replicas** | Copies for read-heavy workloads — improve performance |
| **Automated Backups** | Daily snapshots + transaction logs (point-in-time recovery) |
| **Encryption** | At rest (KMS) and in transit (TLS) |

**Multi-AZ vs Read Replicas:**
- Multi-AZ = **high availability** (failover, disaster recovery)
- Read Replicas = **performance** (scale reads, offload traffic)

---

## Amazon DynamoDB

### What Is DynamoDB?
- Fully managed **NoSQL** database (key-value and document)
- Serverless — no instances to manage
- Single-digit millisecond performance at any scale
- Automatically scales to handle any amount of traffic

### DynamoDB Key Concepts
- **Table** → Collection of items
- **Item** → A row in the table
- **Attribute** → A column/field
- **Primary Key:** Partition key (+ optional sort key)

### DynamoDB Accelerator (DAX)
- In-memory cache for DynamoDB
- Reduces response time from milliseconds → **microseconds**
- No application code changes needed

### DynamoDB Global Tables
- Multi-Region, multi-active database
- Low-latency access for globally distributed applications

---

## Amazon ElastiCache

- In-memory caching service
- Supports **Redis** and **Memcached**
- Reduces database load by caching frequent queries
- Sub-millisecond response times
- Use case: Session storage, leaderboards, caching

---

## Amazon Redshift

- Managed **data warehouse** for analytics
- Columnar storage, massively parallel processing (MPP)
- Petabyte-scale analytics
- Use: Business intelligence, reporting, data lake queries
- **Redshift Serverless:** Pay only for queries

---

## Amazon DocumentDB

- Managed **MongoDB-compatible** document database
- Stores JSON-like documents
- Fully managed, highly available

---

## Amazon Neptune

- Managed **graph database**
- Use case: Social networks, fraud detection, knowledge graphs, recommendation engines

---

## Amazon Keyspaces

- Managed **Apache Cassandra-compatible** database
- Serverless, automatically scales
- Use case: IoT data, time-series data

---

## Amazon QLDB (Quantum Ledger Database)

- Fully managed **ledger database**
- Immutable, cryptographically verifiable transaction log
- Use case: Financial records, supply chain, audit trails

---

## AWS Database Migration Service (DMS)

- Migrate databases to AWS quickly and securely
- Source database remains fully operational during migration
- Supports: homogeneous (MySQL → MySQL) and heterogeneous (Oracle → Aurora) migrations
- Also used for **continuous data replication**

---

## Database Selection Guide

| Need | Service |
|------|---------|
| Relational (MySQL, Postgres) | Amazon RDS |
| Highest performance relational | Amazon Aurora |
| NoSQL key-value / document | DynamoDB |
| In-memory cache / sessions | ElastiCache |
| Data warehouse / analytics | Redshift |
| Document (MongoDB-compatible) | DocumentDB |
| Graph database | Neptune |
| Financial ledger / audit | QLDB |
| Cassandra workloads | Keyspaces |
| Database migration | DMS |

---

## Practice Questions

1. Which AWS database service is best suited for a social network application requiring graph-based queries?
   - A) DynamoDB  B) RDS  C) Neptune ✓  D) Redshift

2. A company needs a NoSQL database with single-digit millisecond performance and no server management. Which service should they use?
   - A) RDS  B) Redshift  C) DynamoDB ✓  D) ElastiCache

3. Which RDS feature creates a database copy in a different AZ for disaster recovery?
   - A) Read Replica  B) Multi-AZ deployment ✓  C) Automated Backup  D) Enhanced Monitoring

4. A company needs to run complex SQL analytics on petabytes of data. Which service is BEST?
   - A) RDS  B) DynamoDB  C) Redshift ✓  D) ElastiCache

5. Which service would you use to reduce the load on a MySQL RDS instance by caching frequent read queries?
   - A) DAX  B) ElastiCache ✓  C) Read Replica  D) Multi-AZ
