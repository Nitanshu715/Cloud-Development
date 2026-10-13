# ☁️ Cloud Application Development Lab

 

<p align="center">

  <img src="https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws&logoColor=white" alt="AWS">

  <img src="https://img.shields.io/badge/Experiments-7-blue" alt="7 experiments">

  <img src="https://img.shields.io/badge/Platform-AWS-yellow?logo=amazonaws&logoColor=white" alt="AWS">

</p>

 

<p align="center">

  **Hands-on AWS Cloud Application Development**  

  <br>

  <sub>Compute • Identity • Storage • Resilience • Serverless APIs</sub>

</p>

 

---

 

## About

 

This repository contains practical work completed for the **Cloud Application Development Lab** using Amazon Web Services (AWS). Each experiment has its own folder with a dedicated `README.md` and, where applicable, screenshots or supporting notes.

 

The experiments progress from core cloud infrastructure to identity and access management, object storage, replication, NoSQL databases, and serverless APIs.

 

## Experiments

 

### Experiment 1 — Introduction to Amazon EC2

 

**Service:** Amazon EC2  

**Focus:** Launching and accessing a cloud virtual machine.

 

- Selected an Amazon Machine Image (AMI) and instance type.

- Launched an EC2 instance and configured its Security Group.

- Used EC2 Instance Connect to access the Linux machine.

- Inspected the operating system, CPU, memory, storage, hostname, and network.

- Reviewed the instance lifecycle and cleanup.

 

**Documentation:** [`experiment-1/README.md`](./experiment-1/README.md)

 

---

 

### Experiment 2 — Introduction to AWS IAM

 

**Service:** AWS Identity and Access Management (IAM)  

**Focus:** Identities, permissions, and policy evaluation.

 

- Created and reviewed IAM users and permissions.

- Examined JSON policy statements and their `Effect`, `Action`, and `Resource` fields.

- Explored Allow and explicit Deny behavior.

- Demonstrated that an applicable explicit Deny overrides an Allow.

- Applied the principle of least privilege to AWS access.

 

**Documentation:** [`experiment-2/README.md`](./experiment-2/README.md)

 

---

 

### Experiment 3 — Creating Buckets and Managing Objects

 

**Service:** Amazon S3  

**Focus:** Cloud object storage and object management.

 

- Created an S3 bucket in the selected AWS Region.

- Reviewed bucket settings and Block Public Access.

- Uploaded files as S3 objects.

- Viewed object details and properties.

- Practiced basic object-management operations.

- Reviewed object keys, access permissions, and storage security.

 

**Documentation:** [`experiment-3/README.md`](./experiment-3/README.md)

 

---

 

### Experiment 4 — Introduction to Amazon EC2 (GCE-to-AWS Adaptation)

 

**Service:** Amazon EC2  

**Focus:** Completing a cloud-compute practical using AWS as the alternative to Google Compute Engine.

 

- Selected the Mumbai Region (`ap-south-1`).

- Launched a `t3.micro` instance using Amazon Linux 2023.

- Configured SSH access through port `22` in a Security Group.

- Connected using EC2 Instance Connect.

- Inspected the Linux system and verified basic system information.

- Cleaned up the instance after completing the practical.

 

**Documentation:** [`experiment-4/README.md`](./experiment-4/README.md)

 

---

 

### Experiment 5 — Multi-Region S3 Backup Using Cross-Region Replication

 

**Service:** Amazon S3  

**Focus:** Replicating objects between AWS Regions for resilience.

 

- Configured a source bucket in US East (N. Virginia), `us-east-1`.

- Configured a destination bucket in Asia Pacific (Mumbai), `ap-south-1`.

- Enabled Versioning on both buckets.

- Created an S3 Cross-Region Replication (CRR) rule and its IAM role.

- Used S3 Batch Replication to handle an existing object, `scheduler.pdf`.

- Verified the replicated object and reviewed cleanup.

 

**Documentation:** [`experiment-5/README.md`](./experiment-5/README.md)

 

---

 

### Experiment 6 — Amazon DynamoDB: Serverless NoSQL Database

 

**Service:** Amazon DynamoDB  

**Focus:** NoSQL data modeling and access patterns.

 

