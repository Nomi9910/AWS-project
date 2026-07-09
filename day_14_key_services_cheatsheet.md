# Day 14 — Complete AWS Services Cheatsheet

## All 200+ AWS Services on One Reference Sheet
> Focus on the services most likely to appear on CLF-C02. Know the use case, not the implementation details.

---

## Compute

| Service | One-Line Description |
|---------|---------------------|
| **EC2** | Virtual machines in the cloud |
| **Lambda** | Run code without servers (event-driven, 15-min max) |
| **ECS** | Run Docker containers on AWS |
| **EKS** | Managed Kubernetes |
| **Fargate** | Serverless containers (works with ECS/EKS) |
| **Elastic Beanstalk** | PaaS — deploy apps without managing infrastructure |
| **Lightsail** | Simplified, fixed-price virtual servers |
| **Batch** | Run batch computing at any scale |
| **App Runner** | Deploy containerised apps without infrastructure |
| **Outposts** | Run AWS infrastructure on-premises |

---

## Storage

| Service | One-Line Description |
|---------|---------------------|
| **S3** | Object storage — unlimited files, pay per GB |
| **EBS** | Block storage attached to EC2 (like a hard drive) |
| **EFS** | Managed shared file system for Linux (many EC2s) |
| **FSx** | Managed Windows file server / Lustre HPC storage |
| **Storage Gateway** | Hybrid storage connecting on-premises to S3 |
| **Snowcone** | Portable 14 TB data transfer device |
| **Snowball Edge** | 80 TB+ data migration device |
| **Snowmobile** | 100 PB data migration (shipping container) |
| **S3 Glacier** | Long-term archive storage |

---

## Databases

| Service | One-Line Description |
|---------|---------------------|
| **RDS** | Managed relational databases (MySQL, PostgreSQL, etc.) |
| **Aurora** | AWS's high-performance relational DB (MySQL/PG compatible) |
| **DynamoDB** | Serverless NoSQL key-value/document database |
| **ElastiCache** | In-memory caching (Redis, Memcached) |
| **Redshift** | Petabyte-scale data warehouse for analytics |
| **DocumentDB** | Managed MongoDB-compatible document database |
| **Neptune** | Managed graph database |
| **QLDB** | Immutable ledger database for financial records |
| **Keyspaces** | Managed Apache Cassandra database |
| **DMS** | Migrate databases with minimal downtime |
| **DAX** | In-memory cache specifically for DynamoDB |

---

## Networking

| Service | One-Line Description |
|---------|---------------------|
| **VPC** | Isolated virtual network in AWS |
| **CloudFront** | CDN — cache content at 400+ edge locations globally |
| **Route 53** | Managed DNS with health checking and routing policies |
| **API Gateway** | Create, manage, and secure APIs at any scale |
| **Direct Connect** | Dedicated private connection from data centre to AWS |
| **Site-to-Site VPN** | Encrypted VPN tunnel over the internet |
| **Transit Gateway** | Hub to connect many VPCs and on-premises networks |
| **Global Accelerator** | Improve performance using AWS global network |
| **ELB** | Distribute traffic across multiple targets |
| **NAT Gateway** | Allow private subnet outbound internet access |

---

## Security & Identity

| Service | One-Line Description |
|---------|---------------------|
| **IAM** | Control WHO can do WHAT on AWS |
| **KMS** | Create and manage encryption keys |
| **CloudHSM** | Dedicated hardware for encryption key management |
| **ACM** | Manage SSL/TLS certificates |
| **Secrets Manager** | Store and auto-rotate passwords and API keys |
| **GuardDuty** | ML-based threat detection (monitors CloudTrail, VPC, DNS) |
| **Inspector** | Automated vulnerability assessment for EC2 + containers |
| **Macie** | Discover and protect sensitive data (PII) in S3 |
| **Shield** | DDoS protection (Standard=free, Advanced=paid) |
| **WAF** | Web application firewall (blocks SQLi, XSS) |
| **Cognito** | User authentication for web/mobile apps |
| **Security Hub** | Centralised security findings from all services |
| **Detective** | Investigate security incidents with ML + graphs |
| **Artifact** | Download AWS compliance reports and agreements |
| **IAM Identity Center** | Centralised SSO for multiple AWS accounts |

---

## Monitoring & Management

