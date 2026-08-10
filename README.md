# Cloud Application Development Lab

This repository contains the laboratory experiments performed for the **Cloud Application Development** course using **Amazon Web Services (AWS)**.

## 📂 Repository Structure

```text
Cloud-Application-Development-Lab/
│
├── README.md
│
├── Experiment-01/
│   ├── README.md
│   ├── website/
│   │   └── index.html
│   └── screenshots/


Each experiment has its own directory containing its documentation, source files, and practical screenshots.

---

## 🧪 Experiments

### Experiment 01 — Static Web Application using Amazon S3 and CloudFront

**Objective:**  
Deploy a static web application using Amazon S3 for storage and Amazon CloudFront for secure and efficient content delivery.

**AWS Services Used:**
- Amazon S3
- Amazon CloudFront

**Implementation:**

```text
User / Browser
      |
      v
Amazon CloudFront
      |
      v
Private Amazon S3
      |
      v
index.html
```

The static website was uploaded to the S3 bucket:

```text
nitanshu-cloud-development-lab-1
```

The bucket was kept private, and CloudFront was configured to access it as the origin. `index.html` was configured as the default root object.

**Final Deployment:**

```text
https://dk81xb1bby19.cloudfront.net
```

Complete documentation and implementation details are available in:

```text
Experiment-01/README.md
```

---

## ☁️ Platform

**Cloud Platform:** Amazon Web Services (AWS)

Additional experiments will be added to the repository as the laboratory progresses.

---

## 👨‍💻 Author

**Nitanshu Tak**

B.Tech CSE — Cloud Computing & Virtualization Technology
