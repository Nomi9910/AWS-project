# Day 3 — EC2 & Compute Services

## Introduction
**Amazon EC2 (Elastic Compute Cloud)** is the backbone of AWS compute. It provides resizable virtual machines (called instances) in the cloud. Understanding EC2 pricing models is heavily tested on the exam.

---

## Amazon EC2

### What Is EC2?
- Virtual servers in the cloud
- You choose: CPU, RAM, storage, network
- Launch in minutes, pay by the second (Linux) or hour (Windows)
- Full control over the OS — you manage it (Customer Responsibility)

### EC2 Instance Types

| Family | Optimised For | Examples |
|--------|--------------|---------|
| **General Purpose** | Balanced compute/memory/network | t3, m6i |
| **Compute Optimised** | High CPU (HPC, batch, gaming) | c6i, c7g |
| **Memory Optimised** | In-memory databases, real-time analytics | r6i, x2idn |
| **Storage Optimised** | High sequential read/write, big data | i3, d3 |
| **Accelerated Computing** | GPU workloads, ML, graphics | p4, g5, inf2 |

**Naming convention:** `m5.xlarge`
- `m` = family (general purpose)
- `5` = generation
- `xlarge` = size

---

## EC2 Pricing Models (Most Tested Topic)

### 1. On-Demand Instances
- Pay by the **second** (Linux) or hour (Windows)
- No commitment, no upfront payment
- **Use when:** Short-term, unpredictable workloads, testing

### 2. Reserved Instances (RI)
- **1-year or 3-year** commitment
- Up to **72% discount** vs On-Demand
- Payment options: All Upfront, Partial Upfront, No Upfront
- **Use when:** Steady-state, predictable workloads (databases, web servers)
- **Standard RI:** Cannot change instance type
- **Convertible RI:** Can change instance attributes, lower discount (~54%)

### 3. Savings Plans
- Flexible alternative to Reserved Instances
- Commit to a **consistent amount of compute usage ($/hour)** for 1 or 3 years
- Up to **66% discount**
- Applies automatically across EC2, Lambda, Fargate

### 4. Spot Instances
- Use **unused AWS capacity**
- Up to **90% discount** vs On-Demand
- **Can be interrupted** with 2-minute warning
- **Use when:** Fault-tolerant, batch processing, data analysis, CI/CD

### 5. Dedicated Hosts
- **Physical server** dedicated to your use
- Most expensive option
- **Use when:** Compliance requirements, software licences tied to physical cores/sockets

### 6. Dedicated Instances
- Instances run on hardware dedicated to you
- May share hardware with other instances from same account

### Quick Decision Guide

| Need | Use |
|------|-----|
| Short-term, unpredictable | On-Demand |
| Predictable, 1-3 years | Reserved Instances or Savings Plans |
| Flexible savings, any workload | Savings Plans |
| Fault-tolerant, cheapest | Spot |
| Compliance/licensing | Dedicated Hosts |

---

## EC2 Key Features

### Security Groups
- Virtual **firewall** for EC2 instances
- Controls inbound and outbound traffic
- Stateful — return traffic automatically allowed
- Default: deny all inbound, allow all outbound
- Rules specify: protocol, port range, source/destination

### Key Pairs
- Used for **SSH access** to Linux instances / RDP to Windows
- Public key stored by AWS, private key downloaded by you
- You are responsible for keeping the private key safe

### User Data
- **Bootstrap script** that runs on first launch
- Used to install software, configure instance automatically
- Runs as root on Linux

### EC2 Instance Connect
- Browser-based SSH to EC2 without managing SSH keys
- Works directly from AWS Console

---

## Other AWS Compute Services

### AWS Lambda
- **Serverless** compute — run code without managing servers
- Pay only for compute time used (per 1ms)
- Triggers: API Gateway, S3 events, DynamoDB, SQS, EventBridge
- Max timeout: 15 minutes
- **Use when:** Short-lived functions, event-driven workloads

### Amazon ECS (Elastic Container Service)
- Run **Docker containers** on AWS
- Can run on EC2 (you manage) or **AWS Fargate** (serverless containers)

### Amazon EKS (Elastic Kubernetes Service)
- Managed **Kubernetes** on AWS
- Runs container workloads at scale

### AWS Fargate
- **Serverless** container hosting
- No EC2 instances to manage
- Works with ECS and EKS

### AWS Elastic Beanstalk
- **PaaS** — deploy web apps without managing infrastructure
- Supports: Node.js, Python, Java, .NET, PHP, Ruby, Go, Docker
- AWS manages: load balancing, auto scaling, health monitoring

### AWS Batch
- Run **batch computing** workloads
- Fully managed, scales automatically

### Amazon Lightsail
- Simplified cloud platform for **simple workloads**
- Fixed monthly pricing
- Best for: blogs, small websites, dev/test environments

---

## Auto Scaling & Load Balancing

### Auto Scaling Group (ASG)
- Automatically **adds or removes EC2 instances** based on demand
- Policies: Target Tracking, Step Scaling, Scheduled
- Minimum, desired, maximum capacity

### Elastic Load Balancer (ELB)
- Distributes incoming traffic across multiple targets
- Types:
  - **ALB (Application Load Balancer):** HTTP/HTTPS, Layer 7
  - **NLB (Network Load Balancer):** TCP/UDP, Layer 4, ultra-high performance
  - **GWLB (Gateway Load Balancer):** Security appliances, Layer 3

---

## Practice Questions

1. A company needs the MOST cost-effective EC2 option for a fault-tolerant batch processing job. Which pricing model should they use?
   - A) On-Demand  B) Reserved  C) Spot ✓  D) Dedicated Host

2. Which EC2 pricing option requires a 1 or 3-year commitment but offers up to 72% savings?
   - A) On-Demand  B) Spot  C) Reserved Instances ✓  D) Savings Plans

3. A developer wants to run code in response to S3 file uploads without managing servers. Which service should they use?
   - A) EC2  B) ECS  C) AWS Lambda ✓  D) Lightsail

4. Which service automatically adjusts the number of EC2 instances based on traffic?
   - A) Elastic Load Balancer  B) Auto Scaling Group ✓  C) CloudFront  D) Route 53
