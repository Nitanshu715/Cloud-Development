# ☁️ AWS Cloud Application Development Lab

> A practical collection of AWS cloud experiments covering core cloud infrastructure, compute, storage, and application development services.

![AWS](https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws) ![Cloud](https://img.shields.io/badge/Focus-Cloud%20Application%20Development-blue) ![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)

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

---

## 🧪 Experiments

| Experiment | Topic | Primary AWS Service(s) | Status |
|---|---|---|---|
| **Experiment 1** | Amazon S3 + CloudFront — Static Website Delivery | S3, CloudFront | ✅ Completed |
| **Experiment 2** | Introduction to Amazon EC2 | EC2, Security Groups | ✅ Completed |
| **Experiment 3** | Introduction to AWS IAM — Identity, Users & Access Policies | IAM, S3 | ✅ Completed |
| **Experiment 4** | Creating Buckets and Managing Objects in AWS | S3 | ✅ Completed |

---

## 📂 Repository Structure

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

The practical also demonstrates that an **explicit Deny overrides an Allow** when AWS evaluates permissions.

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

# 📊 Experiments Comparison

| Area | Experiment 1 | Experiment 2 | Experiment 3 | Experiment 4 |
|---|---|---|---|---|
| **Primary Service** | S3 + CloudFront | EC2 | IAM | S3 |
| **Main Concept** | Static Content Delivery | Cloud Compute | Identity & Access Control | Object Storage |
| **Storage** | S3 | EBS / Instance Storage | S3 Permissions | S3 Objects |
| **Compute** | — | EC2 | — | — |
| **Networking** | CloudFront Delivery | Security Group | IAM Authorization | S3 Access |
| **Security** | Private S3 Origin + HTTPS | Security Group | IAM Policies + Explicit Deny | Block Public Access + IAM |
| **Main Output** | Deployed Website | Running Linux VM | Controlled AWS Permissions | Managed S3 Bucket and Objects |
| **Status** | ✅ Completed | ✅ Completed | ✅ Completed | ✅ Completed |

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

### Supporting Technologies

- Amazon Linux
- Linux command line
- AWS Management Console
- HTTPS
- IAM policy JSON
- Cloud object storage

---

# 🔐 Security Concepts Covered

Security is an important component of the practical work in this repository.

The experiments introduce several fundamental AWS security concepts:

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

---

# 🎯 Repository Purpose

The main objective of this repository is to build practical understanding of AWS infrastructure and cloud application development by:

**Creating → Configuring → Deploying → Accessing → Managing → Securing → Verifying**

cloud resources rather than studying the concepts only theoretically.

Each experiment is designed to provide hands-on exposure to a different part of the AWS ecosystem.

---

# 📈 Learning Progression

The experiments collectively demonstrate a progression from basic cloud resource creation to application-oriented cloud management:

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
```

Together, these experiments establish practical foundations for working with AWS-based cloud applications.

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
- Basic cloud security
- Resource management

---

# 👨‍💻 Author

**Nitanshu Tak**

B.Tech — Computer Science Engineering  
Cloud Computing & Virtualization Technology

---

> 🚀 **Cloud Application Development Lab — Learn → Build → Deploy → Manage → Secure → Verify**
