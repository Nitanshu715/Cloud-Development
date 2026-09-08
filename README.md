# ☁️ AWS Cloud Application Development Lab

> A practical collection of AWS cloud experiments covering cloud storage, content delivery, compute, identity and access management, object management, security fundamentals, and multi-region cloud resilience.

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws&logoColor=white" alt="AWS">
  <img src="https://img.shields.io/badge/Cloud-Application%20Development-blue" alt="Cloud Application Development">
  <img src="https://img.shields.io/badge/AWS%20Experiments-5-purple" alt="Five AWS Experiments">
  <img src="https://img.shields.io/badge/Status-Completed-success" alt="Completed">
</p>

<p align="center">
  <b>Learn → Build → Deploy → Manage → Secure → Replicate → Verify</b>
</p>

---

## 📌 About

This repository contains the practical experiments performed as part of the **Cloud Application Development Lab**.

Each experiment focuses on understanding and implementing an AWS cloud service or concept through the **AWS Management Console** and, where required, supporting command-line or development tools.

The repository is organized experiment-wise so that every practical can be accessed, documented, and reviewed independently.

The experiments progressively cover important cloud application-development concepts including:

- Cloud storage
- Content delivery
- Cloud computing
- Virtual machines
- Identity and access management
- Object storage
- AWS resource configuration
- Cloud security fundamentals
- Data replication
- Multi-region architecture
- Backup and disaster-recovery concepts
- Cloud resource lifecycle management

---

# 🧪 Experiments

| Experiment | Topic | Primary AWS Service(s) | Status |
|---|---|---|---|
| **Experiment 1** | Amazon S3 + CloudFront — Static Website Delivery | S3, CloudFront | ✅ Completed |
| **Experiment 2** | Introduction to Amazon EC2 | EC2, Security Groups | ✅ Completed |
| **Experiment 3** | Introduction to AWS IAM — Identity, Users & Access Policies | IAM, S3 | ✅ Completed |
| **Experiment 4** | Creating Buckets and Managing Objects in AWS | S3 | ✅ Completed |
| **Experiment 5** | Implementing Multi-Region Backup in Amazon S3 Using Cross-Region Replication | S3, IAM, S3 Batch Operations | ✅ Completed |

---

# 📂 Repository Structure

```text
cloud-application-development/
│
├── experiment-1/
│   └── README.md
│
├── experiment-2/
│   └── README.md
│
├── experiment-3/
│   └── README.md
│
├── experiment-4/
│   └── README.md
│
├── experiment-5/
│   └── README.md
│
└── README.md
```

---

# ☁️ Experiments Overview

## 🌐 Experiment 1 — S3 + CloudFront

**Topic:** Static Website Hosting and Content Delivery using Amazon S3 and Amazon CloudFront.

### Key Work

- Created an Amazon S3 bucket for website content.
- Configured the required S3 bucket settings.
- Connected the S3 bucket with Amazon CloudFront.
- Configured CloudFront with the S3 bucket as the origin.
- Used private S3 access through the CloudFront delivery architecture.
- Configured the default root object as `index.html`.
- Created and deployed a CloudFront distribution.
- Verified the CloudFront distribution and website delivery.

### Concepts Covered

- Amazon S3
- Amazon CloudFront
- Object storage
- Static website content
- Content delivery networks
- CloudFront distributions
- S3 origin configuration
- Secure content delivery

📁 Detailed documentation is available in [`experiment-1/README.md`](experiment-1/README.md).

---

## 🖥️ Experiment 2 — Introduction to Amazon EC2

**Topic:** Launching and accessing a cloud-based virtual machine using Amazon EC2.

### Key Work

- Launched a free-tier eligible `t3.micro` EC2 instance.
- Used Amazon Linux 2023.
- Configured a Security Group for SSH access.
- Connected to the EC2 instance using EC2 Instance Connect.
- Inspected the running Linux environment.
- Used Linux commands to inspect system and instance information.
- Examined CPU, memory, storage, operating system, hostname, and network information.

