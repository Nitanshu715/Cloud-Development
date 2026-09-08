# ☁️ Cloud Application Development — Experiment 4
## 🌍 Implementing Multi-Region Backup in Amazon S3 Using Cross-Region Replication

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Amazon%20S3-orange?logo=amazons3&logoColor=white" alt="Amazon S3">
  <img src="https://img.shields.io/badge/Replication-Cross--Region-blue" alt="Cross-Region Replication">
  <img src="https://img.shields.io/badge/Regions-2-purple" alt="Two AWS Regions">
  <img src="https://img.shields.io/badge/Console-AWS%20Management%20Console-yellow" alt="AWS Console">
  <img src="https://img.shields.io/badge/Status-Completed-success" alt="Completed">
</p>

<p align="center">
  <b>Multi-region object backup with Amazon S3 CRR</b><br>
  A hands-on AWS lab demonstrating Versioning, Cross-Region Replication, Batch Replication, IAM roles, replication manifests, verification, and cleanup.
</p>

---

## 📌 Experiment Overview

This experiment demonstrates how to build a simple **multi-region backup architecture using Amazon S3 Cross-Region Replication (CRR)**.

The practical uses two S3 buckets in different AWS Regions:

```text
┌───────────────────────────────────────┐
│ 🇺🇸 SOURCE REGION                     │
│ US East (N. Virginia) — us-east-1   │
│                                       │
│ cad-exp4-source-nitanshu              │
└───────────────────┬───────────────────┘
                    │
                    │  S3 Cross-Region
                    │  Replication (CRR)
                    │  asynchronous
                    ▼
┌───────────────────────────────────────┐
│ 🇮🇳 DESTINATION REGION                │
│ Asia Pacific (Mumbai) — ap-south-1  │
│                                       │
│ cad-exp4-destination-nitanshu         │
└───────────────────────────────────────┘
```

The experiment also demonstrates an important distinction between:

- **Live CRR** → continuously replicates eligible new and updated objects after replication is configured.
- **S3 Batch Replication** → performs on-demand replication of existing eligible objects.

Because the test object `scheduler.pdf` existed before the live replication rule was created, the lab used **Batch Replication** to backfill that object.

---

## 🎯 Aim

To implement a multi-region backup mechanism for Amazon S3 by configuring **Cross-Region Replication (CRR)** between a source bucket in `us-east-1` and a destination bucket in `ap-south-1`, and to verify that objects can be replicated across AWS Regions.

---

## 🧠 Learning Objectives

By completing this experiment, the following concepts were practiced:

- Amazon S3 bucket creation
- AWS Region selection
- S3 object storage
- S3 Versioning
- Cross-Region Replication (CRR)
- Replication rules
- Same-account replication
- IAM roles used by S3 replication
- Replication scope and destination configuration
- Live replication vs. Batch Replication
- S3 Batch Operations
- Replication manifests
- Replication job monitoring
- Multi-region backup architecture
- Disaster-recovery concepts
- Resource cleanup and cost awareness

---

## 🗺️ AWS Architecture

### High-Level Flow

```text
                    AMAZON S3
                       │
                       │
          ┌────────────┴────────────┐
          │                         │
          ▼                         ▼
   ┌──────────────┐          ┌──────────────┐
   │   SOURCE     │          │ DESTINATION  │
   │   BUCKET     │          │    BUCKET    │
   ├──────────────┤          ├──────────────┤
   │ us-east-1    │          │ ap-south-1   │
   │ N. Virginia  │          │ Mumbai       │
   │              │          │              │
   │ source       │ ───────► │ destination  │
   │ bucket       │   CRR    │ bucket       │
   └──────────────┘          └──────────────┘
```

### Practical Configuration

| Component | Configuration |
|---|---|
| AWS Service | Amazon S3 |
| Source bucket | `cad-exp4-source-nitanshu` |
| Source Region | `us-east-1` |
| Source location | US East (N. Virginia) |
| Destination bucket | `cad-exp4-destination-nitanshu` |
| Destination Region | `ap-south-1` |
| Destination location | Asia Pacific (Mumbai) |
| Replication type | Cross-Region Replication |
| Account relationship | Same AWS account |
| Versioning | Enabled on both buckets |
| Replication rule | `CRR-to-ap-south-1` |
| Rule status | Enabled |
| Rule scope | All objects |
| IAM role | Created through the S3 console |
| Existing-object handling | S3 Batch Replication |
| Test object | `scheduler.pdf` |

---

# 📚 Core Concepts

## 1. Amazon S3

Amazon Simple Storage Service (Amazon S3) is AWS object storage.

The basic hierarchy is:

```text
AWS Account
   │
   └── S3 Bucket
          │
          ├── Object
          ├── Object
          └── Object
```

