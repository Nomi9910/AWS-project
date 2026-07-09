# Day 13 — Cloud Architecture & Best Practices

## Introduction
This lesson covers AWS architectural principles, disaster recovery strategies, and migration frameworks — all tested across Domains 1 and 3.

---

## AWS Well-Architected Framework (Deep Dive)

The **6 pillars** form the foundation of well-designed cloud architectures:

### 1. Operational Excellence
Design systems to **run and monitor** workloads effectively.

Key practices:
- Perform operations as code (Infrastructure as Code)
- Make frequent, small, reversible changes
- Refine operations procedures frequently
- Anticipate failure and learn from failures
- Services: CloudFormation, CodePipeline, CloudWatch

### 2. Security
**Protect information, systems, and assets** while delivering business value through risk assessments and mitigation strategies.

Key practices:
- Implement a strong identity foundation (IAM, MFA)
- Enable traceability (CloudTrail, CloudWatch Logs)
- Apply security at all layers (defence in depth)
- Automate security best practices
- Protect data in transit and at rest

### 3. Reliability
Ability to **recover from failures** and acquire computing resources dynamically.

Key practices:
- Recover from infrastructure/service disruptions
- Dynamically acquire resources to meet demand
- Mitigate disruptions from misconfiguration or transient network issues
- Services: Multi-AZ, Auto Scaling, Route 53 health checks, Backup

### 4. Performance Efficiency
Use computing resources **efficiently** to meet system requirements.

Key practices:
- Select the right resource types and sizes
- Monitor performance and make data-driven decisions
- Use serverless where possible
- Go global in minutes
- Services: CloudFront, Lambda, Aurora, ElastiCache

### 5. Cost Optimisation
**Avoid unnecessary costs** and run systems at the lowest possible price.

Key practices:
- Adopt consumption/pay-as-you-go model
- Measure overall efficiency (CloudWatch)
- Stop spending money on undifferentiated heavy lifting
- Analyse and attribute expenditure (Tags, Cost Explorer)
- Services: Savings Plans, Spot, S3 Intelligent-Tiering, Trusted Advisor

### 6. Sustainability
Minimise **environmental impact** of cloud workloads.

Key practices:
- Understand your environmental impact
- Establish sustainability goals
- Maximise utilisation (right-size, shut down idle)
- Adopt managed/serverless services (more efficient)

---

## AWS Well-Architected Tool

- Free service in the console
- Evaluate your architecture against the 6 pillars
- Produces a report with improvement recommendations

---

## High Availability & Disaster Recovery

### High Availability (HA)
System is operational and accessible as much as possible.

**Key HA services:**
- Multi-AZ RDS
- ELB + Auto Scaling
- Route 53 health checks + failover routing
- ElastiCache for Redis (multi-AZ)

### Disaster Recovery (DR) Strategies

| Strategy | RTO | RPO | Cost | Description |
|----------|-----|-----|------|-------------|
| **Backup & Restore** | Hours | Hours | $ | Take backups, restore when needed |
| **Pilot Light** | Minutes | Minutes | $$ | Minimal core infrastructure running |
| **Warm Standby** | Seconds | Seconds | $$$ | Scaled-down full system running |
| **Multi-Site/Active-Active** | Near zero | Near zero | $$$$ | Full duplicate running in another region |

**RTO** = Recovery Time Objective (how long can you be down?)
**RPO** = Recovery Point Objective (how much data can you lose?)

Lower RTO/RPO = higher cost.

---

## AWS Architecture Patterns

### Three-Tier Architecture
```
┌─────────────┐    ┌──────────────┐    ┌─────────────┐
│ Presentation │ →  │  Application │ →  │   Data      │
│  (CloudFront │    │  (EC2 + ALB  │    │  (RDS Multi │
│  + S3)      │    │  + ASG)      │    │   AZ)       │
└─────────────┘    └──────────────┘    └─────────────┘
   Public subnet    Private subnet       Private subnet
```

### Serverless Architecture
- API Gateway → Lambda → DynamoDB/S3
- No servers to manage
- Auto-scales automatically
- Pay per invocation

### Microservices Architecture
- Small, independent services
- Communicate via APIs or message queues
- ECS/EKS for containers, SQS for decoupling

---

## Cloud Migration Strategies (7 Rs)

| Strategy | Description |
|----------|-------------|
| **Retire** | Decommission — no longer needed |
| **Retain** | Keep on-premises for now |
| **Rehost** (Lift & Shift) | Move as-is to EC2 without changes |
| **Replatform** (Lift, Tinker & Shift) | Minor optimisations (RDS instead of self-managed DB) |
| **Repurchase** | Move to SaaS (Salesforce, ServiceNow) |
| **Refactor / Re-architect** | Redesign for cloud-native (microservices, serverless) |
| **Relocate** | Move to VMware Cloud on AWS |

**Most common exam question:** "What migration strategy requires the LEAST effort?" → **Rehost** (Lift & Shift)

---

## AWS Cloud Adoption Framework (CAF)

A framework to help organisations develop cloud adoption plans.

**6 Perspectives:**

| Perspective | Focus |
|------------|-------|
| **Business** | Business outcomes, ROI |
| **People** | Culture, skills, change management |
| **Governance** | Risk management, compliance |
| **Platform** | Architecture, infrastructure |
| **Security** | Identity, data protection |
| **Operations** | Monitoring, incident management |

---

## AWS Acceptable Use Policy

- Defines what you **can and cannot do** with AWS infrastructure
- Prohibited: hacking, sending spam, copyright infringement, child abuse material
- Apply to ALL users — including AWS employees

---

## Practice Questions

1. Which disaster recovery strategy keeps a minimal version of the production environment always running to reduce RTO?
   - A) Backup & Restore  B) Pilot Light ✓  C) Warm Standby  D) Multi-Site

2. A company is migrating its applications to AWS without making any changes to the code or architecture. Which migration strategy is this?
   - A) Refactor  B) Replatform  C) Rehost ✓  D) Repurchase

3. Which Well-Architected pillar focuses on recovering from infrastructure failures?
   - A) Performance Efficiency  B) Reliability ✓  C) Operational Excellence  D) Cost Optimization

4. Which migration strategy involves replacing an on-premises application with a SaaS solution?
   - A) Rehost  B) Replatform  C) Repurchase ✓  D) Refactor