### Concepts Covered

- Amazon EC2
- Cloud computing
- Virtual machines
- Amazon Linux
- Instance types
- Security Groups
- SSH
- EC2 Instance Connect
- Linux command line
- Cloud compute resources

📁 Detailed documentation is available in [`experiment-2/README.md`](experiment-2/README.md).

---

## 🔐 Experiment 3 — Introduction to AWS IAM

**Topic:** Identity, Users, Access Policies, and Permission Management using AWS IAM.

### Key Work

- Explored AWS Identity and Access Management (IAM).
- Created and configured IAM users.
- Examined identity-based permissions.
- Assigned permissions using IAM policies.
- Worked with Amazon S3 permissions.
- Modified an S3-related policy to restrict a specific action.
- Demonstrated the difference between an allowed action and an explicitly denied action.
- Restricted the `s3:DeleteBucket` operation while retaining other required S3 access.
- Verified the resulting permission behavior.

### Concepts Covered

- AWS IAM
- IAM users
- IAM policies
- Identity-based policies
- Permissions
- Allow statements
- Explicit Deny
- Policy evaluation
- Least Privilege
- Amazon S3 permissions
- Access control

### Security Principle Demonstrated

The experiment demonstrates the **Principle of Least Privilege**, where an identity should receive only the permissions necessary to perform its intended tasks.

The practical also demonstrates that an **explicit `Deny` overrides an `Allow`** when AWS evaluates permissions.

📁 Detailed documentation is available in [`experiment-3/README.md`](experiment-3/README.md).

---

## 🪣 Experiment 4 — Creating Buckets and Managing Objects

**Topic:** Creating Amazon S3 buckets and managing objects using the AWS Management Console.

### Key Work

- Opened the Amazon S3 service from the AWS Management Console.
- Created an S3 bucket with a valid globally unique name.
- Selected the required AWS Region.
- Reviewed bucket configuration settings.
- Reviewed Object Ownership settings.
- Reviewed S3 Block Public Access settings.
- Opened the newly created bucket.
- Navigated to the Objects section.
- Uploaded files into the S3 bucket.
- Verified the uploaded objects.
- Inspected object information and properties.
- Performed basic object-management operations.
- Verified the final bucket and object state.

### Concepts Covered

- Amazon S3
- Buckets
- Objects
- Object keys
- AWS Regions
- Object storage
- Storage classes
- Object metadata
- Object management
- S3 security
- Block Public Access
- S3 versioning concepts
- Cloud storage

### Practical Workflow

```text
AWS Management Console
        │
        ▼
     Amazon S3
        │
        ▼
    Create Bucket
        │
        ▼
  Configure Settings
        │
        ▼
     Open Bucket
        │
        ▼
     Upload Object
        │
        ▼
    Inspect Object
        │
        ▼
    Manage Object
        │
        ▼
  Final Verification
```

📁 Detailed documentation is available in [`experiment-4/README.md`](experiment-4/README.md).

---

# 🌍 Experiment 5 — S3 Cross-Region Replication

**Topic:** Implementing Multi-Region Backup in Amazon S3 Using Cross-Region Replication.

### 🎯 Aim

To implement a multi-region backup mechanism for Amazon S3 by configuring **Cross-Region Replication (CRR)** between a source bucket in `us-east-1` and a destination bucket in `ap-south-1`, and to verify that objects can be replicated across AWS Regions.

### 🧩 Practical Configuration

| Component | Configuration |
|---|---|
| AWS Service | Amazon S3 |
| Source bucket | `cad-exp4-source-nitanshu` |
| Source Region | `us-east-1` — US East (N. Virginia) |
| Destination bucket | `cad-exp4-destination-nitanshu` |
| Destination Region | `ap-south-1` — Asia Pacific (Mumbai) |
| Replication type | Cross-Region Replication (CRR) |
| Account relationship | Same AWS account |
| Versioning | Enabled on both buckets |
| Replication rule | `CRR-to-ap-south-1` |
| Rule status | Enabled |
| Replication scope | All objects |
| Test object | `scheduler.pdf` |
| Existing-object mechanism | S3 Batch Replication |
| Completion | Verified and cleaned up |

