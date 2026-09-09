# ☁️ Cloud Application Development Lab

 

<p align="center">

  <img src="https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws&logoColor=white" alt="AWS">

  <img src="https://img.shields.io/badge/Experiments-5-blue" alt="5 Experiments">

  <img src="https://img.shields.io/badge/Platform-Amazon%20Web%20Services-yellow?logo=amazonaws&logoColor=white" alt="AWS">

  <img src="https://img.shields.io/badge/Console-AWS%20Management%20Console-purple" alt="AWS Console">

  <img src="https://img.shields.io/badge/Status-Completed-success" alt="Completed">

</p>

 

<p align="center">

  <b>Hands-on AWS Cloud Application Development</b><br>

  <sub>Compute • Identity • Object Storage • Cloud Infrastructure • Multi-Region Resilience</sub>

</p>

 

<p align="center">

  <a href="#-experiments">Experiments</a> •

  <a href="#-repository-structure">Structure</a> •

  <a href="#-learning-progression">Learning Path</a> •

  <a href="#-security-focus">Security</a>

</p>

 

---

 

## 📌 About

 

This repository contains the practical work completed for the **Cloud Application Development Lab** using **Amazon Web Services (AWS)**.

 

The repository is organized experiment-wise, with each practical documented independently through its own `README.md`, implementation notes, configuration details, observations, and screenshot evidence.

 

The experiments focus on learning cloud concepts by actually creating, configuring, accessing, managing, securing, verifying, and cleaning up AWS resources rather than studying the services only theoretically.

 

### The repository covers

 

- ☁️ Cloud computing

- 🖥️ Virtual machines

- 🔐 Identity and access management

- 🪣 Object storage

- 🌐 Cloud infrastructure

- 🔄 Data replication

- 🌍 Multi-region resilience

- 🛡️ Basic cloud security

- 🧪 Practical verification

- 📸 Screenshot-based documentation

- 🧹 AWS resource cleanup and cost awareness

 

---

 

# 🎯 Repository Objective

 

The main objective is to build a practical foundation in AWS cloud application development through progressive hands-on experiments.

 

The overall workflow followed throughout the repository is:

 

```text

            LEARN

              │

              ▼

          CONFIGURE

              │

              ▼

           CREATE

              │

              ▼

            ACCESS

              │

              ▼

           MANAGE

              │

              ▼

           SECURE

              │

              ▼

            TEST

              │

              ▼

           VERIFY

              │

              ▼

          DOCUMENT

              │

              ▼

          CLEAN UP

```

 

Each experiment adds another layer to the understanding of cloud-based application infrastructure.

 

---

 

# 🧪 Experiments

 

| # | Experiment | Primary AWS Service | Core Focus | Status |

|---|---|---|---|---|

| **01** | [Introduction to Amazon EC2](./experiment-1/README.md) | Amazon EC2 | Cloud VM, AMI, instance configuration, Security Groups, remote access | ✅ Completed |

| **02** | [Introduction to AWS IAM](./experiment-2/README.md) | AWS IAM | Users, policies, authentication, authorization, explicit Deny, least privilege | ✅ Completed |

| **03** | [Creating Buckets and Managing Objects](./experiment-3/README.md) | Amazon S3 | Buckets, objects, object keys, uploads, management, S3 security | ✅ Completed |

| **04** | [Introduction to Amazon EC2 — GCE → AWS](./experiment-4/README.md) | Amazon EC2 | Google Compute Engine assignment adapted to AWS EC2 | ✅ Completed |

| **05** | [Multi-Region S3 Backup Using Cross-Region Replication](./experiment-5/README.md) | Amazon S3 | Versioning, CRR, Batch Replication, IAM roles, resilience | ✅ Completed |

 

---

 

# 📂 Repository Structure

 

