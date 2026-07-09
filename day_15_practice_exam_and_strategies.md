# Day 15 — Practice Exam & Exam Strategies

## Exam Day Checklist

```
BEFORE THE EXAM:
□ Valid government-issued photo ID
□ Know your exam appointment time and location (or online proctoring setup)
□ Quiet room for online proctoring (no papers, phones, extra monitors)
□ 90 minutes — 65 questions (50 scored + 15 unscored pilot)
□ Passing score: 700 / 1000

STRATEGY:
□ Read the FULL question before reading answers
□ Identify key words: "MOST cost-effective", "BEST", "LEAST effort"
□ Eliminate obviously wrong answers first
□ AWS favours managed services over self-managed
□ AWS favours serverless and scalable solutions
□ AWS is NEVER responsible for customer data, OS on EC2, or IAM
□ Never change your first answer unless you're certain
□ Flag and come back to uncertain questions
□ All 65 questions must be answered — no penalty for guessing
```

---

## 50 Practice Questions (Full Exam Simulation)

### Domain 1 — Cloud Concepts (24%)

**1.** A company wants to eliminate the cost of maintaining on-premises servers. Which cloud benefit does this represent?
- A) Go global in minutes  B) Increase speed and agility  C) Stop spending on data centres ✓  D) Trade variable for capital expense

**2.** Which AWS infrastructure component is a single data centre or group of data centres within a Region?
- A) Region  B) Edge Location  C) Availability Zone ✓  D) Local Zone

**3.** Which cloud model allows a company to use both on-premises infrastructure and AWS services together?
- A) Public Cloud  B) Private Cloud  C) Community Cloud  D) Hybrid Cloud ✓

**4.** Which AWS Well-Architected pillar focuses on using resources efficiently while reducing costs?
- A) Reliability  B) Performance Efficiency  C) Cost Optimization ✓  D) Operational Excellence

**5.** A startup wants to scale its application globally without investing in data centres around the world. Which advantage does cloud computing offer?
- A) Economies of scale  B) Go global in minutes ✓  C) Stop guessing capacity  D) Pay less with more use

---

### Domain 2 — Security and Compliance (30%)

**6.** Which AWS service would automatically detect if an IAM user is making API calls from an unusual geographic location?
- A) AWS Config  B) CloudTrail  C) Amazon GuardDuty ✓  D) AWS Inspector

**7.** A company needs to ensure that no member account in their AWS Organization can launch resources in the ap-southeast-2 Region. Which feature enforces this?
- A) IAM Permission Boundary  B) Resource-based Policy  C) Service Control Policy ✓  D) IAM Role

**8.** Under the AWS Shared Responsibility Model, which of the following is the customer's responsibility?
- A) Patching the hypervisor  B) Physical security of data centres  C) Managing IAM users and permissions ✓  D) Maintaining network equipment

**9.** A company wants to store database credentials so they automatically rotate every 30 days. Which service should they use?
- A) SSM Parameter Store  B) AWS KMS  C) AWS Secrets Manager ✓  D) AWS Vault

**10.** Which AWS service uses machine learning to identify, classify, and protect sensitive data stored in S3?
- A) GuardDuty  B) Amazon Macie ✓  C) Inspector  D) Security Hub

**11.** A web application is being targeted by SQL injection attacks. Which service should the company deploy to block these attacks?
- A) AWS Shield  B) GuardDuty  C) AWS WAF ✓  D) Network ACL

**12.** Which AWS service provides downloadable compliance reports like SOC 2 and PCI DSS attestation?
- A) Trusted Advisor  B) AWS Artifact ✓  C) Security Hub  D) Config

**13.** Which is the MOST secure approach to allow an EC2 instance to access an S3 bucket?
- A) Embed access keys in the application code  B) Assign an IAM role to the EC2 instance ✓  C) Create an IAM user and store credentials on the instance  D) Enable public access on the S3 bucket

**14.** MFA (Multi-Factor Authentication) adds which additional security factor beyond a password?
- A) Something you know  B) Something you are OR something you have ✓  C) Something you see  D) Something you hear

**15.** Which service provides a centralised view of all security findings from GuardDuty, Inspector, and Macie?
- A) CloudTrail  B) AWS Config  C) AWS Security Hub ✓  D) CloudWatch

---

### Domain 3 — Cloud Technology and Services (34%)

**16.** A company wants the CHEAPEST option for running fault-tolerant batch jobs that can handle interruptions. Which EC2 pricing model should they use?
- A) On-Demand  B) Reserved  C) Dedicated Host  D) Spot ✓

**17.** Which service automatically distributes incoming HTTP traffic across multiple EC2 instances?
- A) Auto Scaling Group  B) Application Load Balancer ✓  C) Route 53  D) CloudFront

**18.** A developer needs to run a function that processes an image every time a file is uploaded to S3. The function takes 30 seconds to complete. Which compute service is BEST?
- A) EC2  B) Elastic Beanstalk  C) AWS Lambda ✓  D) ECS