> **Note:** The resource names above document the completed practical configuration. Temporary lab resources were cleaned up after verification.

### 🗺️ Architecture

```text
┌───────────────────────────────────────┐
│ 🇺🇸 SOURCE REGION                     │
│ US East (N. Virginia) — us-east-1   │
│                                       │
│ cad-exp4-source-nitanshu              │
└───────────────────┬───────────────────┘
                    │
                    │ S3 Cross-Region
                    │ Replication (CRR)
                    ▼
┌───────────────────────────────────────┐
│ 🇮🇳 DESTINATION REGION                │
│ Asia Pacific (Mumbai) — ap-south-1  │
│                                       │
│ cad-exp4-destination-nitanshu         │
└───────────────────────────────────────┘
```

### 🔑 Key Work

- Created a source S3 bucket in `us-east-1`.
- Enabled Versioning on the source bucket.
- Created a destination S3 bucket in `ap-south-1`.
- Enabled Versioning on the destination bucket.
- Uploaded `scheduler.pdf` to the source bucket.
- Created the replication rule `CRR-to-ap-south-1`.
- Selected the Mumbai bucket as the replication destination.
- Used an IAM role created through the S3 console for replication permissions.
- Applied the replication rule to all objects.
- Used S3 Batch Replication to handle the object that existed before the replication configuration.
- Created and monitored the Batch Operations job.
- Verified `scheduler.pdf` in the Mumbai destination bucket.
- Inspected the job/manifest-related objects created during the Batch Operations workflow.
- Emptied and deleted the temporary source and destination buckets after verification.

### 📚 Concepts Covered

- Amazon S3
- S3 Versioning
- Cross-Region Replication (CRR)
- Same-account replication
- AWS Regions
- Replication rules
- IAM roles
- S3 Batch Operations
- S3 Batch Replication
- Replication manifests
- Completion reports
- Multi-region backup
- Geographic redundancy
- Disaster recovery fundamentals
- Resource cleanup
- Cloud cost awareness

### 🔄 Live Replication vs Batch Replication

A major concept demonstrated by this practical was the difference between live replication and replication of existing objects.

```text
LIVE CRR
New / updated eligible object
            │
            ▼
     Source S3 Bucket
            │
            │ asynchronous replication
            ▼
   Destination S3 Bucket
```

Live replication does **not** retroactively replicate objects that existed before the replication configuration was created.

For existing objects:

```text
Existing object
      │
      ▼
S3 Batch Replication
      │
      ▼
Destination bucket
```

Therefore, because `scheduler.pdf` already existed before the CRR rule was configured, **S3 Batch Replication** was used to backfill the object.

### 🧾 Replication Manifest

The Batch Replication workflow uses a **manifest** to identify objects that the Batch Operations job should process.

Conceptually:

```text
Replication Manifest
        │
        ├── Source bucket
        ├── Object key
        └── Version information where applicable
```

During the practical, a job-related folder appeared in the destination bucket. This represented Batch Operations / manifest-related processing data rather than the original test object itself.

### 📦 Batch Operations Job

The Batch Replication job was created through the S3 console and monitored through the Batch Operations interface.

The practical observed the job progress from its initial state into an active processing state before the destination object was verified.

### ✅ Verification

The destination bucket in Mumbai was opened after the Batch Replication job was processed.

The replicated object:

```text
scheduler.pdf
```

was visible in:

```text
cad-exp4-destination-nitanshu
```

This confirmed that the existing source object had been successfully replicated to the destination Region.

### 🛡️ Security & Reliability Principles

The practical demonstrated several cloud architecture principles:

