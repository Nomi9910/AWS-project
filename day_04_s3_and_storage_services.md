# Day 4 — S3 & Storage Services

## Introduction
Storage is one of AWS's most fundamental services. **Amazon S3** is the most versatile and commonly tested storage service on the CLF-C02 exam.

---

## Amazon S3 (Simple Storage Service)

### What Is S3?
- **Object storage** service — store any type of file (objects)
- Virtually **unlimited storage** capacity
- Objects stored in **buckets** (like folders)
- Each object can be up to **5 TB** in size
- Bucket names must be **globally unique**
- Data stored in a specific Region
- Access via URL: `https://bucket-name.s3.amazonaws.com/object-key`

### S3 Key Concepts
| Term | Description |
|------|-------------|
| **Bucket** | Container for objects (like a folder) |
| **Object** | A file + its metadata |
| **Key** | The full path/name of an object |
| **Versioning** | Keep multiple versions of an object |
| **Prefix** | Folder-like path inside a bucket |

### S3 Storage Classes (Core Exam Topic)

| Class | Use Case | Retrieval | Cost |
|-------|----------|-----------|------|
| **S3 Standard** | Frequently accessed data | Immediate | Highest |
| **S3 Standard-IA** | Infrequently accessed, but needs fast access | Immediate | Lower storage, retrieval fee |
| **S3 One Zone-IA** | Infrequent access, can tolerate AZ loss | Immediate | Even lower |
| **S3 Intelligent-Tiering** | Unknown access patterns — auto-moves data | Immediate | Small monitoring fee |
| **S3 Glacier Instant Retrieval** | Archives, accessed once a quarter | Milliseconds | Very low |
| **S3 Glacier Flexible Retrieval** | Archive, accessed 1-2 times per year | Minutes to hours | Low |
| **S3 Glacier Deep Archive** | Long-term archive, accessed rarely | 12–48 hours | Lowest |

**Decision guide:**
- Frequently accessed → S3 Standard
- Don't know access pattern → S3 Intelligent-Tiering
- Long-term archive, must retrieve same day → Glacier Instant Retrieval
- Long-term archive, 12-hour retrieval OK → Glacier Deep Archive

### S3 Security

| Feature | Description |
|---------|-------------|
| **Bucket Policies** | JSON-based policies applied to the entire bucket |
| **ACLs (Access Control Lists)** | Legacy per-object or per-bucket permissions |
| **Block Public Access** | Setting to prevent accidental public exposure |
| **Server-Side Encryption (SSE)** | Encrypt data at rest |
| **MFA Delete** | Require MFA to delete objects or disable versioning |
| **Presigned URLs** | Temporary access URL for specific object |

**S3 is private by default** — all objects are private unless explicitly made public.

### S3 Replication
- **Cross-Region Replication (CRR):** Copy objects to another Region (compliance, latency)
- **Same-Region Replication (SRR):** Copy within same Region (log aggregation)
- Requires versioning to be enabled on both buckets

### S3 Lifecycle Rules
- Automatically **transition objects** between storage classes based on age
- Example: Move to Standard-IA after 30 days → Glacier after 90 days → Delete after 365 days

### S3 Use Cases
- Static website hosting
- Backup and restore
- Data lake / big data analytics
- Media storage and distribution
- Software delivery

---

## AWS Storage Services Comparison

### Amazon EBS (Elastic Block Store)
- **Block storage** for EC2 instances — like a hard drive attached to a server
- Persists independently of EC2 instance lifecycle
- One EBS volume → One EC2 instance at a time (usually)
- Snapshots stored in S3 for backup
- **Use when:** OS volumes, databases on EC2

### Amazon EFS (Elastic File System)
- **Managed NFS (Network File System)** — shared file storage
- Automatically scales up and down
- Can be mounted on **many EC2 instances simultaneously** (across AZs)
- Linux only
- **Use when:** Shared file storage for multiple EC2 instances

### Amazon FSx
- Managed third-party file systems
- **FSx for Windows File Server:** Windows SMB shares
- **FSx for Lustre:** High-performance computing, ML

### AWS Storage Gateway
- Hybrid storage: connects **on-premises** to AWS cloud storage
- Types:
  - **File Gateway:** NFS/SMB interface backed by S3
  - **Volume Gateway:** iSCSI block storage
  - **Tape Gateway:** Virtual tape library backed by S3 Glacier

### AWS Snow Family (Physical Data Transfer)
| Device | Capacity | Use Case |
|--------|----------|---------|
| **Snowcone** | 8–14 TB | Edge computing, small transfers |
| **Snowball Edge** | 80–210 TB | Large-scale migration |
| **Snowmobile** | Up to 100 PB | Exabyte-scale migration (shipping container!) |

**Rule of thumb:** If it would take more than a week to transfer data over the internet, use a Snow device.

---

## Storage Summary Table

| Service | Type | Use Case |
|---------|------|---------|
| S3 | Object | Files, images, backups, websites |
| EBS | Block | EC2 hard drive, databases |
| EFS | File | Shared Linux file system |
| FSx | File | Windows shares, HPC |
| Storage Gateway | Hybrid | Connect on-premises to cloud |
| Snowball | Physical | Offline large data migration |

---

## Practice Questions

1. A company needs to store files that are accessed frequently. Which S3 storage class is MOST appropriate?
   - A) S3 Glacier  B) S3 Standard ✓  C) S3 Standard-IA  D) S3 One Zone-IA

2. An application requires shared file storage accessible by multiple EC2 Linux instances simultaneously. Which service should be used?
   - A) Amazon EBS  B) Amazon S3  C) Amazon EFS ✓  D) Amazon FSx for Windows

3. A company needs to transfer 800 TB of data to AWS. Internet transfer would take months. What is the BEST solution?
   - A) AWS Direct Connect  B) AWS Snowball Edge ✓  C) S3 Transfer Acceleration  D) AWS VPN

4. Which S3 feature automatically moves objects to cheaper storage classes based on age?
   - A) S3 Versioning  B) S3 Replication  C) S3 Lifecycle Rules ✓  D) S3 Transfer Acceleration
