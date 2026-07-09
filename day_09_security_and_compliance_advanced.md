# Day 9 — Advanced Security & Compliance

## Introduction
Security is the **largest domain** at 30% of the exam. This lesson covers encryption, key management, compliance frameworks, and additional security services beyond IAM.

---

## Encryption Concepts

### Encryption Types

| Type | When Encrypted | Key Holder |
|------|----------------|------------|
| **Encryption at Rest** | Data stored on disk, S3, databases | Customer or AWS |
| **Encryption in Transit** | Data moving over network | TLS/SSL certificates |
| **Client-Side Encryption** | Encrypted before sending to AWS | Customer only |

### Encryption Keys
- **Symmetric:** Same key for encrypt/decrypt (AES-256)
- **Asymmetric:** Public key encrypts, private key decrypts (RSA, TLS certificates)

---

## AWS KMS (Key Management Service)

### What Is KMS?
- Managed service to **create and control encryption keys**
- Integrated with most AWS services (S3, EBS, RDS, DynamoDB, etc.)
- All KMS API calls logged in CloudTrail

### Key Types

| Key Type | Description |
|----------|-------------|
| **AWS Managed Keys** | Created and managed by AWS (free, automatic rotation) |
| **Customer Managed Keys (CMK)** | Created by you (annual rotation optional, $1/month/key) |
| **Customer Provided Keys (SSE-C)** | You provide the key, AWS uses it but doesn't store it |

### S3 Encryption Options

| Method | Key Management |
|--------|---------------|
| **SSE-S3** | AWS manages keys (default, free) |
| **SSE-KMS** | Keys managed in KMS (audit in CloudTrail) |
| **SSE-C** | Customer provides key per request |
| **Client-Side** | Encrypt before uploading |

---

## AWS CloudHSM

- **Dedicated Hardware Security Module** in the AWS cloud
- You manage the encryption keys entirely (AWS has no access)
- FIPS 140-2 Level 3 compliance
- Use when: Strict regulatory requirements, need to own your keys completely

**KMS vs CloudHSM:**
- KMS = AWS manages HSM infrastructure, you manage keys
- CloudHSM = You manage the HSM and keys entirely

---

## AWS Certificate Manager (ACM)

- Manage **SSL/TLS certificates** for HTTPS
- Provision, manage, and deploy certificates
- Free for certificates used with AWS services (ALB, CloudFront, API Gateway)
- Auto-renewal
- **Cannot** export the certificate private key

---

## AWS Secrets Manager

- Securely **store, rotate, and retrieve** credentials (database passwords, API keys)
- Automatic secret rotation (integrated with RDS, Redshift, DocumentDB)
- Costs $0.40 per secret per month
- Applications retrieve secrets via API — no hardcoded credentials

**vs SSM Parameter Store:**
- Secrets Manager: Automatic rotation, higher cost, true secrets
- Parameter Store: Config data, simpler, lower cost (free tier available)

---

## AWS Artifact

- **Self-service portal** for on-demand access to AWS compliance documentation
- Download: SOC reports, PCI DSS attestation, ISO certifications, GDPR data processing agreement
- Free service
- Useful for auditors and compliance teams

---

## AWS Compliance Programs

AWS maintains compliance with many standards and frameworks:

| Standard | Domain |
|----------|--------|
| **SOC 1, 2, 3** | Financial, security, availability controls |
| **PCI DSS Level 1** | Payment card industry |
| **HIPAA** | US healthcare data |
| **ISO 27001** | Information security management |
| **GDPR** | EU data privacy |
| **FedRAMP** | US government |
| **FIPS 140-2** | Cryptographic modules |

**Key point:** AWS maintains the certifications. Customers build **on top of** AWS's compliant infrastructure.

---

## Amazon Cognito

- Manage **user authentication** for web and mobile applications
- **User Pools:** Directory of users (sign-up, sign-in, MFA, social login)
- **Identity Pools:** Grant AWS credentials to authenticated users
- Supports: Username/password, Google, Facebook, Apple, SAML, OpenID Connect

---

## AWS Single Sign-On (IAM Identity Center)

- Centrally manage **SSO access** to multiple AWS accounts and business applications
- Integrates with: Microsoft Active Directory, Google Workspace, Okta
- One login → access to all authorised accounts and apps

---

## Amazon Detective

- Analyses and investigates **security findings** using ML and graphs
- Aggregates data from CloudTrail, VPC Flow Logs, GuardDuty
- Helps root-cause analysis of security incidents
- Visualises relationships between entities

---

## AWS Network Firewall

- Managed **stateful network firewall** for VPCs
- Supports: stateful and stateless inspection, IPS, URL filtering
- More powerful than NACLs and Security Groups

---

## Security Services Summary

| Service | Purpose |
|---------|---------|
| IAM | Identity and access management |
| KMS | Encryption key management |
| CloudHSM | Dedicated HSM hardware |
| ACM | SSL/TLS certificates |
| Secrets Manager | Secure secret storage + rotation |
| GuardDuty | Threat detection (ML) |
| Inspector | Vulnerability assessment |
| Macie | S3 sensitive data discovery |
| Shield | DDoS protection |
| WAF | Web application firewall |
| Cognito | App user authentication |
| Detective | Security incident investigation |
| Security Hub | Centralised security findings |
| Artifact | Compliance documentation |

---

## Practice Questions

1. Which service should a company use to store and automatically rotate database passwords?
   - A) SSM Parameter Store  B) AWS Secrets Manager ✓  C) KMS  D) CloudHSM

2. A company needs to download AWS PCI DSS compliance reports for their auditors. Which service provides this?
   - A) AWS Config  B) Trusted Advisor  C) AWS Artifact ✓  D) Security Hub

3. An application needs to encrypt data in S3 using customer-managed keys with full audit logging. Which encryption method should they use?
   - A) SSE-S3  B) SSE-C  C) SSE-KMS ✓  D) Client-side encryption

4. Which service would you use to add sign-up and sign-in functionality to a mobile app, including social login with Google?
   - A) IAM  B) AWS SSO  C) Amazon Cognito ✓  D) Directory Service