- Keep backup buckets private unless public access is explicitly required.
- Use IAM roles for AWS service permissions.
- Enable Versioning for replication.
- Maintain geographic separation between source and backup data.
- Use least-privilege permissions where possible.
- Understand the difference between live replication and on-demand replication.
- Plan recovery procedures instead of assuming replication alone is a complete disaster-recovery solution.
- Clean up temporary resources after a practical to avoid unnecessary cloud costs.

### 🧹 Cleanup

After successful verification:

```text
Source bucket
     │
     ▼
Remove stored data / versions
     │
     ▼
Delete bucket

Destination bucket
     │
     ▼
Remove stored data / versions
     │
     ▼
Delete bucket
```

Because Versioning was enabled, cleanup required attention to stored versions and delete markers rather than only deleting the visible object.

### 📊 Experiment 5 Result

| Check | Result |
|---|---|
| Source bucket created | ✅ |
| Source Region configured | ✅ `us-east-1` |
| Destination bucket created | ✅ |
| Destination Region configured | ✅ `ap-south-1` |
| Versioning enabled on source | ✅ |
| Versioning enabled on destination | ✅ |
| CRR rule created | ✅ |
| CRR rule enabled | ✅ |
| IAM replication role configured | ✅ |
| Batch Replication job created | ✅ |
| Existing object replicated | ✅ |
| Destination verification | ✅ |
| Cleanup completed | ✅ |

📁 Detailed documentation is available in [`experiment-5/README.md`](experiment-5/README.md).

---

# 📊 Experiments Comparison

| Area | Experiment 1 | Experiment 2 | Experiment 3 | Experiment 4 | Experiment 5 |
|---|---|---|---|---|---|
| **Primary Service** | S3 + CloudFront | EC2 | IAM | S3 | S3 + Batch Operations |
| **Main Concept** | Static Content Delivery | Cloud Compute | Identity & Access Control | Object Storage | Multi-Region Replication |
| **Storage** | S3 | EBS / Instance Storage | S3 Permissions | S3 Objects | S3 Versioned Objects |
| **Compute** | — | EC2 | — | — | — |
| **Networking** | CloudFront Delivery | Security Group | IAM Authorization | S3 Access | Cross-Region Architecture |
| **Security** | Private S3 Origin + HTTPS | Security Group | IAM Policies + Explicit Deny | Block Public Access + IAM | IAM + Versioning + Private Buckets |
| **Resilience** | Content Distribution | VM Availability | Access Control | Object Management | Geographic Redundancy |
| **Main Output** | Deployed Website | Running Linux VM | Controlled AWS Permissions | Managed S3 Bucket and Objects | Verified Multi-Region Object Backup |
| **Status** | ✅ Completed | ✅ Completed | ✅ Completed | ✅ Completed | ✅ Completed |

---

# 🛠️ Technologies & Services

The repository currently uses or demonstrates the following AWS services and technologies:

### AWS Services

- **Amazon S3**
- **Amazon CloudFront**
- **Amazon EC2**
- **AWS Identity and Access Management (IAM)**
- **Amazon EBS**
- **EC2 Instance Connect**
- **Security Groups**
- **S3 Batch Operations**

### Supporting Technologies

- Amazon Linux
- Linux command line
- AWS Management Console
- HTTPS
- IAM policy JSON
- Cloud object storage
- S3 Versioning
- Cross-Region Replication
- Batch Replication
- Multi-region cloud architecture

---

# 🔐 Security Concepts Covered

Security is an important component of the practical work in this repository.

The experiments introduce several fundamental AWS security and resilience concepts.

### Identity and Access Management

IAM is used to control which AWS identities can access which resources and what actions they are allowed to perform.

### Least Privilege

Permissions should be limited to only what is required for a particular task.

### Explicit Deny

An explicit `Deny` in an applicable IAM policy overrides an applicable `Allow`.

### S3 Public Access Protection

