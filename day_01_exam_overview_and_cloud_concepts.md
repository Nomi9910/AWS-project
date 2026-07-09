# Day 1 — AWS Cloud Practitioner (CLF-C02): Exam Overview & Cloud Concepts

## What Is the AWS Cloud Practitioner?

The **AWS Certified Cloud Practitioner (CLF-C02)** is the entry-level AWS certification. It validates foundational knowledge of AWS Cloud services, architecture, pricing, and security — with no hands-on technical prerequisites.

**Exam Details:**
| Field | Info |
|-------|------|
| Exam Code | CLF-C02 |
| Level | Foundational |
| Duration | 90 minutes |
| Questions | 65 questions (50 scored + 15 unscored) |
| Passing Score | 700 out of 1000 |
| Cost | $100 USD |
| Format | Multiple choice & multiple response |
| Validity | 3 years |

---

## The 4 Exam Domains

| Domain | Title | Weight |
|--------|-------|--------|
| 1 | Cloud Concepts | 24% |
| 2 | Security and Compliance | 30% |
| 3 | Cloud Technology and Services | 34% |
| 4 | Billing, Pricing, and Support | 12% |

> **Domain 3 (Cloud Technology)** is the largest — focus here first.
> **Domain 2 (Security)** is second — AWS loves security questions.

---

## Domain 1: Cloud Concepts (24%)

### What Is Cloud Computing?
Cloud computing is the **on-demand delivery** of IT resources (compute, storage, networking, databases) over the internet with **pay-as-you-go pricing**.

Instead of buying and maintaining physical servers, you rent them from AWS and pay only for what you use.

### 6 Advantages of Cloud Computing (Must Memorise)

| # | Advantage | Explanation |
|---|-----------|-------------|
| 1 | **Trade capital expense for variable expense** | Pay for what you use instead of large upfront investments |
| 2 | **Benefit from massive economies of scale** | AWS aggregates millions of customers → lower prices |
| 3 | **Stop guessing capacity** | Scale up or down instantly — no over/under provisioning |
| 4 | **Increase speed and agility** | Deploy resources in minutes, not weeks |
| 5 | **Stop spending on data centres** | Focus on your business, not infrastructure maintenance |
| 6 | **Go global in minutes** | Deploy worldwide using AWS's global infrastructure |

### Cloud Deployment Models

| Model | Description | Example |
|-------|-------------|---------|
| **Public Cloud** | Resources owned and operated by AWS, shared with multiple customers | AWS, Azure, GCP |
| **Private Cloud** | Cloud resources used exclusively by one organisation | On-premises VMware |
| **Hybrid Cloud** | Mix of public and private cloud | AWS + on-premises connected via VPN |

### Cloud Service Models

| Model | What AWS Manages | What You Manage | Example |
|-------|-----------------|-----------------|---------|
| **IaaS** (Infrastructure as a Service) | Physical hardware, networking | OS, apps, data | EC2 |
| **PaaS** (Platform as a Service) | Hardware + OS + runtime | Application code, data | Elastic Beanstalk |
| **SaaS** (Software as a Service) | Everything | Nothing (just use it) | Gmail, Salesforce |

### AWS Global Infrastructure

| Component | Description |
|-----------|-------------|
| **Region** | Geographic area with 2+ Availability Zones (e.g., us-east-1, eu-west-1) |
| **Availability Zone (AZ)** | One or more data centres within a Region |
| **Edge Location** | Data centre for CloudFront CDN caching, closer to end users |
| **Local Zone** | Extension of a Region for ultra-low latency |

**How to choose a Region:**
1. **Compliance** — data sovereignty laws
2. **Proximity** — closer to users = lower latency
3. **Available services** — not all services in all regions
4. **Pricing** — varies by region

### AWS Well-Architected Framework (6 Pillars)

| Pillar | Focus |
|--------|-------|
| **Operational Excellence** | Run and monitor systems |
| **Security** | Protect data and systems |
| **Reliability** | Recover from failures, scale |
| **Performance Efficiency** | Use resources efficiently |
| **Cost Optimization** | Avoid unnecessary costs |
| **Sustainability** | Minimise environmental impact |

---

## Practice Questions

1. Which cloud deployment model combines on-premises infrastructure with AWS?
   - A) Public cloud  B) Private cloud  C) Hybrid cloud ✓  D) Community cloud

2. Which of the following is an advantage of cloud computing?
   - A) Fixed monthly pricing  B) Trade capital expense for variable expense ✓  C) Limited global reach  D) Manual scaling

3. What is an AWS Region?
   - A) A single data centre  B) A geographic area containing multiple Availability Zones ✓  C) A content delivery network  D) An edge location

4. A company wants to migrate to cloud to avoid purchasing servers. Which advantage does this represent?
   - A) Go global in minutes  B) Stop guessing capacity  C) Trade capital expense for variable expense ✓  D) Economies of scale
