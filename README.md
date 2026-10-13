# ☁️ Cloud Application Development Lab

 

<p align="center">

  <img src="https://img.shields.io/badge/AWS-Cloud%20Application%20Development-orange?logo=amazonaws&logoColor=white" alt="AWS">

  <img src="https://img.shields.io/badge/Experiments-7-blue" alt="7 Experiments">

  <img src="https://img.shields.io/badge/Status-Documented-success" alt="Documented">

</p>

 

<p align="center">

  <b>Hands-on AWS Cloud Application Development</b><br>

  <sub>Compute • Identity • Storage • Serverless APIs • Resilience</sub>

</p>

 

---

 

## 📌 About

 

This repository contains practical work completed for the **Cloud Application Development Lab** using **Amazon Web Services (AWS)**. Each experiment has its own `README.md` and screenshot evidence.

 

## 🎯 Experiments

 

| # | Experiment | AWS Service | Focus | Status |

|---|---|---|---|---|

| 01 | [Introduction to Amazon EC2](./experiment-1/README.md) | EC2 | Virtual machines, AMIs, Security Groups, SSH | ✅ |

| 02 | [Introduction to AWS IAM](./experiment-2/README.md) | IAM | Users, policies, permissions, least privilege | ✅ |

| 03 | [Creating Buckets and Managing Objects](./experiment-3/README.md) | S3 | Buckets, objects, access and security | ✅ |

| 04 | [EC2 — GCE to AWS Adaptation](./experiment-4/README.md) | EC2 | Cloud compute using AWS as the GCE alternative | ✅ |

| 05 | [Multi-Region S3 Backup](./experiment-5/README.md) | S3 | Versioning, Cross-Region Replication, Batch Replication | ✅ |

| 06 | [Serverless NoSQL Database](./experiment-6/README.md) | DynamoDB | Keys, CRUD, Query vs Scan, GSI | ✅ |

| 07 | [Introduction to Amazon API Gateway](./experiment-7/README.md) | API Gateway + Lambda | REST API, GET/POST, API key, CloudWatch | ⚠️ Handler verification needed |

 

## 📂 Repository Structure

 

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

 

## 🧭 Learning Path

 

```text

EC2 Compute → IAM Security → S3 Storage → EC2 Platform Adaptation

           → Multi-Region Resilience → DynamoDB → API Gateway + Lambda

```

 

## 🌐 Experiment 7 — Amazon API Gateway

 

- **Region:** Mumbai (`ap-south-1`)

- **REST API:** `CAD-Experiment-7-REST-API`

- **API ID:** `6pnwbvfcy6`

- **Lambda:** `cad-exp7-student-api`

- **Resource:** `/students`

- **Methods:** `GET`, `POST`

- **Stage:** `dev`

- **Usage plan:** `CAD-Experiment-7-Usage-Plan`

- **Invoke URL:** `https://6pnwbvfcy6.execute-api.ap-south-1.amazonaws.com/dev/students`

 

The API methods use Lambda proxy integration. API-key-based access was configured through a usage plan, and CloudWatch logs were inspected.

 

**Testing note:** Requests without the required API key returned HTTP `403`. Requests with the key reached Lambda, but the final response remained `Hello from Lambda!`; the intended student-specific GET/POST behavior was not verified. Check the Lambda handler configuration before reporting the student API logic as functional.

 

## 🛡️ Security & Cleanup

 

- Use least-privilege IAM permissions and keep API keys private.

- Review CloudWatch logs when troubleshooting.

- Delete only lab resources that are no longer needed, including dedicated APIs, Lambda functions, usage plans, keys, and log groups.

- Do not delete shared IAM roles or resources used by other projects.

 

## 📚 Documentation

 

- [Amazon EC2](https://docs.aws.amazon.com/ec2/)

- [AWS IAM](https://docs.aws.amazon.com/iam/)

- [Amazon S3](https://docs.aws.amazon.com/s3/)

- [Amazon DynamoDB](https://docs.aws.amazon.com/dynamodb/)

- [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/)

- [AWS Lambda](https://docs.aws.amazon.com/lambda/)

- [Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/)

 

## 👨‍💻 Author

 

**Nitanshu Tak**  

B.Tech — Computer Science Engineering  

Cloud Computing & Virtualization Technology

 

<p align="center">

  <b>☁️ Cloud Application Development Lab</b><br>

  <sub>Learn → Build → Secure → Verify → Document</sub>

</p>
