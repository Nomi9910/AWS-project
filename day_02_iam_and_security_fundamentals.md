# Day 2 — IAM & Security Fundamentals

## Introduction
**AWS Identity and Access Management (IAM)** controls WHO can do WHAT on AWS. It is a global service — not region-specific. Understanding IAM is critical: **Domain 2 (Security)** is 30% of the exam.

---

## IAM Core Components

### Users
- Represents a **person or application** that interacts with AWS
- Each user has credentials: password (console) and/or access keys (CLI/API)
- Best practice: create individual users, never share credentials
- The **root user** is created when you open an AWS account — has full access — should be locked away and rarely used

### Groups
- A collection of IAM users
- Assign permissions to the group — all users in the group inherit those permissions
- Users can belong to multiple groups
- Groups **cannot** contain other groups

### Roles
- An IAM identity with permissions that can be **assumed** by trusted entities
- No permanent credentials — temporary security credentials issued when assumed
- Use cases:
  - EC2 instance accessing S3 (instance role)
  - Cross-account access
  - AWS services acting on your behalf (Lambda, EC2)
  - Federated users (SAML, Google login)

### Policies
- JSON documents that define what actions are allowed or denied
- Attached to users, groups, or roles
- **Effect:** Allow or Deny
- **Action:** What can be done (e.g., `s3:GetObject`)
- **Resource:** What it applies to (specific ARN or `*` for all)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

### IAM Policy Types

| Type | Description |
|------|-------------|
| **AWS Managed Policies** | Pre-built by AWS (e.g., AdministratorAccess, ReadOnlyAccess) |
| **Customer Managed Policies** | Created and managed by you |
| **Inline Policies** | Embedded directly in a user, group, or role |

---

## Principle of Least Privilege
Grant only the permissions necessary to perform a task — nothing more. This limits the blast radius if credentials are compromised.

---

## Multi-Factor Authentication (MFA)
Adds a second layer of security on top of password.

| MFA Type | Description |
|----------|-------------|
| **Virtual MFA** | Authenticator app (Google Authenticator, Authy) |
| **Hardware TOTP** | Physical device generating one-time codes |
| **FIDO Security Key** | Physical USB/NFC key (YubiKey) |

**Exam tip:** Always enable MFA on the root user account.

---

## IAM Best Practices (Exam Favourite)
1. Lock away root user access keys
2. Create individual IAM users
3. Use groups to assign permissions
4. Grant least privilege
5. Enable MFA for privileged users
6. Use IAM roles for EC2 instances and applications
7. Rotate credentials regularly
8. Use IAM Access Analyzer to review permissions

---

## AWS Security Services Overview

### AWS Shield
- Protects against **DDoS (Distributed Denial of Service)** attacks
- **Standard:** Automatic, free for all AWS customers
- **Advanced:** Paid, 24/7 DDoS response team, financial protection

### AWS WAF (Web Application Firewall)
- Protects web applications from common exploits
- Filter HTTP/HTTPS traffic based on rules
- Blocks: SQL injection, cross-site scripting (XSS)
- Works with CloudFront, ALB, API Gateway

### Amazon GuardDuty
- **Intelligent threat detection** service
- Continuously monitors AWS accounts, VPC flow logs, DNS logs, CloudTrail
- Uses ML to identify unusual activity
- No agents to install

### AWS Inspector
- **Automated security assessment** for EC2 instances and containers
- Checks for software vulnerabilities and unintended network exposure

### AWS Macie
- Uses ML to **discover and protect sensitive data** in S3
- Automatically detects PII (Personally Identifiable Information)

### AWS Security Hub
- Centralised security dashboard
- Aggregates findings from GuardDuty, Inspector, Macie, and others

---

## Shared Responsibility Model (Critical Exam Topic)

```
┌─────────────────────────────────────────────────────┐
│  CUSTOMER RESPONSIBILITY ("Security IN the cloud")  │
│  • Data encryption                                  │
│  • OS patches on EC2                                │
│  • Network/firewall configuration                   │
│  • IAM users, roles, and policies                   │
│  • Application security                             │
├─────────────────────────────────────────────────────┤
│  AWS RESPONSIBILITY ("Security OF the cloud")       │
│  • Physical data centres                            │
│  • Network infrastructure                           │
│  • Hypervisor and virtualisation                    │
│  • Managed service platforms (RDS OS patching)      │
│  • Hardware and global infrastructure               │
└─────────────────────────────────────────────────────┘
```

**Key exam pattern:** "Who is responsible for X?"
- Customer: IAM, data, OS on EC2, application code
- AWS: Physical hardware, hypervisor, managed services

---

## Practice Questions

1. Which AWS service provides intelligent threat detection using ML?
   - A) AWS Inspector  B) AWS GuardDuty ✓  C) AWS Shield  D) AWS WAF

2. Under the shared responsibility model, patching the OS on an EC2 instance is the responsibility of:
   - A) AWS  B) The customer ✓  C) Both equally  D) Neither

3. A user needs temporary access to S3 for an application running on EC2. What is the BEST solution?
   - A) Create an IAM user with access keys  B) Assign an IAM role to the EC2 instance ✓  C) Enable public access on the bucket  D) Use the root account

4. Which service protects against DDoS attacks automatically for all AWS customers at no extra charge?
   - A) AWS WAF  B) AWS Shield Advanced  C) AWS Shield Standard ✓  D) Amazon GuardDuty
