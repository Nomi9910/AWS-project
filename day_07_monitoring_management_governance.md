# Day 7 — Monitoring, Management & Governance

## Introduction
AWS provides powerful tools to monitor your resources, manage configuration, and ensure compliance. These services are heavily tested in Domain 3 and align with the **Operational Excellence** pillar of the Well-Architected Framework.

---

## Amazon CloudWatch

### What Is CloudWatch?
- AWS's primary **monitoring and observability** service
- Collects metrics, logs, and events from AWS services and custom applications

### CloudWatch Components

| Component | Description |
|-----------|-------------|
| **Metrics** | Numerical data over time (CPU utilisation, request count) |
| **Alarms** | Trigger actions when metrics cross thresholds |
| **Logs** | Collect, monitor, and store log files |
| **Log Groups** | Container for log streams |
| **Dashboards** | Custom visualisations of metrics |
| **Events / EventBridge** | React to changes in AWS resources |
| **Synthetics** | Monitor endpoints using canary scripts |

### CloudWatch Alarms
- Monitor a metric and perform actions:
  - Send SNS notification
  - Trigger EC2 Auto Scaling
  - Stop/terminate/reboot EC2 instance
- States: OK, ALARM, INSUFFICIENT_DATA

### CloudWatch Logs Insights
- Query and analyse log data using SQL-like syntax
- Useful for troubleshooting and security analysis

---

## AWS CloudTrail

### What Is CloudTrail?
- Records **API calls** made in your AWS account
- Answers: "Who did what, when, from where?"
- Enabled by default — trails stored in S3
- **Management Events:** Control plane operations (create EC2, delete S3 bucket)
- **Data Events:** Data plane operations (S3 object access, Lambda invocations) — optional, extra cost

### CloudTrail vs CloudWatch

| | CloudTrail | CloudWatch |
|--|-----------|------------|
| What it monitors | **API calls** and account activity | **Performance metrics** and logs |
| Who did what | ✓ | ✗ |
| CPU / network metrics | ✗ | ✓ |
| Log retention | Indefinite (in S3) | Configurable (1 day to 10 years) |

---

## AWS Config

- **Records configuration changes** to AWS resources over time
- Answers: "What did this resource look like at any point in time?"
- Checks compliance against Config Rules (e.g., "Are all EBS volumes encrypted?")
- Can trigger auto-remediation via SSM Automation or Lambda
- **Not real-time** — evaluates periodically or on change

### Config vs CloudTrail
- Config = **What** the resource configuration is/was
- CloudTrail = **Who** made the change and when

---

## AWS Organizations

### What Is AWS Organizations?
- Manage **multiple AWS accounts** from a central location
- Group accounts into **Organizational Units (OUs)**

### Key Features
| Feature | Description |
|---------|-------------|
| **Consolidated Billing** | Single payment method, combined usage for discounts |
| **Service Control Policies (SCPs)** | Restrict what services/actions accounts can use |
| **Management Account** | The master account that creates and manages the org |
| **Member Accounts** | All other accounts in the organization |

### Service Control Policies (SCPs)
- Applied at the OU or account level
- **Do NOT grant permissions** — they set maximum available permissions
- Even a user with AdministratorAccess cannot exceed the SCP boundary
- Cannot restrict the management account

---

## AWS Control Tower

- Quickly set up a **secure, multi-account AWS environment** (landing zone)
- Built on top of AWS Organizations
- Provides guardrails (preventive and detective controls)
- Dashboard to monitor compliance

---

## AWS Systems Manager (SSM)

- Manage **EC2 instances and on-premises** servers at scale
- **Key features:**

| Feature | Description |
|---------|-------------|
| **Session Manager** | Browser-based SSH/RDP without opening ports 22/3389 |
| **Patch Manager** | Automate OS and application patching |
| **Parameter Store** | Secure storage for config data and secrets |
| **Run Command** | Execute commands across many instances at once |
| **Inventory** | Collect metadata about instances |
| **State Manager** | Define and maintain desired configuration state |

---

## AWS Trusted Advisor

- Automated advisor providing **best practice recommendations**
- Five categories:

| Category | Examples |
|----------|---------|
| **Cost Optimization** | Idle EC2 instances, underutilised Reserved Instances |
| **Performance** | CloudFront configuration, EBS IOPS optimization |
| **Security** | MFA on root, open security group ports |
| **Fault Tolerance** | RDS Multi-AZ, EBS snapshots |
| **Service Limits** | Approaching service quotas |

- **Basic/Developer plans:** 7 core checks only
- **Business/Enterprise plans:** Full set of checks + API access

---

## AWS Health Dashboard

- **Service Health Dashboard:** Public status of all AWS services
- **Personal Health Dashboard:** Alerts for events affecting YOUR resources

---

## AWS Service Catalog

- Create and manage **approved IT service catalogues**
- Users deploy pre-approved, compliant resources from the catalogue
- Enforces governance and compliance

---

## Practice Questions

1. Which service would you use to determine who deleted an S3 bucket and when?
   - A) CloudWatch  B) CloudTrail ✓  C) AWS Config  D) Trusted Advisor

2. A company needs to enforce that no accounts in their AWS Organization can launch EC2 instances in a specific Region. Which should they use?
   - A) IAM Policies  B) SCPs ✓  C) CloudTrail  D) AWS Config

3. Which service provides automated best practice recommendations for cost optimization and security?
   - A) CloudWatch  B) AWS Config  C) Trusted Advisor ✓  D) Control Tower

4. A developer needs to connect to an EC2 instance without SSH keys or open port 22. Which service enables this?
   - A) EC2 Instance Connect  B) SSM Session Manager ✓  C) CloudShell  D) VPN

5. Which service records changes to AWS resource configurations over time and checks compliance?
   - A) CloudTrail  B) CloudWatch  C) AWS Config ✓  D) Systems Manager