```text

cloud-application-development/

│

├── README.md

│

├── experiment-1/

│   ├── README.md

│   └── screenshots/

│

├── experiment-2/

│   ├── README.md

│   └── screenshots/

│

├── experiment-3/

│   ├── README.md

│   └── screenshots/

│

├── experiment-4/

│   ├── README.md

│   └── screenshots/

│

└── experiment-5/

    ├── README.md

    ├── screenshots/

    └── notes/

```

 

> Each experiment is intentionally self-contained so that the practical, its explanation, and its evidence can be reviewed independently.

 

---

 

# 🧭 Experiments Overview

 

## 01 — 🖥️ Introduction to Amazon EC2

 

### What this experiment covers

 

The first experiment introduces **Amazon Elastic Compute Cloud (Amazon EC2)** and the fundamental workflow of launching and working with a cloud-based Linux virtual machine.

 

The practical focuses on understanding how a cloud VM is provisioned, secured, accessed remotely, and inspected.

 

### Key work

 

- Opened the Amazon EC2 service

- Selected the required AWS Region

- Selected an Amazon Machine Image (AMI)

- Selected an EC2 instance type

- Launched an EC2 instance

- Configured a Security Group

- Allowed SSH access through port `22`

- Waited for the instance to reach the `Running` state

- Connected using **EC2 Instance Connect**

- Inspected the Linux operating system

- Verified CPU, memory, storage, hostname, and network configuration

- Cleaned up the resource after completion

 

### Core workflow

 

```text

AWS Management Console

        │

        ▼

   Launch EC2

        │

        ├── AMI

        ├── Instance Type

        └── Security Group

                │

                ▼

          Running Instance

                │

                ▼

       EC2 Instance Connect

                │

                ▼

       Linux System Inspection

                │

                ▼

             Cleanup

```

 

### Concepts practiced

 

- Amazon EC2

- AMIs

- Instance types

- Virtual machines

- Security Groups

- SSH

- EC2 Instance Connect

- Linux command line

- Cloud resource lifecycle

 

### Linux commands practiced

 

```text

whoami

pwd

cat /etc/os-release

hostname

lscpu

free -h

df -h

ip addr

```

 

📁 **Detailed documentation:** [Experiment 1 README](./experiment-1/README.md)

 

---

 

## 02 — 🔐 Introduction to AWS IAM

 

### What this experiment covers

 

The second experiment introduces **AWS Identity and Access Management (IAM)** and demonstrates how AWS identities and policies control access to cloud resources.

 

The practical work focused on users, permissions, policies, authentication, authorization, explicit Deny, and the principle of least privilege.

 

### Key work

 

- Opened AWS IAM

- Created and managed IAM users

- Reviewed IAM user configurations

- Examined permissions

- Explored IAM policies

- Studied JSON-based policy statements

- Used Amazon S3 permissions as a practical authorization example

- Worked with broad permissions such as `s3:*`

- Restricted the high-impact `s3:DeleteBucket` operation

- Demonstrated explicit `Deny` precedence

- Applied least-privilege thinking

- Verified the resulting permission behavior

 

### IAM authorization model

 

```text

                Requester

                    │

                    ▼

             Authentication

                    │

                    ▼

                Identity

                    │

                    ▼

              Authorization

                    │

                    ▼

              IAM Policies

                    │

                    ▼

              AWS Resource

```

 

### Explicit Deny demonstration

 

```text

        Allow: s3:*

              +

  Deny: s3:DeleteBucket

              │

              ▼

   DeleteBucket = DENIED

```

 

The practical demonstrated that an applicable explicit `Deny` overrides an applicable `Allow`.

 

### Policy model practiced

 

```json

{

  "Version": "2012-10-17",

  "Statement": [

    {

      "Sid": "AllowS3Access",

      "Effect": "Allow",

      "Action": "s3:*",

      "Resource": "*"

    },

    {

      "Sid": "DenyBucketDeletion",

      "Effect": "Deny",

      "Action": "s3:DeleteBucket",

      "Resource": "*"

    }

  ]

}

```

 

