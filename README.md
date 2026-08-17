# ☁️ AWS Cloud Development Lab



> A practical collection of AWS cloud experiments covering core cloud infrastructure, application development, security, and management services.



![AWS](https://img.shields.io/badge/AWS-Cloud%20Development-orange?logo=amazonaws)



---



## 📌 About



This repository contains the practical experiments performed as part of the **Cloud Development Lab**.



Each experiment focuses on understanding and implementing an AWS cloud service through the **AWS Management Console** and, where required, command-line tools.



The repository is organized experiment-wise so that each lab can be accessed, executed, and documented independently.



The experiments collectively cover important areas of cloud application development, infrastructure deployment, virtual machines, identity management, access control, security, and AWS service configuration.



---



## 🧪 Experiments



| Experiment | Topic | Status |

|---|---|---|

| **Experiment 1** | Amazon S3 + CloudFront — Static Website Delivery | ✅ Completed |

| **Experiment 2** | Introduction to Amazon EC2 | ✅ Completed |

| **Experiment 3** | Introduction to AWS IAM — Identity, Users & Access Policies | ✅ Completed |



---



## 📂 Repository Structure



```text

cloud-development/


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


└── README.md

```



---



## ☁️ Experiment 1 — S3 + CloudFront



**Topic:** Static website hosting and content delivery using Amazon S3 and Amazon CloudFront.



### Key Work



- Created an Amazon S3 bucket for static website content.


- Uploaded the `index.html` static web application.


- Configured Amazon S3 as the origin for Amazon CloudFront.


- Kept the S3 bucket private rather than exposing the storage origin directly.


- Enabled private S3 access through CloudFront.


- Configured the default root object as `index.html`.


- Created and deployed a CloudFront distribution.


- Verified the CloudFront distribution and its deployment status.


- Accessed and validated the final static website through the CloudFront HTTPS endpoint.


- Observed the role of CDN caching and edge-based content delivery.



### AWS Services Used



- Amazon S3


- Amazon CloudFront



📁 Detailed documentation is available in [`experiment-1/README.md`](experiment-1/README.md).



---



## 🖥️ Experiment 2 — Introduction to EC2



**Topic:** Launching and accessing a cloud-based virtual machine using Amazon EC2.



### Key Work



- Launched a free-tier eligible `t3.micro` EC2 instance.


- Used Amazon Linux 2023 as the operating system.


- Configured a Security Group for SSH access.


- Connected to the instance using EC2 Instance Connect.


- Verified the running state and instance configuration.


- Inspected CPU, memory, storage, operating system, hostname, and network information using Linux commands.


- Understood the basic lifecycle and management of an EC2 virtual machine.


- Observed how Security Groups control inbound network access to cloud infrastructure.



### AWS Services & Technologies Used



- Amazon EC2


- EC2 Instance Connect


- Security Groups


- Amazon Linux


- Linux command line



📁 Detailed documentation is available in [`experiment-2/README.md`](experiment-2/README.md).



---



## 🔐 Experiment 3 — Introduction to AWS IAM



**Topic:** Identity and Access Management using AWS IAM, including IAM users, permissions, policies, S3 access control, explicit Deny, and the principle of least privilege.



### Key Work



- Opened and explored the AWS Identity and Access Management (IAM) service.


- Created and managed two separate IAM users.


- Reviewed individual IAM user configurations.


- Inspected permissions assigned to IAM identities.


- Explored IAM policies and their JSON-based permission structure.


- Worked with Amazon S3 permissions as a practical authorization example.


- Understood the difference between authentication and authorization.


- Examined the relationship between IAM identities, policies, actions, and AWS resources.


- Worked with broad S3 permissions such as `s3:*`.


- Modified the permission model to restrict the high-impact `s3:DeleteBucket` action.


- Used an explicit `Deny` statement to prevent bucket deletion.


- Demonstrated that an explicit `Deny` overrides an applicable `Allow`.


- Applied the principle of least privilege by restricting an unnecessary destructive operation while retaining other required S3 access.


- Reviewed and verified the resulting permission behavior.


- Documented IAM as a security and access-control layer for AWS resources.



### IAM Policy Example



The restricted S3 permission model used in the experiment follows the structure below:



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



The important IAM security principle demonstrated here is:



```text

Allow + Explicit Deny

        ↓

Explicit Deny takes precedence

        ↓

s3:DeleteBucket → DENIED

```



This demonstrates how IAM policies can be used to create security guardrails around powerful cloud permissions.



### IAM Concepts Covered



- AWS Identity and Access Management


- IAM Users


- IAM Groups


- IAM Policies


- Policy Statements


- Allow and Deny


- Explicit Deny precedence


- Authentication


- Authorization


- AWS resource permissions


- Amazon S3 permissions


- `s3:*`


- `s3:DeleteBucket`


- Principle of Least Privilege


- Identity-based access control


- Permission testing and verification



### AWS Services Used



- AWS Identity and Access Management (IAM)


- Amazon S3



📁 Detailed documentation is available in [`experiment-3/README.md`](experiment-3/README.md).



---



## 🛠️ Technologies & Services



### AWS Services



- **Amazon Web Services (AWS)**


- Amazon S3


- Amazon CloudFront


- Amazon EC2


- AWS Identity and Access Management (IAM)


- EC2 Instance Connect


- Security Groups



### Operating Systems & Tools



- Amazon Linux 2023


- Linux command line


- AWS Management Console



### Core Cloud Concepts



- Object Storage


- Content Delivery Networks


- Cloud Computing


- Virtual Machines


- Network Security


- Identity and Access Management


- Authentication


- Authorization


- Access Policies


- Least Privilege


- Cloud Security



---



## 🎯 Purpose



The main objective of this repository is to build practical understanding of AWS infrastructure and cloud services by **creating, configuring, accessing, securing, and validating cloud resources** rather than only studying the concepts theoretically.



The experiments progressively demonstrate different layers of cloud computing:



```text

Experiment 1

Amazon S3 + CloudFront

        ↓

Static Application Storage & Delivery



Experiment 2

Amazon EC2

        ↓

Compute & Virtual Machine Infrastructure



Experiment 3

AWS IAM

        ↓

Identity, Authorization & Cloud Security

```



Together, these experiments provide practical exposure to:



```text

Storage

   +

Content Delivery

   +

Compute

   +

Networking

   +

Identity

   +

Access Control

   +

Security

```



---



## 🧠 Learning Progression



The repository follows a practical cloud-development progression:



### 1️⃣ Store and Deliver



**S3 + CloudFront**



Learn how static application files can be stored in cloud object storage and distributed through a CDN.



### 2️⃣ Compute and Access



**EC2**



Learn how to launch, configure, connect to, and inspect a cloud-based virtual machine.



### 3️⃣ Secure and Control



**IAM**



Learn how identities and policies control access to cloud resources and how permissions can be restricted using explicit security rules.



This creates a foundation for understanding larger AWS architectures where compute, storage, networking, application delivery, and security work together.



---



## 📊 Experiment Summary



| Area | Experiment 1 | Experiment 2 | Experiment 3 |

|---|---|---|---|

| Primary Service | S3 + CloudFront | EC2 | IAM |

| Main Concept | Static Content Delivery | Cloud Compute | Identity & Access Control |

| Storage | S3 | EBS / Instance Storage | S3 Permissions |

| Compute | — | EC2 | — |

| Networking | CloudFront Delivery | Security Group | IAM Authorization |

| Security | Private S3 Origin + HTTPS | Security Group | IAM Policies + Explicit Deny |

| Main Output | Deployed Website | Running Linux VM | Controlled AWS Permissions |

| Status | ✅ Completed | ✅ Completed | ✅ Completed |



---



## 📁 Experiment Documentation



Each experiment contains its own detailed documentation.



### Experiment 1



```text

experiment-1/

└── README.md

```



Covers:



- S3 bucket creation


- Static website files


- CloudFront origin configuration


- Private S3 access


- Default root object


- CDN deployment


- HTTPS access


- Testing and verification



### Experiment 2



```text

experiment-2/

└── README.md

```



Covers:



- EC2 instance creation


- Amazon Linux 2023


- Instance configuration


- Security Groups


- EC2 Instance Connect


- Linux system inspection


- Compute resource verification



### Experiment 3



```text

experiment-3/

└── README.md

```



Covers:



- IAM service


- IAM users


- User permissions


- IAM policies


- Policy JSON


- S3 authorization


- Explicit Deny


- `s3:DeleteBucket` restriction


- Least privilege


- Permission testing


- Cloud security concepts



---



## 🔒 Security Focus



Security is an important component of the experiments in this repository.



The practical work demonstrates security at multiple levels:



```text

Experiment 1

        ↓

Private S3 Origin

        +

HTTPS CloudFront Delivery



Experiment 2

        ↓

EC2 Security Group

        +

Controlled Network Access



Experiment 3

        ↓

IAM Users

        +

IAM Policies

        +

Least Privilege

        +

Explicit Deny

```



These examples demonstrate that cloud security is not a single configuration. It involves protecting storage, controlling network access, and managing identity and authorization.



---



## 🚀 Future Experiments



The repository can be extended with additional AWS experiments covering areas such as:



- Amazon VPC


- Subnets


- Route Tables


- Internet Gateways


- NAT Gateways


- AWS Lambda


- API Gateway


- Amazon DynamoDB


- Amazon RDS


- AWS CloudWatch


- AWS CloudTrail


- AWS WAF


- Route 53


- Auto Scaling


- Elastic Load Balancing


- Docker and container deployment


- CI/CD pipelines


- Infrastructure as Code


- AWS DevSecOps



---



## 🎯 Repository Goals



The long-term goal of this repository is to build a structured practical reference for AWS cloud development and security.



The experiments are intended to demonstrate the complete cloud workflow:



```text

Learn

  ↓

Configure

  ↓

Deploy

  ↓

Access

  ↓

Secure

  ↓

Test

  ↓

Verify

  ↓

Document

```



Rather than only recording theoretical definitions, each experiment focuses on actually interacting with AWS services and understanding how the services behave in a real cloud environment.



---



## 👨‍💻 Author



**Nitanshu Tak**



B.Tech — Computer Science Engineering



Cloud Computing & Virtualization Technology



---



> 🚀 **Cloud Development Lab — Learn → Build → Secure → Deploy → Verify**
