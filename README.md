# ☁️ AWS Cloud Development Lab


> A practical collection of AWS cloud experiments covering core cloud infrastructure and services.


![AWS](https://img.shields.io/badge/AWS-Cloud%20Development-orange?logo=amazonaws)


---


## 📌 About


This repository contains the practical experiments performed as part of the **Cloud Development Lab**.


Each experiment focuses on understanding and implementing an AWS cloud service through the AWS Management Console and, where required, command-line tools.


The repository is organized experiment-wise so that each lab can be accessed and documented independently.


---


## 🧪 Experiments


| Experiment | Topic | Status |

|---|---|---|

| **Experiment 1** | Amazon S3 + CloudFront — Static Website Delivery | ✅ Completed |

| **Experiment 2** | Introduction to Amazon EC2 | ✅ Completed |


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

└── README.md

```


---


## ☁️ Experiment 1 — S3 + CloudFront


**Topic:** Static website hosting and content delivery using Amazon S3 and Amazon CloudFront.


### Key Work


- Created an S3 bucket for website content.

- Configured CloudFront with the S3 bucket as the origin.

- Enabled private S3 access through CloudFront.

- Configured the default root object as `index.html`.

- Created and deployed a CloudFront distribution.

- Verified the CloudFront distribution and deployment.


📁 Detailed documentation is available in [`experiment-1/README.md`](experiment-1/README.md).


---


## 🖥️ Experiment 2 — Introduction to EC2


**Topic:** Launching and accessing a cloud-based virtual machine using Amazon EC2.


### Key Work


- Launched a free-tier eligible `t3.micro` EC2 instance.

- Used Amazon Linux 2023.

- Configured a Security Group for SSH access.

- Connected using EC2 Instance Connect.

- Inspected CPU, memory, storage, OS, hostname, and network information using Linux commands.


📁 Detailed documentation is available in [`experiment-2/README.md`](experiment-2/README.md).


---


## 🛠️ Technologies & Services


- **Amazon Web Services (AWS)**

- Amazon S3

- Amazon CloudFront

- Amazon EC2

- EC2 Instance Connect

- Security Groups

- Amazon Linux

- Linux command line


---


## 🎯 Purpose


The main objective of this repository is to build practical understanding of AWS infrastructure by **creating, configuring, accessing, and validating cloud resources** rather than only studying the concepts theoretically.


---


## 👨‍💻 Author


**Nitanshu Tak**  

B.Tech — Computer Science Engineering  

Cloud Computing & Virtualization Technology


---


> 🚀 **Cloud Development Lab — Learn → Build → Deploy → Verify**