### Core security concepts

 

- Authentication

- Authorization

- IAM users

- IAM policies

- Policy statements

- `Effect`

- `Action`

- `Resource`

- Allow

- Explicit Deny

- Least privilege

- S3 authorization

 

📁 **Detailed documentation:** [Experiment 2 README](./experiment-2/README.md)

 

---

 

## 03 — 🪣 Creating Buckets and Managing Objects

 

### What this experiment covers

 

The third experiment focuses on **Amazon Simple Storage Service (Amazon S3)** and introduces the fundamentals of cloud object storage.

 

The practical was performed using the **AWS Management Console** and covers the creation of an S3 bucket and basic object-management operations.

 

### Key work

 

- Opened Amazon S3

- Created an S3 bucket

- Selected an AWS Region

- Reviewed bucket configuration

- Reviewed public-access protection

- Uploaded files as S3 objects

- Viewed stored objects

- Inspected object properties

- Performed object-management operations

- Understood object keys

- Reviewed basic S3 security

- Verified the final bucket and object state

 

### S3 architecture

 

```text

AWS Account

     │

     ▼

 Amazon S3

     │

     ▼

   Bucket

     │

     ├── Object

     ├── Object

     └── Object

```

 

### Bucket vs Object

 

| Component | Meaning |

|---|---|

| **Bucket** | Logical container for S3 objects |

| **Object** | Actual stored data |

| **Object Key** | Unique name/path-like identifier for an object |

| **Region** | AWS Region where the bucket is created |

| **Metadata** | Information associated with the object |

 

### Typical object workflow

 

```text

Create Bucket

      │

      ▼

Upload Object

      │

      ▼

View / Inspect

      │

      ▼

Manage Object

      │

      ▼

Verify

```

 

### Security concepts

 

- Block Public Access

- IAM permissions

- Bucket policies

- Object ownership

- Encryption

- HTTPS/TLS

- Least privilege

 

📁 **Detailed documentation:** [Experiment 3 README](./experiment-3/README.md)

 

---

 

## 04 — 🖥️ Introduction to Amazon EC2 — Changed from Google Compute Engine

 

### Why this experiment exists

 

This experiment was originally designed around **Google Compute Engine (GCE)**.

 

Because GCP access was not available for the practical, the assignment was implemented using the AWS equivalent: **Amazon EC2**.

 

The experiment therefore demonstrates the same broad cloud-compute idea using AWS infrastructure.

 

> **Original platform:** Google Cloud Platform / Google Compute Engine  

> **Implemented platform:** Amazon Web Services / Amazon EC2

 

### AWS configuration used

 

| Parameter | Configuration |

|---|---|

| AWS Service | Amazon EC2 |

| Region | Asia Pacific (Mumbai) — `ap-south-1` |

| Instance Type | `t3.micro` |

| Operating System | Amazon Linux 2023 |

| Access Method | EC2 Instance Connect |

| Security | Security Group + SSH |

| SSH Port | `22` |

 

### Practical workflow

 

```text

AWS Console

     │

     ▼

Launch EC2 Instance

     │

     ├── Amazon Linux 2023

     ├── t3.micro

     └── Security Group

              │

              ▼

        SSH / Port 22

              │

              ▼

      EC2 Instance Connect

              │

              ▼

     Linux System Inspection

```

 

### Steps performed

 

1. Opened Amazon EC2.

2. Selected Mumbai (`ap-south-1`).

3. Launched a `t3.micro` instance.

4. Selected Amazon Linux 2023.

5. Configured SSH access on port `22`.

6. Waited for the instance to reach `Running`.

7. Connected through EC2 Instance Connect.

8. Inspected the Linux system.

9. Verified OS, CPU, memory, storage, hostname, and network information.

10. Cleaned up the AWS resource after completion.

 

### Concepts reinforced

 

- Cloud virtual machines

