# Day 6 — Networking & VPC

## Introduction
Understanding AWS networking is fundamental. The **Amazon VPC (Virtual Private Cloud)** is your isolated network in the cloud, and knowing how traffic flows through it is key to the exam.

---

## Amazon VPC (Virtual Private Cloud)

### What Is a VPC?
- A **logically isolated section** of the AWS cloud where you launch resources
- You control: IP address range, subnets, routing, gateways, security
- Exists within a **single Region** but spans multiple AZs
- Each AWS account gets a **default VPC** in each Region

### VPC Key Components

| Component | Description |
|-----------|-------------|
| **Subnet** | Sub-division of a VPC within a single AZ |
| **Public Subnet** | Has route to Internet Gateway — internet accessible |
| **Private Subnet** | No route to internet — for databases, backend |
| **Internet Gateway (IGW)** | Enables internet access for public subnets |
| **NAT Gateway** | Allows private subnet resources to access internet (outbound only) |
| **Route Table** | Rules determining where traffic is directed |

### VPC Flow Logs
- Capture information about IP traffic going to/from network interfaces in your VPC
- Stored in CloudWatch Logs or S3
- Used for: security analysis, troubleshooting

---

## Security: Security Groups vs NACLs

| Feature | Security Groups | Network ACLs (NACLs) |
|---------|----------------|---------------------|
| Level | Instance level | Subnet level |
| State | Stateful (return traffic auto-allowed) | Stateless (must allow both directions) |
| Rules | Allow rules only | Allow AND Deny rules |
| Default | Deny all inbound, Allow all outbound | Allow all traffic |
| Evaluation | All rules evaluated | Rules evaluated in order (lowest number first) |

**Memory trick:**
- Security Group = **instance firewall**, stateful
- NACL = **subnet firewall**, stateless

---

## VPC Connectivity Options

### Internet Gateway (IGW)
- Connects your VPC to the public internet
- Horizontally scaled, redundant, highly available
- One IGW per VPC

### NAT Gateway
- Allows instances in **private subnets** to initiate outbound internet connections
- Managed by AWS — no administration required
- Must be created in a **public subnet**
- Not accessible from the internet (one-way outbound only)

### VPC Peering
- Connects **two VPCs** privately (same or different accounts/regions)
- Traffic stays on AWS network
- Not transitive (A↔B, B↔C doesn't mean A↔C)

### AWS Transit Gateway
- Hub-and-spoke model to connect **many VPCs** and on-premises networks
- Central hub — avoids complex peering meshes

### VPC Endpoints
- Connect to AWS services **privately** without internet
- **Interface Endpoints:** ENI with private IP (most services)
- **Gateway Endpoints:** S3 and DynamoDB only

---

## Connecting to On-Premises

### AWS Site-to-Site VPN
- Encrypted VPN tunnel over the **public internet**
- Quick to set up (minutes)
- Lower cost
- Bandwidth limited by internet

### AWS Direct Connect
- **Dedicated private network connection** from your data centre to AWS
- More consistent, higher bandwidth
- Takes weeks to set up
- Higher cost
- Not encrypted by default (use with VPN for encryption)

**Exam rule:** VPN = fast setup, internet-based. Direct Connect = private, consistent, high bandwidth.

---

## AWS Route 53 (DNS Service)

- Managed **Domain Name System (DNS)** service
- Routes end users to applications
- **Routing Policies:**

| Policy | Use Case |
|--------|---------|
| Simple | Single resource |
| Weighted | A/B testing, split traffic by % |
| Latency | Route to Region with lowest latency |
| Failover | Active-passive failover |
| Geolocation | Route based on user's country/continent |
| Geoproximity | Route based on user's location + resource bias |
| Multi-Value | Returns multiple healthy records |

---

## Amazon CloudFront (CDN)

- **Content Delivery Network (CDN)** — caches content at edge locations worldwide
- Reduces latency by serving content from the edge closest to the user
- Works with: S3, ALB, EC2, API Gateway, Lambda@Edge
- **Origins:** S3 bucket, HTTP server (EC2, ALB), MediaStore

**Benefits:**
- Improved performance (cached at 400+ edge locations)
- DDoS protection (Shield integration)
- Can restrict access with signed URLs/cookies

---

## AWS Global Accelerator

- Improves performance using **AWS's private global network** (not public internet)
- Routes traffic to optimal endpoints
- Two static IP addresses (anycast) — don't change
- **vs CloudFront:** CloudFront = content caching (HTTP). Global Accelerator = TCP/UDP routing.

---

## Practice Questions

1. A web server in a private subnet needs to download software updates from the internet. Which service enables this?
   - A) Internet Gateway  B) VPC Peering  C) NAT Gateway ✓  D) VPC Endpoint

2. Which service provides a dedicated, private network connection from an on-premises data centre to AWS with consistent bandwidth?
   - A) AWS Site-to-Site VPN  B) AWS Direct Connect ✓  C) Internet Gateway  D) Transit Gateway

3. A company wants to route users in Europe to a European AWS Region and users in Asia to an Asian Region. Which Route 53 policy should they use?
   - A) Latency  B) Weighted  C) Geolocation ✓  D) Failover

4. Which service operates at the subnet level and supports both Allow and Deny rules?
   - A) Security Group  B) IAM Policy  C) Network ACL ✓  D) WAF
