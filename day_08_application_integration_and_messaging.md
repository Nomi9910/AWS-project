# Day 8 — Application Integration & Messaging Services

## Introduction
Modern cloud applications are built from loosely coupled components. AWS provides messaging, queuing, and notification services to decouple these components — ensuring scalability, reliability, and flexibility.

---

## Amazon SQS (Simple Queue Service)

### What Is SQS?
- Fully managed **message queuing** service
- Decouple and scale distributed systems
- Messages stored in the queue until a consumer processes and deletes them
- Pull-based (consumers poll the queue)

### SQS Key Concepts

| Concept | Description |
|---------|-------------|
| **Queue** | Container for messages |
| **Producer** | Sends messages to the queue |
| **Consumer** | Polls the queue and processes messages |
| **Visibility Timeout** | Time a message is hidden after being received (prevent double processing) |
| **Dead Letter Queue (DLQ)** | Queue for messages that fail processing repeatedly |
| **Message Retention** | 1 minute to 14 days (default 4 days) |
| **Max Message Size** | 256 KB |

### SQS Queue Types

| Type | Description |
|------|-------------|
| **Standard Queue** | Best-effort ordering, at-least-once delivery, unlimited throughput |
| **FIFO Queue** | Strict ordering, exactly-once processing, limited throughput (3,000 msg/s with batching) |

**Use Standard** when order doesn't matter and throughput is critical.
**Use FIFO** when order matters (order processing, financial transactions).

### SQS Use Cases
- Decouple application components
- Buffer writes to databases
- Handle traffic spikes
- Batch job processing

---

## Amazon SNS (Simple Notification Service)

### What Is SNS?
- Fully managed **pub/sub (publish-subscribe)** messaging service
- One message → pushed to **many subscribers** simultaneously
- Push-based (no polling needed)

### SNS Key Concepts
- **Topic:** Channel where messages are published
- **Publisher:** Sends messages to a topic
- **Subscriber:** Receives messages from the topic

### SNS Subscribers
- SQS queues
- AWS Lambda functions
- HTTP/HTTPS endpoints
- Email addresses
- SMS text messages
- Mobile push notifications (APNS, GCM/FCM)

### SNS Fan-Out Pattern
```
                ┌──► SQS Queue 1 → Process A
Publisher → SNS Topic ──► SQS Queue 2 → Process B
                └──► Lambda Function → Process C
```
One SNS message triggers processing by multiple services simultaneously.

---

## SQS vs SNS

| Feature | SQS | SNS |
|---------|-----|-----|
| Model | Queue (pull) | Pub/Sub (push) |
| Receivers | One consumer processes each message | Many subscribers receive each message |
| Persistence | Messages stored until consumed | No storage — delivered immediately |
| Use case | Work queue, decoupling | Notifications, fan-out |

---

## Amazon EventBridge (formerly CloudWatch Events)

- **Serverless event bus** for connecting AWS services and SaaS applications
- Responds to events from AWS services, custom apps, or third-party SaaS
- Routes events to targets (Lambda, SQS, SNS, Step Functions, etc.)

**Examples:**
- EC2 state change → notify via SNS
- S3 object upload → trigger Lambda
- Scheduled rule (cron) → run Lambda every hour
- GuardDuty finding → invoke Step Functions

---

## AWS Step Functions

- **Visual workflow** service to orchestrate multiple AWS services into serverless workflows
- Build state machines using JSON (Amazon States Language)
- Coordinates: Lambda, ECS, SQS, DynamoDB, SNS, and 200+ services
- **Use when:** Multi-step workflows, retry logic, human approval steps

---

## Amazon Kinesis

- Collect, process, and analyse **real-time streaming data**
- Components:

| Service | Purpose |
|---------|---------|
| **Kinesis Data Streams** | Real-time data ingestion for custom processing |
| **Kinesis Data Firehose** | Load streaming data to S3, Redshift, OpenSearch |
| **Kinesis Data Analytics** | Real-time SQL analysis of streaming data |
| **Kinesis Video Streams** | Stream video from connected devices |

---

## Amazon MQ

- Managed **message broker** for ActiveMQ and RabbitMQ
- Use when migrating existing on-premises message brokers to the cloud
- MQTT, AMQP, STOMP, OpenWire, WSS protocols

**vs SQS/SNS:** MQ for migrating existing brokers. SQS/SNS for new cloud-native apps.

---

## AWS AppSync

- Managed **GraphQL** API service
- Real-time data synchronisation
- Connects to DynamoDB, Lambda, Elasticsearch, HTTP

---

## Summary — Which Service When?

| Need | Service |
|------|---------|
| Queue for decoupling components | SQS |
| Push notifications to many subscribers | SNS |
| React to AWS events / schedule tasks | EventBridge |
| Multi-step workflow orchestration | Step Functions |
| Real-time data streaming | Kinesis |
| Migrate existing AMQP/MQTT broker | Amazon MQ |

---

## Practice Questions

1. A company wants to send a single notification to email, SMS, and an SQS queue simultaneously. Which service should they use?
   - A) SQS  B) SNS ✓  C) Kinesis  D) EventBridge

2. An e-commerce application needs to process orders in the exact sequence they were received. Which SQS queue type should they use?
   - A) Standard Queue  B) FIFO Queue ✓  C) Dead Letter Queue  D) Priority Queue

3. A company wants to trigger a Lambda function whenever a new EC2 instance is launched. Which service should they configure?
   - A) CloudWatch Alarm  B) SNS  C) EventBridge ✓  D) SQS

4. Which service would you use to ingest and process millions of real-time clickstream events per second?
   - A) SQS  B) SNS  C) Kinesis Data Streams ✓  D) Amazon MQ