- Amazon EC2

- AMIs

- Instance types

- Security Groups

- SSH

- EC2 Instance Connect

- Linux system inspection

- AWS resource lifecycle

 

### Platform mapping

 

```text

Google Cloud

     │

     ▼

Google Compute Engine

     │

     │  Assignment adapted to AWS

     ▼

Amazon Web Services

     │

     ▼

Amazon EC2

```

 

This experiment reinforces the idea that the fundamental cloud-compute workflow remains similar across major cloud providers even though service names and console interfaces differ.

 

📁 **Detailed documentation:** [Experiment 4 README](./experiment-4/README.md)

 

---

 

## 05 — 🌍 Multi-Region S3 Backup Using Cross-Region Replication

 

### What this experiment covers

 

The fifth experiment extends the S3 knowledge from Experiment 3 into a **multi-region backup and resilience architecture**.

 

The practical uses two Amazon S3 buckets located in different AWS Regions.

 

### Architecture

 

```text

┌─────────────────────────────────────────┐

│ SOURCE                                  │

│ US East (N. Virginia) — us-east-1      │

│                                         │

│ cad-exp4-source-nitanshu                │

└───────────────────┬─────────────────────┘

                    │

                    │ S3 Cross-Region

                    │ Replication (CRR)

                    │

                    ▼

┌─────────────────────────────────────────┐

│ DESTINATION                             │

│ Asia Pacific (Mumbai) — ap-south-1     │

│                                         │

│ cad-exp4-destination-nitanshu           │

└─────────────────────────────────────────┘

```

 

### Practical configuration

 

| Component | Configuration |

|---|---|

| AWS Service | Amazon S3 |

| Source Bucket | `cad-exp4-source-nitanshu` |

| Source Region | `us-east-1` |

| Destination Bucket | `cad-exp4-destination-nitanshu` |

| Destination Region | `ap-south-1` |

| Replication | Cross-Region Replication |

| Account | Same AWS account |

| Versioning | Enabled on both buckets |

| Replication Rule | `CRR-to-ap-south-1` |

| Rule Status | Enabled |

| Rule Scope | All objects |

| IAM Role | Created through S3 Console |

| Test Object | `scheduler.pdf` |

 

### Versioning

 

Versioning was enabled on both the source and destination buckets.

 

```text

Source Bucket

Versioning = ENABLED

 

        │

        │ CRR

        ▼

 

Destination Bucket

Versioning = ENABLED

```

 

Versioning is an important prerequisite for the replication configuration used in this practical and also provides protection against accidental overwrites and deletions by preserving object versions.

 

### Live Replication vs Batch Replication

 

A major concept demonstrated in this experiment is the difference between live replication and replication of existing objects.

 

#### Live CRR

 

```text

New / Updated Object

        │

        ▼

Source Bucket

        │

        │ Live CRR

        ▼

Destination Bucket

```

 

#### Batch Replication

 

```text

Existing Object

       │

       ▼

S3 Batch Operations

       │

       │ Batch Replication

       ▼

Destination Bucket

```

 

The test object `scheduler.pdf` already existed before the live replication rule was configured.

 

Therefore, **S3 Batch Replication** was used to backfill the existing object.

 

### Concepts practiced

 

- Amazon S3

- S3 Versioning

- Cross-Region Replication

- Replication rules

- Same-account replication

- IAM roles

- Replication scope

- S3 Batch Operations

- Replication manifests

- Batch job monitoring

- Multi-region backup

- Disaster recovery concepts

- Geographic redundancy

- Cost awareness

- Resource cleanup

 

### Security approach

 

The practical intentionally kept the buckets private.

 

Key principles included:

 

- Avoid unnecessary public access

- Use IAM roles for service permissions

- Enable Versioning

- Keep the backup copy in a separate Region

- Grant only required replication permissions

- Avoid unnecessary configuration complexity

- Clean up temporary lab resources

 