**19.** Which S3 storage class automatically moves data to cheaper tiers based on changing access patterns?
- A) S3 Standard-IA  B) S3 Glacier  C) S3 One Zone-IA  D) S3 Intelligent-Tiering ✓

**20.** A company needs shared file storage that can be mounted by multiple EC2 Linux instances at the same time. Which service should they use?
- A) EBS  B) S3  C) Amazon EFS ✓  D) Instance Store

**21.** Which RDS feature creates an automatic failover replica in a different Availability Zone?
- A) Read Replica  B) Multi-AZ ✓  C) Aurora Serverless  D) Enhanced Monitoring

**22.** Which service would you use to cache frequently accessed database query results in memory?
- A) DAX (for DynamoDB)  B) ElastiCache ✓ (for RDS/other)  C) CloudFront  D) Read Replica
*(Note: Both A and B are valid — DAX specifically for DynamoDB, ElastiCache for others)*

**23.** A company wants to connect their on-premises data centre to AWS with a dedicated private connection (not the internet). Which service should they use?
- A) Site-to-Site VPN  B) AWS Direct Connect ✓  C) Internet Gateway  D) VPC Peering

**24.** Which service records every API call made in an AWS account, including who made the call and when?
- A) CloudWatch  B) CloudTrail ✓  C) AWS Config  D) VPC Flow Logs

**25.** Which service would you use to automatically scale the number of EC2 instances up and down based on CPU utilisation?
- A) Elastic Load Balancer  B) Auto Scaling Group ✓  C) CloudWatch Alarm only  D) Trusted Advisor

**26.** A company needs to migrate 500 TB of data from their on-premises data centre to AWS. The internet connection is too slow. Which is the BEST solution?
- A) AWS Direct Connect  B) S3 Transfer Acceleration  C) AWS Snowball Edge ✓  D) VPN

**27.** Which database service is most appropriate for a social network that needs to traverse relationships between millions of users?
- A) DynamoDB  B) RDS  C) Amazon Neptune ✓  D) Redshift

**28.** Which service helps analyse and investigate security incidents by visualising relationships between security findings using ML?
- A) GuardDuty  B) Inspector  C) Security Hub  D) Amazon Detective ✓

**29.** A company wants to automatically convert customer service call recordings to text to analyse sentiment. Which COMBINATION of services should they use?
- A) Polly + Comprehend  B) Transcribe + Comprehend ✓  C) Lex + Translate  D) Rekognition + Textract

**30.** Which AWS service helps developers build, train, and deploy machine learning models?
- A) Rekognition  B) SageMaker ✓  C) Comprehend  D) Bedrock

**31.** A company wants to deliver their website content with low latency to users worldwide by caching it at locations close to users. Which service provides this?
- A) Route 53  B) Global Accelerator  C) Amazon CloudFront ✓  D) ELB

**32.** Which service allows a developer to run Docker containers without managing any EC2 infrastructure?
- A) ECS with EC2 launch type  B) EKS  C) AWS Fargate ✓  D) Elastic Beanstalk

**33.** Which service is used to create step-by-step automated workflows that coordinate multiple AWS services?
- A) SQS  B) EventBridge  C) AWS Step Functions ✓  D) CodePipeline

**34.** A company needs the LEAST effort migration strategy to move their existing application to AWS. Which strategy should they choose?
- A) Refactor  B) Replatform  C) Rehost (Lift and Shift) ✓  D) Repurchase

---

### Domain 4 — Billing, Pricing, and Support (12%)

**35.** Which service provides automated recommendations to right-size EC2 instances and reduce costs?
- A) Cost Explorer  B) AWS Budgets  C) AWS Trusted Advisor ✓  D) Pricing Calculator

**36.** A company wants to set up an alert when their monthly AWS spend reaches $500. Which service should they use?
- A) Cost Explorer  B) AWS Budgets ✓  C) CloudWatch  D) Pricing Calculator

**37.** Which AWS support plan is the MINIMUM required to get 24/7 access to technical support via phone?
- A) Basic  B) Developer  C) Business ✓  D) Enterprise

**38.** A company has multiple AWS accounts. Which feature allows them to combine their usage for volume pricing discounts on a single invoice?
- A) AWS Marketplace  B) Reserved Instances  C) Consolidated Billing ✓  D) AWS Cost Explorer

**39.** Which Reserved Instance type allows the customer to change the instance family, OS, and tenancy during the term?
- A) Standard RI  B) Convertible RI ✓  C) Scheduled RI  D) On-Demand

**40.** Data transfer from the internet INTO AWS (ingress) is priced at:
- A) $0.09/GB  B) $0.01/GB  C) Free ✓  D) Varies by service

**41.** A company wants to estimate the cost of a new AWS architecture before building it. Which tool should they use?
- A) Cost Explorer  B) Trusted Advisor  C) AWS Pricing Calculator ✓  D) AWS Budgets

**42.** Which EC2 pricing option provides up to 90% discount but may be interrupted by AWS with a 2-minute warning?
- A) On-Demand  B) Reserved  C) Dedicated Host  D) Spot ✓