A bucket is created in a particular AWS Region and can contain objects such as:

- Documents
- Images
- Videos
- Application files
- Logs
- Backups
- Datasets
- Static website assets

---

## 2. S3 Versioning

Versioning allows S3 to preserve multiple versions of objects with the same key.

For this experiment:

```text
Source bucket       → Versioning ENABLED
Destination bucket  → Versioning ENABLED
```

Versioning is required for S3 replication.

It also provides protection against accidental overwrites and deletions because previous object versions can remain recoverable.

---

## 3. Cross-Region Replication (CRR)

**Cross-Region Replication** automatically and asynchronously copies eligible objects from a source S3 bucket to a destination bucket in a **different AWS Region**.

In this experiment:

```text
us-east-1
    │
    │ CRR
    ▼
ap-south-1
```

CRR can be useful for:

- Disaster recovery
- Business continuity
- Geographic redundancy
- Compliance requirements
- Regional resilience
- Maintaining a secondary copy of important data

---

## 4. Live Replication vs Batch Replication

### 🔄 Live Replication

Live replication handles eligible objects written or updated after the replication configuration is established.

```text
New object
    │
    ▼
Source bucket
    │
    │ Live CRR
    ▼
Destination bucket
```

### 📦 Batch Replication

Batch Replication is an on-demand mechanism for existing eligible objects.

```text
Existing object
       │
       ▼
S3 Batch Operations
       │
       │ Batch Replication
       ▼
Destination bucket
```

This distinction was a key part of the experiment.

---

# 🧪 Practical Workflow

## Phase 1 — Create the Source Bucket

The source bucket was created in:

```text
Region:
US East (N. Virginia)

Region code:
us-east-1

Bucket:
cad-exp4-source-nitanshu
```

### Configuration

- Public access remained blocked.
- Versioning was enabled.
- Standard S3 server-side encryption was used.
- The bucket was kept private for the practical.

---

## Phase 2 — Create the Destination Bucket

The destination bucket was created in:

```text
Region:
Asia Pacific (Mumbai)

Region code:
ap-south-1

Bucket:
cad-exp4-destination-nitanshu
```

Versioning was also enabled on this bucket.

The important architectural requirement was:

```text
Source Region ≠ Destination Region
```

Therefore:

```text
us-east-1 ≠ ap-south-1
```

which makes this a Cross-Region Replication configuration.

---

# 📄 Phase 3 — Upload Initial Test Object

The test object used during the practical was:

```text
scheduler.pdf
```

It was uploaded to:

```text
cad-exp4-source-nitanshu
```

At this stage, the object existed before the live CRR rule was configured.

That detail became important later.

---

# ⚙️ Phase 4 — Configure the CRR Rule

The source bucket was opened:

```text
Amazon S3
  → Buckets
  → cad-exp4-source-nitanshu
  → Management
  → Replication rules
  → Create replication rule
```

### Replication rule

```text
Rule name:
CRR-to-ap-south-1

Status:
Enabled

Scope:
Apply to all objects in the bucket
```

### Destination

The destination was selected from the same AWS account:

```text
cad-exp4-destination-nitanshu
```

The console confirmed:

```text
Destination Region:
Asia Pacific (Mumbai)
ap-south-1
```

### IAM

The S3 console was allowed to:

```text
Create new role
```

This provided the permissions required for S3 to perform the replication workflow.

---

# 🧩 Phase 5 — Handle Existing Objects

At the time the replication rule was created, the console offered the option to replicate existing objects.

This was important because:

```text
scheduler.pdf
```

already existed before CRR was configured.

Therefore, the practical used:

```text
S3 Batch Replication
```

instead of relying only on live replication.

---

# 📦 Phase 6 — Create the Batch Operations Job

The Batch Operations workflow opened:

```text
Create Batch Operations job
```

The practical used:

```text
Job run:
Automatically run the job when it's ready

Completion report:
Enabled

Completion report scope:
All tasks

Destination account:
This account

IAM:
Create new role
```

The Batch Replication job was successfully created.

---

# 🧾 Understanding the Replication Manifest

A Batch Replication job requires a **manifest**.

A manifest is essentially a list of S3 objects that tells the Batch Operations job which objects should be processed.

Conceptually:

```text
Replication Manifest
        │
        ├── Bucket
        ├── Object key
        └── Version information where applicable
```

Amazon S3 can generate a manifest based on the replication configuration.

During the practical, a job-related folder appeared in the destination bucket:

```text
job-<batch-job-id>/
```

This should not be confused with the original application/test object.

It was associated with the Batch Operations / manifest workflow.

---

# 🚀 Phase 7 — Monitor the Batch Job

The Batch Operations page initially showed the job as:

```text
New
```

After processing began, it changed to:

```text
Active
```

The practical showed:

```text
Total objects: 1
% Complete: 0%
Total failed: 0
```

The job was allowed to process automatically.

---

# ✅ Phase 8 — Verify Replication

The console was switched to:

```text
Asia Pacific (Mumbai)
ap-south-1
```

Then:

```text
S3
  → Buckets
  → cad-exp4-destination-nitanshu
  → Objects
```

The destination bucket showed:

```text
scheduler.pdf
```

This demonstrated that the existing object had successfully reached the Mumbai destination through the Batch Replication workflow.

---

# 🔍 What Was Actually Demonstrated?

The experiment demonstrated two related replication concepts:

### Existing object

```text
scheduler.pdf
       │
       │ existed before CRR
       ▼
S3 Batch Replication
       │
       ▼
Mumbai destination
```

### Ongoing replication architecture

```text
Future eligible objects
       │
       ▼
US East source
       │
       │ Live CRR
       ▼
Mumbai destination
```

Therefore, the lab was not just about creating two buckets.

It demonstrated how S3 can be used as part of a **multi-region backup strategy**.

---

# 🔐 Security Considerations

The practical intentionally kept the buckets private.

Recommended principles demonstrated by the lab:

- Avoid unnecessary public access.
- Use IAM roles instead of embedding credentials in applications.
- Enable Versioning for data protection.
- Keep backup destinations separated from the source Region.
- Grant only the permissions required by the replication workflow.
- Avoid unnecessary KMS complexity unless encryption requirements demand it.
- Clean up temporary lab resources after completion.

---

# 🛡️ Disaster Recovery Perspective

The architecture provides a simple regional redundancy pattern:

```text
             PRIMARY DATA
                  │
                  ▼
       ┌─────────────────────┐
       │   us-east-1         │
       │   Source S3 Bucket  │
       └──────────┬──────────┘
                  │
                  │ CRR
                  ▼
       ┌─────────────────────┐
       │   ap-south-1        │
       │ Destination Bucket  │
       └─────────────────────┘
                  │
                  ▼
          SECONDARY COPY
```

If the application needs to recover data from another Region, having a geographically separate copy can be valuable.

CRR alone, however, should not be interpreted as a complete disaster-recovery architecture. Real production systems may additionally require:

- Recovery procedures
- Application failover
- DNS / routing strategy
- Monitoring and alerting
- IAM controls
- Backup retention policies
- RPO/RTO planning
- Encryption/key-management strategy
- Lifecycle and cost policies

---

# 💰 Cost Awareness

AWS cloud resources should be deleted after a temporary practical when they are no longer required.

This experiment created:

- Two S3 buckets
- Versioned objects
- A CRR configuration
- IAM roles
- A Batch Operations job
- Replication/manifest-related objects

After verification, the buckets were emptied and deleted.

### Cleanup performed

```text
Source bucket
      ↓
Remove objects / versions
      ↓
Delete bucket

Destination bucket
      ↓
Remove objects / versions
      ↓
Delete bucket
```

Because Versioning was enabled, simply deleting the visible object is not necessarily sufficient to remove every stored version.

---

# 🧹 Final Cleanup

The practical resources were cleaned up after successful verification.

### Source

```text
cad-exp4-source-nitanshu
```

### Destination

```text
cad-exp4-destination-nitanshu
```

Both buckets were emptied and deleted.

The purpose was to avoid leaving unnecessary storage resources active after the lab.

---

# 📊 Final Results

| Check | Result |
|---|---|
| Source bucket created | ✅ |
| Source Region | ✅ `us-east-1` |
| Destination bucket created | ✅ |
| Destination Region | ✅ `ap-south-1` |
| Versioning on source | ✅ |
| Versioning on destination | ✅ |
| CRR rule created | ✅ |
| CRR rule enabled | ✅ |
| Destination configured | ✅ Mumbai |
| IAM role created | ✅ |
| Batch Replication job created | ✅ |
| Batch job processed | ✅ |
| Existing object replicated | ✅ |
| Destination verification | ✅ |
| Resource cleanup | ✅ |

---

# 🧠 Key Takeaways

> **1. S3 replication requires Versioning on both buckets.**

> **2. CRR replicates across different AWS Regions.**

> **3. Live replication is asynchronous.**

> **4. Objects that existed before the live replication configuration are not automatically replicated retroactively.**

> **5. S3 Batch Replication can be used to backfill existing objects.**

> **6. Batch Replication uses a manifest to identify objects for the Batch Operations job.**

> **7. IAM roles provide AWS services with the permissions required to perform replication operations.**

> **8. A destination Region provides geographic separation from the source Region.**

> **9. Versioned buckets require careful cleanup because object versions can remain after normal deletes.**