### Verification

 

The practical successfully verified:

 

```text

Source Bucket

      │

      │ CRR / Batch Replication

      ▼

Destination Bucket

      │

      ▼

scheduler.pdf

      │

      ▼

Replication Verified ✅

```

 

After verification, the temporary source and destination resources were cleaned up.

 

📁 **Detailed documentation:** [Experiment 5 README](./experiment-5/README.md)

 

---

 

# 🔗 How the Five Experiments Connect

 

The experiments form a broader cloud-development learning path:

 

```text

┌───────────────────────────────────────┐

│ EXPERIMENT 01                         │

│ Amazon EC2                            │

│ Cloud Compute Fundamentals            │

└──────────────────┬────────────────────┘

                   │

                   ▼

┌───────────────────────────────────────┐

│ EXPERIMENT 02                         │

│ AWS IAM                               │

│ Identity & Access Control             │

└──────────────────┬────────────────────┘

                   │

                   ▼

┌───────────────────────────────────────┐

│ EXPERIMENT 03                         │

│ Amazon S3                             │

│ Buckets & Object Management           │

└──────────────────┬────────────────────┘

                   │

                   ▼

┌───────────────────────────────────────┐

│ EXPERIMENT 04                         │

│ Amazon EC2                            │

│ GCE → AWS Platform Adaptation         │

└──────────────────┬────────────────────┘

                   │

                   ▼

┌───────────────────────────────────────┐

│ EXPERIMENT 05                         │

│ Amazon S3 CRR                         │

│ Multi-Region Backup & Resilience      │

└───────────────────────────────────────┘

```

 

The overall repository therefore moves through:

 

**Compute → Identity → Storage → Cross-Cloud Adaptation → Resilience**

 

---

 

# 🧠 Concepts Covered Across the Repository

 

## 🖥️ Compute

 

- Amazon EC2

- Cloud virtual machines

- AMIs

- Instance types

- Amazon Linux 2023

- SSH

- EC2 Instance Connect

- Linux system inspection

- Security Groups

 

## 🔐 Identity & Access

 

- AWS IAM

- IAM users

- Authentication

- Authorization

- IAM policies

- JSON policy statements

- Allow

- Explicit Deny

- Least privilege

- S3 permissions

 

## 🪣 Object Storage

 

- Amazon S3

- Buckets

- Objects

- Object keys

- Object properties

- Object management

- Block Public Access

- Encryption

- Versioning

 

## 🌍 Resilience

 

- Cross-Region Replication

- Live replication

- Batch Replication

- S3 Batch Operations

- Replication manifests

- IAM replication roles

- Geographic redundancy

- Multi-region backup

- Disaster recovery concepts

 

## 🔄 Cloud Platform Adaptation

 

Experiment 4 demonstrates how a practical originally designed around **Google Compute Engine** can be implemented using **Amazon EC2** when the required GCP environment is unavailable.

 

This introduces an important real-world cloud skill:

 

```text

Cloud Concept

     │

     ▼

Provider-Specific Service

     │

     ├── GCE

     │

     └── EC2

     │

     ▼

Same Fundamental Compute Goal

```

 

---

 

# 🛡️ Security Focus

 

Security is not treated as a separate topic limited to IAM. It appears throughout the experiments.

 

### Experiment 01 — EC2

 

```text

EC2

 │

 └── Security Group

          │

          └── Controlled SSH Access

```

 

### Experiment 02 — IAM

 

```text

Identity

   │

   ▼

IAM Policy

   │

   ├── Allow

   │

   └── Explicit Deny

           │

           ▼

     Least Privilege

```

 

### Experiment 03 — S3

 

```text

S3 Bucket

   │

   ├── Block Public Access

   ├── IAM Permissions

   ├── Encryption

   └── Controlled Object Access

```

 

### Experiment 04 — EC2 Adaptation

 