---

### Mixed / Tricky Questions

**43.** A company is running a web application with traffic that spikes during business hours and is very low overnight. Which pricing strategy offers the BEST cost optimization?
- A) All On-Demand  B) All Reserved  C) Reserved for baseline + On-Demand/Spot for spikes ✓  D) All Spot

**44.** Which AWS service provides a software marketplace where customers can purchase third-party software that runs on AWS?
- A) AWS Partner Network  B) AWS Marketplace ✓  C) Service Catalog  D) AWS Exchange

**45.** A Solutions Architect wants to ensure that an application continues to operate even if an entire AWS Region fails. What architectural approach should they use?
- A) Deploy across multiple Availability Zones  B) Use Multi-AZ RDS  C) Deploy across multiple AWS Regions ✓  D) Use Auto Scaling

**46.** Which AWS service provides a fully managed graph database?
- A) DynamoDB  B) DocumentDB  C) Amazon Neptune ✓  D) QLDB

**47.** A company needs to ensure that a specific S3 bucket is never made publicly accessible, regardless of individual bucket or object ACL settings. Which S3 feature enforces this?
- A) Bucket Policy  B) S3 Encryption  C) S3 Block Public Access ✓  D) ACL Deny Rule

**48.** Which statement about AWS Availability Zones is correct?
- A) Each AZ is a separate Region  B) AZs within a Region are connected by low-latency links ✓  C) Each Region has exactly one AZ  D) AZs are the same as Edge Locations

**49.** A company wants to use AWS to host a Windows file server share accessible by on-premises Windows clients. Which service is MOST appropriate?
- A) Amazon EFS  B) Amazon S3  C) Amazon FSx for Windows File Server ✓  D) AWS Storage Gateway

**50.** Which AWS service is used to establish a private virtual network within AWS and control networking, IP addressing, subnets, and routing?
- A) AWS Direct Connect  B) Amazon Route 53  C) Amazon VPC ✓  D) AWS Transit Gateway

---

## Answer Key

| Q | Ans | Q | Ans | Q | Ans | Q | Ans | Q | Ans |
|---|-----|---|-----|---|-----|---|-----|---|-----|
| 1 | C | 11 | C | 21 | B | 31 | C | 41 | C |
| 2 | C | 12 | B | 22 | B | 32 | C | 42 | D |
| 3 | D | 13 | B | 23 | B | 33 | C | 43 | C |
| 4 | C | 14 | B | 24 | B | 34 | C | 44 | B |
| 5 | B | 15 | C | 25 | B | 35 | C | 45 | C |
| 6 | C | 16 | D | 26 | C | 36 | B | 46 | C |
| 7 | C | 17 | B | 27 | C | 37 | C | 47 | C |
| 8 | C | 18 | C | 28 | D | 38 | C | 48 | B |
| 9 | C | 19 | D | 29 | B | 39 | B | 49 | C |
| 10 | B | 20 | C | 30 | B | 40 | C | 50 | C |

---

## Top 10 Exam Tips

```
1. MANAGED > SELF-MANAGED  
   AWS always prefers managed services (RDS over EC2+MySQL, EFS over NFS on EC2)

2. SERVERLESS > SERVERS when possible
   Lambda, Fargate, DynamoDB, Aurora Serverless = no patching, auto-scale

3. SHARED RESPONSIBILITY  
   AWS = hardware, hypervisor, managed service OS
   Customer = EC2 OS, IAM, data, applications

4. SPOT = CHEAPEST, can be interrupted
   RESERVED = best for predictable 1-3yr workloads
   ON-DEMAND = flexible, no commitment

5. CLOUDTRAIL = WHO did WHAT
   CLOUDWATCH = performance METRICS and logs
   AWS CONFIG = WHAT the resource config looks like

6. MULTI-AZ = high availability (failover)
   READ REPLICAS = performance (scale reads)

7. REGION = geographic area
   AZ = data centre(s) within a region
   EDGE LOCATION = CloudFront cache location

8. S3 = unlimited object storage (any file type)
   EBS = EC2 hard drive (one instance)
   EFS = shared NFS for many Linux instances

9. SECURITY: GuardDuty(threats) | Inspector(vulnerabilities) | Macie(PII in S3)

10. COST: Trusted Advisor | Cost Explorer | Budgets | Pricing Calculator
    Know WHICH tool for WHICH cost management task
```

---

## Additional Study Resources

- **AWS Skill Builder:** Free official training at skillbuilder.aws
- **AWS Cloud Quest:** Free gamified learning (Cloud Practitioner path)
- **AWS Whitepapers:** Overview of Amazon Web Services, AWS Pricing, Well-Architected Framework
- **Practice Exams:** AWS official practice questions, Tutorials Dojo, Whizlabs
- **AWS Free Tier:** Create an account and explore services hands-on
- **YouTube:** freeCodeCamp AWS Practitioner 4-hour course
- **Exam guide:** Download from aws.amazon.com/certification

**You've got this! 🎯 Time to schedule your exam and get certified!**