S3 Block Public Access helps prevent accidental public exposure of buckets and objects.

### Security Groups

EC2 Security Groups act as virtual firewalls controlling inbound and outbound traffic associated with instances.

### Secure Content Delivery

CloudFront can provide HTTPS-based delivery for content distributed from cloud storage.

### Versioning

S3 Versioning maintains multiple versions of objects and is required for S3 replication configurations.

### Cross-Region Redundancy

CRR provides a mechanism for maintaining eligible object replicas in a different AWS Region.

### Backup Lifecycle Awareness

Replication and backup resources should be monitored, verified, retained according to requirements, and cleaned up when temporary resources are no longer required.

---

# 🎯 Repository Purpose

The main objective of this repository is to build practical understanding of AWS infrastructure and cloud application development by:

**Creating → Configuring → Deploying → Accessing → Managing → Securing → Replicating → Verifying**

cloud resources rather than studying the concepts only theoretically.

Each experiment is designed to provide hands-on exposure to a different part of the AWS ecosystem.

---

# 📈 Learning Progression

The experiments collectively demonstrate a progression from basic cloud resource creation to application-oriented cloud management and multi-region resilience:

```text
Experiment 1
S3 + CloudFront
       │
       ▼
Static Content Delivery
       │
       ▼
Experiment 2
EC2
       │
       ▼
Cloud Compute
       │
       ▼
Experiment 3
IAM
       │
       ▼
Identity & Access Control
       │
       ▼
Experiment 4
S3 Bucket & Objects
       │
       ▼
Cloud Object Storage Management
       │
       ▼
Experiment 5
S3 Cross-Region Replication
       │
       ▼
Multi-Region Backup & Resilience
```

Together, these experiments establish practical foundations for working with AWS-based cloud applications.

---

# 🧠 Experiment-to-Concept Map

```text
┌─────────────────────────────────────────────────────────────┐
│                 AWS CLOUD APPLICATION DEVELOPMENT           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  EXP 1 → S3 + CloudFront                                    │
│          Static delivery + CDN                              │
│                                                             │
│  EXP 2 → EC2                                                │
│          Cloud compute + Linux VM                           │
│                                                             │
│  EXP 3 → IAM                                                │
│          Identity + permissions + least privilege            │
│                                                             │
│  EXP 4 → S3                                                 │
│          Buckets + objects + object management              │
│                                                             │
│  EXP 5 → S3 CRR                                             │
│          Versioning + replication + multi-region backup     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

# 📚 Key Learning Areas

By completing the experiments in this repository, the following areas are covered:

- AWS Management Console
- Cloud object storage
- Static website delivery
- Content delivery networks
- Cloud computing
- Virtual machines
- Linux-based cloud instances
- Security Groups
- IAM users
- IAM policies
- Permission evaluation
- Explicit Deny
- Least Privilege
- S3 buckets
- S3 objects
- Object keys
- Storage classes
- S3 Versioning
- Cross-Region Replication
- S3 Batch Operations
- Replication manifests
- Multi-region backup
- Geographic redundancy
- Disaster-recovery fundamentals
- Basic cloud security
- Resource management
- Cloud cost awareness

---

# 🏆 Skills Demonstrated

After completing the five experiments, the repository demonstrates practical exposure to:

```text
AWS Console Usage
        ↓
Resource Creation
        ↓
Cloud Configuration
        ↓
Compute & Storage
        ↓
Identity & Access Control
        ↓
Application Content Delivery
        ↓
Object Management
        ↓
Data Replication
        ↓
Multi-Region Resilience
        ↓
Verification & Cleanup
```

---

# 👨‍💻 Author

**Nitanshu Tak**

B.Tech — Computer Science Engineering  
Cloud Computing & Virtualization Technology

---

<p align="center">
  <b>☁️ Cloud Application Development Lab</b><br>
  <sub>Learn → Build → Deploy → Manage → Secure → Replicate → Verify</sub>
</p>