```text

Cloud VM

   │

   ├── Security Group

   ├── SSH

   └── Controlled Remote Access

```

 

### Experiment 05 — S3 Replication

 

```text

Source Bucket

      │

      ├── Versioning

      ├── IAM Role

      └── CRR

            │

            ▼

Destination Bucket

```

 

The combined experiments demonstrate that cloud security is **layered** across identity, network access, resource configuration, storage controls, and resilience.

 

---

 

# 📸 Screenshot & Evidence Structure

 

Each experiment contains screenshot evidence documenting the important stages of the practical.

 

| Experiment | Typical Evidence |

|---|---|

| **01 — EC2** | Instance launch, running state, Security Group, EC2 Instance Connect, Linux verification |

| **02 — IAM** | IAM users, permissions, policies, JSON policy, explicit Deny, permission testing |

| **03 — S3** | Bucket creation, configuration, uploaded objects, object details, management operations |

| **04 — EC2 / GCE → AWS** | EC2 configuration, Security Group, terminal, OS verification, system inspection |

| **05 — S3 CRR** | Source bucket, Versioning, destination bucket, replication rule, IAM role, Batch job, replicated object, cleanup |

 

The individual experiment READMEs provide the detailed screenshot sequence for each practical.

 

---

 

# 📊 Experiment Comparison

 

| Area | Exp. 01 | Exp. 02 | Exp. 03 | Exp. 04 | Exp. 05 |

|---|---|---|---|---|---|

| **Primary Service** | EC2 | IAM | S3 | EC2 | S3 |

| **Main Focus** | Compute | Identity | Object Storage | Cloud Compute Adaptation | Resilience |

| **Virtual Machine** | ✅ | — | — | ✅ | — |

| **IAM** | — | ✅ | Supporting | Supporting | Replication Role |

| **S3** | — | Supporting | ✅ | — | ✅ |

| **Networking** | Security Group | Authorization | S3 Access | Security Group | Regional Architecture |

| **Security** | SSH Control | Policies + Deny | Public Access Protection | SSH Control | IAM + Private Buckets |

| **Multi-Region** | — | — | — | — | ✅ |

| **Status** | ✅ | ✅ | ✅ | ✅ | ✅ |

 

---

 

# 🛠️ AWS Services & Technologies

 

### AWS Services

 

- **Amazon EC2**

- **Amazon S3**

- **AWS Identity and Access Management (IAM)**

- **Amazon CloudFront** where applicable to the repository's broader cloud coursework

- **EC2 Instance Connect**

- **S3 Cross-Region Replication**

- **S3 Batch Operations**

- **Security Groups**

 

### Supporting Technologies

 

- AWS Management Console

- Amazon Linux 2023

- Linux command line

- SSH

- IAM Policy JSON

- HTTPS

- Cloud object storage

- AWS Regions

 

---

 

# 🧹 Cleanup & Cost Awareness

 

Temporary cloud resources should not be left active after a practical unless they are intentionally required.

 

The experiments therefore emphasize cleanup after verification.

 

Typical cleanup actions include:

 

- Terminating EC2 instances

- Removing temporary S3 objects

- Deleting temporary S3 buckets

- Removing versioned objects and delete markers where applicable

- Removing temporary replication configurations

- Reviewing resources after the practical

 

### Why cleanup matters

 

Cloud resources can generate charges even when they are only being used for educational experimentation.

 

A good cloud workflow is therefore:

 

```text

Create

  ↓

Configure

  ↓

Test

  ↓

Verify

  ↓

Document

  ↓

Clean Up

```

 

---

 

# 📈 Learning Progression

 

The repository builds practical knowledge in stages:

 