- Created the `StudentCourses` table with `StudentId` as the partition key and `CourseId` as the sort key.

- Inserted sample student-course registrations.

- Read and updated an item.

- Compared Query and Scan operations.

- Created the `Status-CourseId-index` Global Secondary Index (GSI).

- Queried registrations using the GSI and reviewed resource cleanup.

 

**Documentation:** [`experiment-6/README.md`](./experiment-6/README.md)

 

---

 

### Experiment 7 — Introduction to Amazon API Gateway

 

**Services:** Amazon API Gateway, AWS Lambda, Amazon CloudWatch  

**Focus:** Deploying and testing a serverless REST API.

 

- Configured the REST API `CAD-Experiment-7-REST-API` in Mumbai (`ap-south-1`).

- Created the `/students` resource with `GET` and `POST` methods.

- Integrated both methods with the Lambda function `cad-exp7-student-api` using Lambda proxy integration.

- Deployed the API to the `dev` stage.

- Configured API-key access through `CAD-Experiment-7-Usage-Plan`.

- Tested requests from PowerShell and inspected CloudWatch logs.

 

**Endpoint:**  

`https://6pnwbvfcy6.execute-api.ap-south-1.amazonaws.com/dev/students`

 

**Testing note:** Requests without the required API key returned HTTP `403`. Requests with the key reached Lambda, but the final response remained `Hello from Lambda!`. The intended student-specific GET/POST behavior was not verified; the Lambda handler configuration needs to be checked.

 

**Documentation:** [`experiment-7/README.md`](./experiment-7/README.md)

 

---

 

## Repository Structure

 

```text

cloud-application-development/

├── README.md

├── experiment-1/

│   ├── README.md

│   └── screenshots/

├── experiment-2/

│   ├── README.md

│   └── screenshots/

├── experiment-3/

│   ├── README.md

│   └── screenshots/

├── experiment-4/

│   ├── README.md

│   └── screenshots/

├── experiment-5/

│   ├── README.md

│   ├── screenshots/

│   └── notes/

├── experiment-6/

│   ├── README.md

│   └── screenshots/

└── experiment-7/

    ├── README.md

    └── screenshots/

```

 

## Learning Path

 

```text

EC2 Compute

    ↓

IAM Identity and Access

    ↓

S3 Object Storage

    ↓

EC2 Platform Adaptation

    ↓

Multi-Region S3 Replication

    ↓

DynamoDB NoSQL

    ↓

API Gateway + Lambda

```

 

## Core Skills Practiced

 

- **Compute:** EC2 instances, AMIs, instance types, Security Groups, SSH, Linux inspection.

- **Identity and security:** IAM users, policies, explicit Deny, least privilege, API-key controls.

- **Storage:** S3 buckets and objects, object keys, Versioning, Cross-Region Replication.

- **Databases:** DynamoDB primary keys, CRUD operations, Query, Scan, and GSIs.

- **Serverless applications:** API Gateway resources and methods, Lambda proxy integration, deployment stages, HTTPS testing.

- **Operations:** CloudWatch logs, verification, documentation, cleanup, and cost awareness.

 

## Security and Cleanup

 

- Use least-privilege permissions and avoid unnecessary public access.

- Keep API keys and credentials private; never commit real secrets to source control.

- Check CloudWatch logs when diagnosing failures.

- Remove temporary resources after collecting required evidence.

- Delete IAM roles only when they were created for a lab and are not used by other resources.

 

## AWS Documentation

 

- [Amazon EC2](https://docs.aws.amazon.com/ec2/)

- [AWS IAM](https://docs.aws.amazon.com/iam/)

- [Amazon S3](https://docs.aws.amazon.com/s3/)

- [Amazon DynamoDB](https://docs.aws.amazon.com/dynamodb/)

- [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/)

- [AWS Lambda](https://docs.aws.amazon.com/lambda/)

- [Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/)

 

---

 

## Author

 

**Nitanshu Tak**  

B.Tech — Computer Science Engineering  

Cloud Computing & Virtualization Technology

 

<p align="center">

  <b>Cloud Application Development Lab</b><br>

  <sub>Learn → Build → Secure → Verify → Document</sub>

</p>
