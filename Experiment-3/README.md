# Experiment - 3 - AWS Cloud Application Development Lab

> A practical experiment demonstrating Amazon S3 bucket creation and object management using the AWS Management Console.

![AWS](https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws) ![S3](https://img.shields.io/badge/Service-Amazon%20S3-blue?logo=amazons3) ![Storage](https://img.shields.io/badge/Focus-Object%20Storage-green) ![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 About

This folder contains the documentation for **Experiment 4** of the **Cloud Application Development Lab**.

The experiment focuses on **Amazon Simple Storage Service (Amazon S3)** and demonstrates the practical process of creating an S3 bucket and managing objects stored inside it.

The experiment was performed using the **AWS Management Console** rather than command-line tools. The purpose is to build practical familiarity with cloud object storage and understand how applications can store and manage files using AWS.

---

## 🧪 Experiment Information

| Parameter | Details |
|---|---|
| **Experiment** | Experiment 3 |
| **Subject** | Cloud Application Development |
| **Topic** | Creating Buckets and Managing Objects in AWS |
| **Cloud Platform** | Amazon Web Services (AWS) |
| **Primary Service** | Amazon Simple Storage Service (Amazon S3) |
| **Implementation** | AWS Management Console |
| **Main Concept** | Cloud Object Storage |
| **Key Operations** | Bucket Creation, Object Upload, Object Management |
| **Status** | ✅ Completed |

---

## 🎯 Aim

To create an Amazon S3 bucket and perform basic object-management operations using the AWS Management Console while understanding the fundamental concepts of cloud-based object storage.

---

## 🎯 Objectives

- Understand the purpose of Amazon S3.
- Understand the difference between an S3 bucket and an S3 object.
- Create an S3 bucket using the AWS Management Console.
- Understand basic bucket configuration.
- Upload files as objects into an S3 bucket.
- View and inspect stored objects.
- Perform basic object-management operations.
- Understand object keys and object properties.
- Understand basic S3 security considerations.
- Verify the final state of the bucket and its objects.

---

## ☁️ Introduction to Amazon S3

**Amazon Simple Storage Service (Amazon S3)** is an object storage service provided by AWS.

S3 allows users and applications to store and retrieve data at scale without managing physical storage infrastructure.

Instead of storing files in a traditional filesystem, S3 stores data as **objects** inside **buckets**.

The basic S3 structure can be represented as:

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

S3 can be used for:

- Application files
- Images and videos
- Documents
- Backups
- Logs
- Datasets
- Static website assets
- Software artifacts
- Archival storage

---

## 🪣 What is an S3 Bucket?

An **S3 bucket** is a logical container used to store objects.

Every object stored in Amazon S3 belongs to a bucket.

Important characteristics of S3 buckets include:

- Bucket names must follow AWS naming rules.
- Bucket names are globally unique within the S3 namespace.
- A bucket is created in a specific AWS Region.
- Bucket-level security and configuration can be applied.
- A bucket can contain a very large number of objects.
- Features such as versioning and lifecycle management can be configured at the bucket level.

Example:

```text
my-cloud-lab-bucket
```

---

## 📦 What is an S3 Object?

An **S3 object** is the actual data stored inside a bucket.

Examples include:

```text
index.html
image.png
report.pdf
data.csv
backup.zip
```

An object generally consists of:

- Object data
- Object key
- Metadata
- Storage class
- Version information, when versioning is enabled

Example:

```text
Bucket:
cloud-development-lab

Object:
documents/report.pdf
```

Here:

```text
Bucket = cloud-development-lab
Object Key = documents/report.pdf
```

---

## 🔑 Object Key

The **object key** is the name used to identify an object inside an S3 bucket.

For example:

```text
documents/report.pdf
images/cloud.png
website/index.html
```

S3 does not use a traditional hierarchical filesystem. The `/` character is commonly used in object keys to create a folder-like organization in the AWS Console.

---

## 🆚 Bucket vs Object

| Aspect | Bucket | Object |
|---|---|---|
| Purpose | Container for objects | Actual stored data |
| Example | `cloud-lab-bucket` | `report.pdf` |
| Identification | Bucket name | Object key |
| Configuration | Policies, versioning, lifecycle | Metadata, tags, storage class |
| Level | Bucket-level resource | Object-level resource |

---

## 🌎 AWS Region

An S3 bucket is associated with an AWS Region when it is created.

The Region determines where AWS stores the bucket's data infrastructure.

Region selection can be influenced by:

- Application latency
- Data residency requirements
- Compliance requirements
- Cost
- Proximity to users or applications
- Integration with other AWS services

---

## 🗄️ S3 Storage Classes

Amazon S3 provides different storage classes for different access patterns.

Common examples include:

- **S3 Standard** — frequently accessed data.
- **S3 Intelligent-Tiering** — data with changing or unknown access patterns.
- **S3 Standard-IA** — infrequently accessed data.
- **S3 One Zone-IA** — infrequently accessed data stored in a single Availability Zone.
- **S3 Glacier Instant Retrieval** — archival data requiring rapid retrieval.
- **S3 Glacier Flexible Retrieval** — archival storage with flexible retrieval times.
- **S3 Glacier Deep Archive** — long-term archival storage.

The correct storage class depends on:

- Frequency of access
- Retrieval requirements
- Retention period
- Cost considerations

---

## 🔐 S3 Security

S3 security is an important part of cloud application development.

Access to S3 resources should follow the **principle of least privilege**, meaning users and applications should receive only the permissions they actually require.

Important security mechanisms include:

- AWS IAM policies
- S3 bucket policies
- S3 Block Public Access
- Object Ownership
- Encryption
- HTTPS/TLS
- Logging and monitoring

### Public Access

S3 buckets should generally remain private unless public access is intentionally required.

For normal lab and application-storage use cases, **Block Public Access** should remain enabled.

---

## 🔄 Experiment Workflow

The practical workflow followed in this experiment was:

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
   Create Bucket
        │
        ▼
    Open Bucket
        │
        ▼
    Upload Object
        │
        ▼
   View Object
        │
        ▼
 Manage Object
        │
        ▼
 Final Verification
```

---

## 🛠️ Practical Procedure

### Step 1 — Open Amazon S3

1. Sign in to the AWS Management Console.
2. Search for **S3** using the AWS service search.
3. Open **Amazon S3**.
4. Navigate to the **Buckets** section.

---

### Step 2 — Create an S3 Bucket

1. Select **Create bucket**.
2. Enter a valid and globally unique bucket name.
3. Select the required AWS Region.
4. Review the Object Ownership settings.
5. Review the Block Public Access settings.
6. Keep public access blocked unless the experiment specifically requires otherwise.
7. Review the remaining settings.
8. Select **Create bucket**.

After successful creation, the new bucket should appear in the bucket list.

---

### Step 3 — Open the Bucket

1. Select the newly created bucket.
2. Open the bucket.
3. Navigate to the **Objects** section.

The bucket should initially contain no objects unless objects were added during creation or by another operation.

---

### Step 4 — Upload an Object

1. Select **Upload**.
2. Choose the required file from the local computer.
3. Review the selected file.
4. Start the upload.
5. Wait for the upload to complete.
6. Return to the Objects section.

The uploaded file should now appear as an object.

---

### Step 5 — Inspect the Object

Select the uploaded object to view its information.

Depending on the console view, object information may include:

- Object name
- Object key
- Object URL
- Object size
- Last modified time
- Storage class
- Encryption information
- Metadata
- Tags

---

### Step 6 — Manage the Object

Amazon S3 provides several object-management operations.

Common operations include:

- Download
- Copy
- Move
- Delete
- Open
- View properties
- Modify metadata or tags where applicable

The required operation for the experiment can be performed from the object-management interface.

---

## 📋 Object Management Operations

| Operation | Purpose |
|---|---|
| **Upload** | Adds a new object to the bucket |
| **View** | Displays object information |
| **Download** | Retrieves the object to the local system |
| **Copy** | Creates a copy of the object |
| **Move** | Relocates an object as supported by the console workflow |
| **Delete** | Removes an object from the bucket |

---

## ✅ Verification

The experiment can be considered successfully completed when:

- The S3 bucket appears in the bucket list.
- The bucket name is correct.
- The bucket was created in the intended Region.
- The bucket opens successfully.
- The Objects section is accessible.
- The uploaded object appears in the bucket.
- Object information can be inspected.
- The required object-management operation succeeds.
- The final bucket state is visible and correct.

---

## 🧪 Test Cases

| Test Case | Action | Expected Result | Status |
|---|---|---|---|
| **TC-01** | Open Amazon S3 | S3 Console opens successfully | ✅ Pass |
| **TC-02** | Create bucket | Bucket appears in bucket list | ✅ Pass |
| **TC-03** | Open bucket | Bucket contents page opens | ✅ Pass |
| **TC-04** | Upload object | Object appears in the bucket | ✅ Pass |
| **TC-05** | Inspect object | Object details are displayed | ✅ Pass |
| **TC-06** | Manage object | Required operation completes | ✅ Pass |
| **TC-07** | Final verification | Expected final state is visible | ✅ Pass |

---

## 📸 Screenshots

The practical screenshots captured during the experiment should be placed in this section.

Recommended order:

```text
01 — Amazon S3 Dashboard
02 — Create Bucket
03 — Bucket Created
04 — Bucket Overview
05 — Objects Section
06 — Upload Objects
07 — Uploaded Object
08 — Object Details
09 — Object Management
10 — Final Verification
```

Screenshots can be stored in this folder using a structure such as:

```text
experiment-4/
│
├── README.md
│
└── screenshots/
    ├── 01-s3-dashboard.png
    ├── 02-create-bucket.png
    ├── 03-bucket-created.png
    ├── 04-bucket-overview.png
    ├── 05-objects-section.png
    ├── 06-upload-object.png
    ├── 07-uploaded-object.png
    ├── 08-object-details.png
    ├── 09-object-management.png
    └── 10-final-verification.png
```

---

## 👀 Observations

During the experiment, the following observations were made:

- Amazon S3 uses an object-storage architecture.
- Buckets act as containers for stored objects.
- Objects are identified using object keys.
- Bucket names must satisfy global naming requirements.
- S3 buckets are associated with AWS Regions.
- The AWS Management Console provides a graphical interface for storage management.
- Objects can be uploaded and managed directly from the S3 Console.
- S3 provides multiple storage classes for different access patterns.
- S3 provides multiple mechanisms for controlling access.
- Public access should not be enabled unnecessarily.

---

## 🌐 Applications of Amazon S3

Amazon S3 is commonly used for:

### Application Storage

Applications can store documents, images, videos, reports, and other files.

### Backup and Recovery

S3 can be used as a destination for backup data and recovery workflows.

### Static Websites

HTML, CSS, JavaScript, images, and other static website resources can be stored in S3.

### Data Lakes

Large datasets can be stored in S3 and processed using AWS analytics services.

### Logging

Application and infrastructure logs can be stored for later analysis.

### Software Artifacts

Build artifacts, packages, installers, and deployment files can be stored in S3.

### Archival

S3 storage classes can be used for long-term retention and archival requirements.

---

## ⭐ Advantages of Amazon S3

- Highly durable object storage.
- Elastic storage capacity.
- No need to manage physical storage infrastructure.
- Integration with numerous AWS services.
- Multiple storage classes.
- Access-control mechanisms.
- Versioning support.
- Lifecycle management.
- Encryption capabilities.
- Management through Console, CLI, SDKs, and APIs.
- Suitable for small applications and large-scale cloud workloads.

---

## 🔒 Security Best Practices

When working with Amazon S3:

1. Follow the principle of least privilege.
2. Keep Block Public Access enabled unless public access is required.
3. Avoid storing sensitive information in publicly accessible buckets.
4. Use IAM policies to control identity permissions.
5. Use bucket policies only when required.
6. Enable encryption according to application requirements.
7. Use HTTPS/TLS for data transfer.
8. Protect AWS credentials.
9. Never commit AWS access keys to Git repositories.
10. Review permissions regularly.
11. Consider versioning for important data.
12. Remove temporary resources when they are no longer required.

---

## 📚 Key Concepts Learned

This experiment covered the following AWS concepts:

```text
Amazon S3
│
├── Buckets
│   ├── Bucket Name
│   ├── AWS Region
│   ├── Access Configuration
│   └── Bucket Settings
│
├── Objects
│   ├── Object Data
│   ├── Object Key
│   ├── Metadata
│   ├── Tags
│   └── Storage Class
│
├── Security
│   ├── IAM
│   ├── Bucket Policies
│   ├── Block Public Access
│   └── Encryption
│
└── Management
    ├── Upload
    ├── Download
    ├── Copy
    ├── Move
    └── Delete
```

---

## 🎓 Learning Outcomes

After completing this experiment, the following outcomes were achieved:

- Understanding of Amazon S3 fundamentals.
- Understanding of cloud object storage.
- Practical bucket creation experience.
- Practical object upload experience.
- Understanding of object keys and properties.
- Practical object-management experience.
- Understanding of basic S3 security.
- Understanding of storage classes.
- Understanding of versioning at a conceptual level.
- Ability to verify AWS storage operations using the Management Console.

---

## 📝 Result

The experiment was successfully completed.

An Amazon S3 bucket was created using the AWS Management Console, objects were uploaded into the bucket, object information was inspected, and the required object-management operations were performed successfully.

The experiment provided practical exposure to AWS object storage and demonstrated how S3 can be used as a fundamental storage component for cloud applications.

---

## 🏁 Conclusion

This experiment demonstrated the basic lifecycle of Amazon S3 object storage.

The practical work covered:

```text
Create
  ↓
Configure
  ↓
Store
  ↓
Inspect
  ↓
Manage
  ↓
Verify
```

Through this experiment, the relationship between **buckets and objects** was understood along with the importance of AWS Regions, object keys, storage classes, access control, and secure S3 configuration.

Amazon S3 provides a scalable and highly durable foundation for storing application data in cloud environments, making it one of the fundamental services used in AWS-based application development.

---

## 👨‍💻 Author

**Nitanshu Tak**

B.Tech — Computer Science Engineering  
Cloud Computing & Virtualization Technology

---

> 🚀 **Cloud Application Development Lab — Learn → Build → Manage → Verify**