```text

01

EC2

│

├── Virtual Machines

├── AMIs

├── Instance Types

├── Security Groups

└── Remote Access

        │

        ▼

02

IAM

│

├── Users

├── Authentication

├── Authorization

├── Policies

└── Least Privilege

        │

        ▼

03

S3

│

├── Buckets

├── Objects

├── Object Keys

├── Object Management

└── Storage Security

        │

        ▼

04

EC2 — GCE → AWS

│

├── Cloud Platform Mapping

├── EC2 Provisioning

├── SSH

└── Linux Inspection

        │

        ▼

05

S3 CRR

│

├── Versioning

├── Replication

├── Batch Operations

├── IAM Roles

└── Multi-Region Resilience

```

 

This creates a practical foundation for more advanced cloud architectures.

 

---

 

# 🎓 Learning Outcomes

 

After completing these experiments, the learner should have practical exposure to:

 

- Launching and accessing AWS compute resources

- Working with Linux cloud instances

- Configuring basic network access

- Understanding IAM identities and permissions

- Reading IAM policy JSON

- Applying explicit Deny

- Applying least-privilege principles

- Creating and managing S3 buckets

- Uploading and managing S3 objects

- Understanding object keys and storage concepts

- Applying basic S3 security controls

- Understanding Versioning

- Configuring Cross-Region Replication

- Understanding Live vs Batch Replication

- Working with S3 Batch Operations

- Understanding replication manifests

- Thinking about regional redundancy

- Understanding cloud-provider service mapping

- Verifying AWS configurations

- Documenting practical work

- Cleaning up cloud resources responsibly

 

---

 

# 🔮 Future Extensions

 

The current experiments establish a strong foundation for more advanced cloud application development.

 

Potential future experiments include:

 

### 🌐 Networking

 

- Amazon VPC

- Subnets

- Route Tables

- Internet Gateways

- NAT Gateways

- Network ACLs

- VPC Flow Logs

 

### ⚙️ Application Development

 

- AWS Lambda

- API Gateway

- Amazon DynamoDB

- Amazon RDS

- Application Load Balancer

 

### 📊 Monitoring & Security

 

- Amazon CloudWatch

- AWS CloudTrail

- AWS WAF

- AWS Config

- IAM Roles

- Secrets Manager

 

### 🚀 Cloud Operations

 

- Auto Scaling

- Elastic Load Balancing

- Docker

- Container deployment

- CI/CD pipelines

- Infrastructure as Code

- AWS DevSecOps

 

---

 

# 📚 AWS Documentation

 

- [Amazon EC2 Documentation](https://docs.aws.amazon.com/ec2/)

- [AWS Identity and Access Management Documentation](https://docs.aws.amazon.com/iam/)

- [Amazon S3 Documentation](https://docs.aws.amazon.com/s3/)

- [Amazon S3 Replication Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html)

- [S3 Batch Replication Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-batch-replication-batch.html)

 

---

 

# 🏁 Final Repository Status

 

```text

╔══════════════════════════════════════════════════════╗

║             CLOUD APPLICATION DEVELOPMENT            ║

╠══════════════════════════════════════════════════════╣

║                                                      ║

║  EXPERIMENT 01  │ Amazon EC2                  │  ✅  ║

║  EXPERIMENT 02  │ AWS IAM                     │  ✅  ║

║  EXPERIMENT 03  │ Amazon S3                   │  ✅  ║

║  EXPERIMENT 04  │ EC2 — GCE → AWS             │  ✅  ║

║  EXPERIMENT 05  │ S3 Cross-Region Replication │  ✅  ║

║                                                      ║

║  Compute        │ Identity     │ Storage             ║

║  Security       │ Resilience   │ Verification        ║

║                                                      ║

║                 STATUS: COMPLETED 🚀                 ║

╚══════════════════════════════════════════════════════╝

```

 

---

 

# 👨‍💻 Author

 

**Nitanshu Tak**

 

B.Tech — Computer Science Engineering  

Cloud Computing & Virtualization Technology

 

---

 

<p align="center">

  <b>☁️ Cloud Application Development Lab</b><br>

  <sub>Learn → Build → Secure → Verify → Document</sub>

</p>