| Service | One-Line Description |
|---------|---------------------|
| **CloudWatch** | Metrics, logs, alarms, dashboards |
| **CloudTrail** | Audit log of all API calls in your account |
| **AWS Config** | Record resource configurations and check compliance |
| **Trusted Advisor** | Best practice recommendations (cost, security, perf) |
| **Systems Manager** | Manage EC2 and on-premises at scale |
| **Organizations** | Manage multiple AWS accounts centrally |
| **Control Tower** | Set up secure multi-account environment |
| **Health Dashboard** | AWS service status + your account health |
| **Service Catalog** | Catalogue of approved IT services |

---

## Application Integration

| Service | One-Line Description |
|---------|---------------------|
| **SQS** | Message queue to decouple components |
| **SNS** | Pub/sub notifications to many subscribers |
| **EventBridge** | Serverless event bus — react to events |
| **Step Functions** | Orchestrate multi-step serverless workflows |
| **Kinesis** | Real-time data streaming and processing |
| **MQ** | Managed message broker (ActiveMQ, RabbitMQ) |
| **AppSync** | Managed GraphQL API |

---

## Developer Tools

| Service | One-Line Description |
|---------|---------------------|
| **CodeCommit** | Managed Git repository (private) |
| **CodeBuild** | Managed build and test service |
| **CodeDeploy** | Automated code deployment |
| **CodePipeline** | CI/CD pipeline orchestration |
| **CloudFormation** | Infrastructure as Code (JSON/YAML) |
| **CDK** | Infrastructure as Code using programming languages |
| **SAM** | Serverless Application Model framework |
| **Cloud9** | Browser-based IDE |
| **X-Ray** | Distributed tracing for applications |
| **CodeWhisperer** | AI code suggestions as you type |
| **Amplify** | Build and deploy full-stack mobile/web apps |

---

## AI/ML

| Service | One-Line Description |
|---------|---------------------|
| **Rekognition** | Image/video analysis |
| **Textract** | Extract text and data from documents |
| **Transcribe** | Speech to text |
| **Polly** | Text to speech |
| **Translate** | Language translation |
| **Comprehend** | NLP — sentiment, entities, key phrases |
| **Lex** | Build conversational chatbots |
| **Kendra** | Intelligent enterprise search |
| **Personalize** | Personalised recommendations |
| **Forecast** | Time-series forecasting |
| **Fraud Detector** | Detect online fraud |
| **SageMaker** | End-to-end ML platform |
| **Bedrock** | Access foundation models for Gen AI |
| **Q** | Gen AI assistant for business and developers |

---

## Analytics

| Service | One-Line Description |
|---------|---------------------|
| **Athena** | Query S3 data with SQL (serverless) |
| **EMR** | Managed big data (Hadoop, Spark) |
| **Glue** | Serverless ETL (extract, transform, load) |
| **QuickSight** | Business intelligence and visualisation dashboards |
| **Lake Formation** | Build and secure data lakes on S3 |
| **OpenSearch** | Search and analytics (Elasticsearch successor) |
| **Data Exchange** | Subscribe to third-party data |

---

## Migration

| Service | One-Line Description |
|---------|---------------------|
| **MGN** | Lift-and-shift server migration |
| **DMS** | Database migration |
| **Migration Hub** | Central migration tracking |
| **Application Discovery** | Discover on-premises infrastructure |
| **Transfer Family** | SFTP/FTP/FTPS transfers to S3/EFS |

---

## End-User Computing

| Service | One-Line Description |
|---------|---------------------|
| **WorkSpaces** | Managed virtual desktops (DaaS) |
| **AppStream 2.0** | Stream desktop applications to browsers |
| **WorkDocs** | Managed document collaboration |

---

## Cost Management

| Service | One-Line Description |
|---------|---------------------|
| **Cost Explorer** | Visualise and analyse spending trends |
| **Budgets** | Set alerts when spending exceeds thresholds |
| **Pricing Calculator** | Estimate costs before deploying |
| **Cost and Usage Report** | Most detailed billing data |
| **Savings Plans** | Flexible discount for consistent usage |

---

## Quick Decision Tables

### "Which service detects X?"
| Threat | Service |
|--------|---------|
| DDoS | AWS Shield |
| Web application attacks | WAF |
| Unusual account activity (ML) | GuardDuty |
| PII in S3 | Macie |
| Software vulnerabilities on EC2 | Inspector |
| Security incidents (investigate) | Detective |

### "Who is responsible for X?"
| Task | Responsible |
|------|-------------|
| Physical server hardware | AWS |
| Patching RDS database engine | AWS |
| Patching OS on EC2 | Customer |
| IAM user management | Customer |
| Data encryption in S3 | Customer |
| Network infrastructure | AWS |
| Application code | Customer |