> **10. A production multi-region backup design requires more than replication alone — monitoring, recovery procedures, security, cost controls, and RPO/RTO planning also matter.**

---

# 🎓 Viva / Interview Questions

### Q1. What is Amazon S3?

Amazon S3 is an AWS object storage service used to store and retrieve objects in buckets.

### Q2. What is Cross-Region Replication?

CRR is an S3 live replication mechanism that asynchronously copies eligible objects between buckets in different AWS Regions.

### Q3. Why were two Regions used?

To create a geographically separated copy and demonstrate Cross-Region Replication.

### Q4. Which Regions were used?

```text
Source:
us-east-1 — US East (N. Virginia)

Destination:
ap-south-1 — Asia Pacific (Mumbai)
```

### Q5. Why is Versioning required?

S3 replication requires Versioning to be enabled on both source and destination buckets.

### Q6. Does CRR automatically copy objects that existed before the rule?

No. Existing objects are not automatically replicated retroactively by live replication.

### Q7. How can existing objects be replicated?

Using S3 Batch Replication.

### Q8. What is an S3 replication manifest?

It is an S3 object containing the object list that a Batch Operations job should process.

### Q9. Is S3 replication synchronous?

No. S3 replication is asynchronous.

### Q10. What is the difference between CRR and SRR?

```text
CRR → Different AWS Regions
SRR → Same AWS Region
```

### Q11. Why was an IAM role created?

The AWS service needs appropriate permissions to perform the replication operations.

### Q12. Why should backup buckets normally remain private?

Because backup data can be sensitive and public access unnecessarily increases the risk of unauthorized data exposure.

---

# 🖼️ Suggested Screenshot Evidence

Add screenshots to the repository's experiment documentation if required.

Recommended evidence:

1. Source bucket in `us-east-1`
2. Source bucket Versioning enabled
3. Destination bucket in `ap-south-1`
4. Destination bucket Versioning enabled
5. `scheduler.pdf` in source bucket
6. CRR rule creation page
7. Mumbai destination selected
8. IAM role configuration
9. Enabled replication rule
10. Batch Operations job creation
11. Successful Batch Operations job creation
12. Batch job status
13. `scheduler.pdf` visible in Mumbai
14. Batch job / manifest-related object
15. Final replication verification
16. Source bucket cleanup
17. Destination bucket cleanup

---

# 📁 Repository Structure

A clean repository can use the following structure:

```text
cloud-application-development/
│
├── README.md
│
├── Experiment-01/
│   ├── README.md
│   └── screenshots/
│
├── Experiment-02/
│   ├── README.md
│   └── screenshots/
│
├── Experiment-03/
│   ├── README.md
│   └── screenshots/
│
└── Experiment-04/
    ├── README.md
    ├── screenshots/
    │   ├── 01-source-bucket.png
    │   ├── 02-versioning-source.png
    │   ├── 03-destination-bucket.png
    │   ├── 04-versioning-destination.png
    │   ├── 05-source-object.png
    │   ├── 06-replication-rule.png
    │   ├── 07-destination-selection.png
    │   ├── 08-iam-role.png
    │   ├── 09-rule-enabled.png
    │   ├── 10-batch-job.png
    │   ├── 11-job-created.png
    │   ├── 12-job-status.png
    │   ├── 13-replicated-object.png
    │   └── 14-cleanup.png
    │
    └── notes/
        └── experiment-notes.md
```

---

# 🏁 Final Status

```text
╔══════════════════════════════════════════════╗
║       CLOUD APPLICATION DEVELOPMENT          ║
║               EXPERIMENT 04                  ║
╠══════════════════════════════════════════════╣
║                                              ║
║  Amazon S3 Cross-Region Replication          ║
║                                              ║
║  Source      : us-east-1                     ║
║  Destination : ap-south-1                    ║
║  Versioning  : Enabled                       ║
║  CRR         : Configured                    ║
║  Batch Rep.  : Verified                      ║
║  Cleanup     : Completed                     ║
║                                              ║
║              STATUS: COMPLETED ✅            ║
╚══════════════════════════════════════════════╝
```

---

## 🔗 AWS Documentation

- [Amazon S3 Replication Overview](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html)
- [Setting Up Live Replication](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication-how-setup.html)
- [Replication Requirements](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication-requirements.html)
- [S3 Batch Replication](https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-batch-replication-batch.html)

---

<p align="center">
  <b>☁️ Cloud Application Development • Experiment 4</b><br>
  <sub>Amazon S3 • Cross-Region Replication • Multi-Region Backup</sub>
</p>


Note: The content above is the complete README.md source. Copy the contents of the code block/table cell into Experiment-04/README.md in the repository.
