# Day 10 — AWS Pricing, Billing & Cost Management

## Introduction
**Domain 4 (Billing, Pricing, and Support)** is 12% of the exam. Understanding AWS pricing models, cost management tools, and support plans is essential.

---

## AWS Pricing Fundamentals

### Three Pricing Drivers

| Driver | Description |
|--------|-------------|
| **Compute** | Amount of compute time used (per second/hour) |
| **Storage** | Amount of data stored (per GB per month) |
| **Data Transfer** | Data transferred OUT of AWS (IN is free) |

### Key Pricing Principles
- **Pay as you go:** No upfront costs, pay only for what you use
- **Pay less when you reserve:** Commit to 1 or 3 years for discounts
- **Pay less with more use:** Volume discounts (e.g., S3 tiered pricing)
- **Pay even less as AWS grows:** AWS passes economies of scale savings to customers
- **Data transfer IN is always free**
- **Data transfer BETWEEN regions costs money**
- **Data transfer within the same AZ is free**

---

## AWS Free Tier

Three types of Free Tier offers:

| Type | Description | Example |
|------|-------------|---------|
| **Always Free** | Never expires | Lambda (1M requests/month), DynamoDB (25 GB) |
| **12 Months Free** | Free for first 12 months after sign-up | EC2 t2.micro (750 hrs/month), S3 (5 GB) |
| **Trials** | Short-term trial period | SageMaker (2 months), Lightsail (3 months) |

---

## AWS Cost Management Tools

### AWS Pricing Calculator
- **Estimate costs** before deploying
- Model different scenarios and service configurations
- Build cost estimates for new architectures
- URL: calculator.aws

### AWS Cost Explorer
- **Visualise and analyse** historical and current AWS spending
- Identify cost trends, outliers, and optimisation opportunities
- Forecast future costs (up to 12 months)
- Filter by service, region, account, tag

### AWS Budgets
- Set **custom cost and usage budgets**
- Receive alerts when you approach or exceed thresholds
- Types:
  - Cost Budget: Alert at $ amount
  - Usage Budget: Alert at service usage level
  - Savings Plans/RI Coverage Budget
- Can trigger automated actions (stop EC2, restrict IAM)

### AWS Cost and Usage Report (CUR)
- Most **comprehensive billing data** available
- Hourly or daily reports stored in S3
- Used for detailed analysis in Athena or QuickSight

### AWS Billing Dashboard
- Summary of current month's charges
- Month-to-date spend by service
- Forecasted end-of-month charges

---

## AWS Consolidated Billing

- Feature of **AWS Organizations**
- Single payment method for all accounts in the organisation
- One invoice for all accounts
- **Volume discounts:** Combined usage counts for pricing tiers
- **Reserved Instance sharing:** Accounts in org share RI benefits
- Management account pays for all member accounts

---

## Cost Optimisation Strategies

### 1. Right-Sizing
- Match instance type to actual workload requirements
- Use CloudWatch metrics to find underutilised resources
- Tools: Trusted Advisor, Compute Optimizer

### 2. Savings Plans & Reserved Instances
- Commit to consistent usage for 1–3 years
- Up to 72% savings on EC2, Lambda, Fargate

### 3. Spot Instances
- Interrupt-tolerant workloads
- Up to 90% discount

### 4. S3 Intelligent-Tiering
- Auto-move data to cheaper tiers when not accessed

### 5. Turn Off Unused Resources
- Schedule non-production environments to stop after hours
- Delete unattached EBS volumes, idle load balancers

### 6. Tags for Cost Allocation
- Apply tags to resources (Environment: Prod, Team: Engineering)
- View costs broken down by tag in Cost Explorer

---

## AWS Support Plans

| Plan | Cost | Features |
|------|------|---------|
| **Basic** | Free | 24/7 customer service, documentation, forums, Trusted Advisor (7 checks) |
| **Developer** | $29+/month | Business hours email support, 1 contact, 12–24hr response |
| **Business** | $100+/month | 24/7 phone/chat/email, full Trusted Advisor, < 1hr response for critical |
| **Enterprise On-Ramp** | $5,500+/month | Pool of TAMs, 30-min response for critical issues |
| **Enterprise** | $15,000+/month | Dedicated TAM, 15-min response, Concierge support, Well-Architected reviews |

### Technical Account Manager (TAM)
- Available in Enterprise On-Ramp and Enterprise plans
- Proactive guidance, architectural reviews, relationship management

### AWS Concierge Support
- Only on Enterprise plan
- Account and billing specialist
- Helps with billing queries and account management

---

## AWS Marketplace

- Digital catalogue to **buy and sell** software running on AWS
- 3rd-party applications: security, networking, ML, data, DevOps tools
- Pay via AWS billing — no separate invoices
- Options: BYOL (Bring Your Own Licence), hourly pricing, annual subscriptions

---

## AWS Partner Network (APN)

| Partner Type | Description |
|-------------|-------------|
| **Consulting Partners** | Help design, build, migrate on AWS (system integrators, MSPs) |
| **Technology Partners** | Software products that work with AWS |
| **ISV (Independent Software Vendor)** | Build software on/for AWS |

---

## Practice Questions

1. Which AWS service allows you to set alerts when your AWS spending exceeds a defined threshold?
   - A) Cost Explorer  B) AWS Budgets ✓  C) Billing Dashboard  D) Pricing Calculator

2. Which AWS support plan includes a dedicated Technical Account Manager (TAM)?
   - A) Developer  B) Business  C) Enterprise ✓  D) Basic

3. A startup wants to estimate the monthly cost of a new architecture before building it. Which tool should they use?
   - A) Cost Explorer  B) AWS Budgets  C) AWS Pricing Calculator ✓  D) Trusted Advisor

4. Under consolidated billing in AWS Organizations, which of the following is a benefit?
   - A) Each account gets separate discounts  B) Combined usage qualifies for volume pricing discounts ✓  C) Reserved Instances cannot be shared  D) Each account gets its own support plan

5. Data transfer FROM the internet INTO AWS (ingress) is:
   - A) Always charged  B) Free ✓  C) Free only for S3  D) Free only for EC2
