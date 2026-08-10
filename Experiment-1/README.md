# Experiment 01 — Deploy a Static Web Application using Amazon S3 and Amazon CloudFront

## 📌 Experiment Information

| Field | Details |
|---|---|
| **Experiment No.** | 01 |
| **Subject** | Cloud Application Development |
| **Experiment Title** | Deploy a Static Web Application using Amazon S3 and Amazon CloudFront |
| **Cloud Platform** | Amazon Web Services (AWS) |
| **AWS Services** | Amazon S3, Amazon CloudFront |
| **AWS Region** | Asia Pacific (Mumbai) — `ap-south-1` |
| **Student** | Nitanshu Tak |
| **Deployment Type** | Static Web Application |
| **CloudFront Distribution** | `nitanshu-cloud-development-lab-1` |
| **S3 Bucket** | `nitanshu-cloud-development-lab-1` |
| **Default Root Object** | `index.html` |
| **CloudFront Domain** | `dk81xb1bby19.cloudfront.net` |

---

## 🎯 Aim

To deploy a static web application on Amazon Web Services (AWS) by storing the website files in a private Amazon S3 bucket and delivering the application through Amazon CloudFront using a secure and scalable cloud architecture.

---

## 📝 Overview

This experiment demonstrates the deployment of a static web application using two AWS managed services:

- **Amazon S3** — used to store the static website files.
- **Amazon CloudFront** — used as the Content Delivery Network (CDN) that delivers the website to users over HTTPS.

The website consists of a static `index.html` file. The file is uploaded to an S3 bucket, while the S3 bucket remains private. CloudFront is configured to use the S3 bucket as its origin and is granted permission to retrieve objects from the private bucket.

The final architecture is:

```text
                         🌍 USER / BROWSER
                                |
                                | HTTPS Request
                                v
                    +------------------------+
                    |    AMAZON CLOUDFRONT   |
                    |  CDN + HTTPS + CACHE   |
                    +-----------+------------+
                                |
                                | Secure Origin Access
                                v
                    +------------------------+
                    |       AMAZON S3         |
                    |     PRIVATE BUCKET      |
                    +-----------+------------+
                                |
                                v
                           index.html
```

The user accesses the CloudFront URL instead of directly accessing the S3 storage origin.

---

## 🎯 Objectives

1. Understand the concept of static web application deployment in the cloud.
2. Create and configure an Amazon S3 bucket.
3. Upload a static HTML file to Amazon S3.
4. Keep the S3 bucket private instead of exposing it publicly.
5. Create an Amazon CloudFront distribution.
6. Configure Amazon S3 as the CloudFront origin.
7. Enable private S3 bucket access for CloudFront.
8. Use AWS recommended origin and cache settings.
9. Configure `index.html` as the CloudFront default root object.
10. Understand CDN caching and edge delivery.
11. Access the deployed application through an HTTPS CloudFront URL.
12. Understand the security and scalability advantages of the S3 + CloudFront architecture.

---

## 🧠 Background Theory

### Amazon S3

Amazon Simple Storage Service (Amazon S3) is an object storage service provided by AWS. Data is stored as objects inside buckets.

For a static website, files such as:

- HTML
- CSS
- JavaScript
- Images
- Fonts
- Videos
- Static JSON files

can be stored as S3 objects.

In this experiment, the primary website object is:

```text
index.html
```

The S3 bucket used for this experiment is:

```text
nitanshu-cloud-development-lab-1
```

The bucket was created in:

```text
Asia Pacific (Mumbai)
ap-south-1
```

The bucket was kept private by retaining the S3 Block Public Access configuration.

---

### Amazon CloudFront

Amazon CloudFront is AWS's Content Delivery Network (CDN).

CloudFront receives requests from users and delivers content through its distributed network of edge locations.

Instead of every request travelling directly to the S3 origin, CloudFront can cache frequently requested objects.

A simplified request flow is:

```text
User
 |
 v
CloudFront
 |
 +---- Cache Hit ----> Return cached object
 |
 +---- Cache Miss ---> Request object from S3
                         |
                         v
                      index.html
```

This can reduce latency, decrease repeated origin requests, and improve the scalability of the application.

---

## 🔐 Private S3 + CloudFront Architecture

A major security decision in this experiment is that the S3 bucket is **not made publicly accessible**.

Instead:

```text
Internet
   |
   v
CloudFront
   |
   | Authorized access
   v
Private S3 Bucket
```

The CloudFront console option:

```text
Allow private S3 bucket access to CloudFront
```

was enabled.

This allows CloudFront to retrieve content from the S3 origin while the bucket itself remains private.

This is preferable to unnecessarily exposing the storage origin directly to the internet.

---

## ⚡ CloudFront Caching

CloudFront uses caching to improve content delivery.

### Cache Hit

A cache hit occurs when CloudFront already has the requested object available in its cache.

```text
User
 |
 v
CloudFront
 |
 v
Cached index.html
 |
 v
User
```

The origin does not need to be contacted for that request.

### Cache Miss

A cache miss occurs when the requested object is not currently available in the relevant CloudFront cache.

```text
User
 |
 v
CloudFront
 |
 v
S3 Origin
 |
 v
index.html
 |
 v
CloudFront
 |
 v
User
```

CloudFront can then cache the object for subsequent requests according to the configured caching behavior.

---

## 🔒 HTTPS

The website is accessed through the CloudFront HTTPS endpoint:

```text
https://dk81xb1bby19.cloudfront.net
```

HTTPS provides encrypted communication between the browser and CloudFront.

For this experiment, a custom domain was not required. The CloudFront-generated `cloudfront.net` domain was sufficient to demonstrate secure web delivery.

---

# 🛠️ Technologies and Services Used

| Technology / Service | Purpose |
|---|---|
| HTML5 | Static website content |
| Amazon S3 | Storage for website files |
| Amazon CloudFront | CDN and content delivery |
| HTTPS | Secure communication |
| AWS Management Console | Cloud resource configuration |

---

# 📁 Project Structure

```text
Experiment-01/
│
├── README.md
│
├── website/
│   └── index.html
│
└── screenshots/
    ├── 01-s3-bucket-created.png
    ├── 02-index-html-uploaded.png
    ├── 03-cloudfront-origin.png
    ├── 04-cloudfront-cache-settings.png
    ├── 05-cloudfront-security.png
    ├── 06-cloudfront-review.png
    ├── 07-cloudfront-created.png
    ├── 08-default-root-object.png
    └── 09-final-deployed-website.png
```

---

# 🌐 Website Source Code

The static webpage used in this experiment is:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My AWS Cloud Website</title>
</head>

<body>
    <h1>Hello from AWS! 🚀</h1>

    <h2>Cloud Application Development Lab</h2>

    <p>This website is deployed using Amazon S3 and CloudFront.</p>

    <p>Created by Nitanshu</p>
</body>
</html>
```

---

# 🚀 Procedure

## Step 1 — Prepare the Static Website

Create a file named:

```text
index.html
```

Add the static HTML content to the file.

Open the file locally in a browser and verify that the webpage renders correctly.

---

## Step 2 — Open Amazon S3

1. Sign in to the AWS Management Console.
2. Use the AWS service search bar.
3. Search for **S3**.
4. Open **Amazon S3**.
5. Select **Create bucket**.

---

## Step 3 — Create the S3 Bucket

Configure the bucket as follows:

```text
Region:
Asia Pacific (Mumbai) — ap-south-1

Bucket Name:
nitanshu-cloud-development-lab-1
```

Keep:

```text
Object Ownership:
ACLs disabled
```

Keep:

```text
Block Public Access:
Enabled
```

Bucket versioning is not required for this experiment.

Retain the default encryption configuration.

Finally, select:

```text
Create bucket
```

---

## Step 4 — Upload the Website

1. Open the newly created S3 bucket.
2. Open the **Objects** section.
3. Select **Upload**.
4. Select **Add files**.
5. Choose:

```text
index.html
```

6. Select **Upload**.
7. Confirm that `index.html` appears in the bucket.

The final object structure is:

```text
S3 Bucket
└── index.html
```

---

## Step 5 — Open Amazon CloudFront

1. Use the AWS Console search bar.
2. Search for **CloudFront**.
3. Open **Amazon CloudFront**.
4. Select **Distributions**.
5. Select **Create distribution**.

Keep the distribution type as:

```text
Single website or app
```

---

## Step 6 — Configure the CloudFront Distribution

Use the following distribution name:

```text
nitanshu-cloud-development-lab-1
```

A custom Route 53 managed domain is not required.

Leave the Route 53 domain field empty.

---

## Step 7 — Configure the S3 Origin

Select the S3 bucket:

```text
nitanshu-cloud-development-lab-1
```

The origin domain should correspond to the S3 bucket:

```text
nitanshu-cloud-development-lab-1.s3.ap-south-1.amazonaws.com
```

Leave the origin path empty.

Enable:

```text
Allow private S3 bucket access to CloudFront
```

Keep:

```text
Use recommended origin settings
```

selected.

---

## Step 8 — Configure Cache Settings

Keep:

```text
Use recommended cache settings tailored to serving S3 content
```

selected.

No custom cache configuration is required for this introductory experiment.

---

## Step 9 — Configure Security

Open the CloudFront security configuration.

For this experiment, no additional custom WAF configuration is required.

Retain the default security configuration provided by the selected CloudFront plan.

---

## Step 10 — Review the Distribution

Before creation, verify:

```text
Distribution Type:
Single website or app

Origin:
Amazon S3

S3 Origin:
nitanshu-cloud-development-lab-1

Private S3 Access:
Enabled

Origin Path:
None

Cache Settings:
Recommended S3 settings
```

Then select:

```text
Create distribution
```

---

## Step 11 — Wait for CloudFront Deployment

After creation, CloudFront initially shows a deployment state such as:

```text
Deploying
```

CloudFront requires time to propagate the distribution configuration.

Wait until the distribution is fully deployed and available.

---

## Step 12 — Configure the Default Root Object

Open the CloudFront distribution.

Go to:

```text
General → Settings → Edit
```

Find:

```text
Default root object
```

Enter:

```text
index.html
```

Save the settings.

The configuration should display:

```text
Default root object:
index.html
```

This allows:

```text
https://dk81xb1bby19.cloudfront.net
```

to automatically serve:

```text
index.html
```

---

## Step 13 — Obtain the CloudFront URL

From the CloudFront distribution details, locate:

```text
Distribution domain name
```

The domain generated for this experiment is:

```text
dk81xb1bby19.cloudfront.net
```

The final website URL is:

```text
https://dk81xb1bby19.cloudfront.net
```

---

## Step 14 — Verify the Deployment

Open the CloudFront URL in a browser:

```text
https://dk81xb1bby19.cloudfront.net
```

The webpage should display:

```text
Hello from AWS! 🚀

Cloud Application Development Lab

This website is deployed using Amazon S3 and CloudFront.

Created by Nitanshu
```

The browser address bar should show the CloudFront HTTPS domain.

---

# 🧩 Complete Architecture Flow

```text
                         INTERNET
                            |
                            v
                     USER / BROWSER
                            |
                            | HTTPS
                            v
              +---------------------------+
              |      AMAZON CLOUDFRONT    |
              |                           |
              |  CDN                      |
              |  HTTPS                    |
              |  Caching                  |
              |  Edge Delivery            |
              +-------------+-------------+
                            |
                            | Secure Origin Access
                            v
              +---------------------------+
              |        AMAZON S3          |
              |                           |
              |      Private Bucket       |
              |                           |
              |       index.html          |
              +---------------------------+
```

---

# 🔄 Request Processing Flow

```text
1. User opens CloudFront URL
              |
              v
2. CloudFront receives HTTPS request
              |
              v
3. CloudFront identifies requested object
              |
              v
4. Root request maps to index.html
              |
              v
5. CloudFront checks its cache
              |
       +------+------+
       |             |
       v             v
  Cache Hit      Cache Miss
       |             |
       |             v
       |       Request from S3
       |             |
       |             v
       |        Receive index.html
       |             |
       +------+------+
              |
              v
6. CloudFront returns content
              |
              v
7. Browser renders webpage
```

---

# 📊 Configuration Summary

| Configuration | Value |
|---|---|
| S3 Bucket | `nitanshu-cloud-development-lab-1` |
| Region | `ap-south-1` |
| Website Object | `index.html` |
| Public S3 Access | Blocked |
| CloudFront Distribution | `nitanshu-cloud-development-lab-1` |
| Origin | Amazon S3 |
| Origin Path | None |
| Private S3 Access | Enabled |
| Origin Settings | Recommended |
| Cache Settings | Recommended S3 settings |
| Default Root Object | `index.html` |
| Protocol | HTTPS |
| CloudFront Domain | `dk81xb1bby19.cloudfront.net` |

---

# 🔐 Security Configuration

The experiment follows a private-origin architecture.

### S3

```text
Block Public Access:
Enabled
```

The S3 bucket is not intentionally exposed as a public storage endpoint.

### CloudFront

CloudFront is the public-facing delivery layer.

```text
Internet
   ↓
CloudFront
   ↓
Private S3
```

This provides a cleaner separation between the public application endpoint and the storage origin.

---

# ⚡ Performance Characteristics

CloudFront improves static content delivery through caching.

Without a CDN:

```text
User → S3
User → S3
User → S3
User → S3
```

With CloudFront:

```text
                 +--> Cache Hit
                 |
User → CloudFront
                 |
                 +--> Cache Miss → S3
```

Once an object is available in a CloudFront cache, subsequent requests can potentially be served without another origin request.

Benefits include:

- Lower latency
- Reduced origin traffic
- Improved scalability
- Better global content delivery
- Efficient distribution of static assets

---

# 🧪 Testing

| Test ID | Test Case | Expected Result | Status |
|---|---|---|---|
| TC-01 | Create S3 bucket | Bucket created successfully | ✅ Pass |
| TC-02 | Upload index.html | Object visible in S3 | ✅ Pass |
| TC-03 | Create CloudFront distribution | Distribution created | ✅ Pass |
| TC-04 | Configure S3 origin | Correct S3 bucket selected | ✅ Pass |
| TC-05 | Enable private S3 access | CloudFront can access private origin | ✅ Pass |
| TC-06 | Configure root object | `index.html` configured | ✅ Pass |
| TC-07 | Deploy distribution | Distribution becomes available | ✅ Pass |
| TC-08 | Open CloudFront URL | Website loads successfully | ✅ Pass |

---

# 👀 Observations

1. The S3 bucket was successfully created in the Mumbai region.
2. The static HTML file was successfully uploaded to S3.
3. S3 public access was kept blocked.
4. CloudFront successfully accepted the S3 bucket as its origin.
5. Private S3 access to CloudFront was enabled.
6. Recommended origin settings were used.
7. Recommended cache settings for S3 content were used.
8. CloudFront successfully created the distribution.
9. The distribution initially required time to deploy.
10. `index.html` was configured as the default root object.
11. The CloudFront distribution generated a `cloudfront.net` domain.
12. The final webpage was accessed using HTTPS through CloudFront.

---

# 📸 Screenshots

Screenshots captured during the experiment should be stored in:

```text
screenshots/
```

Recommended evidence:

### Screenshot 01 — S3 Bucket Created

![S3 Bucket Created](screenshots/01-s3-bucket-created.png)

Shows the successful creation of the S3 bucket.

---

### Screenshot 02 — index.html Uploaded

![index.html Uploaded](screenshots/02-index-html-uploaded.png)

Shows `index.html` inside the S3 bucket.

---

### Screenshot 03 — CloudFront Origin

![CloudFront Origin](screenshots/03-cloudfront-origin.png)

Shows the S3 bucket configured as the CloudFront origin and private S3 access enabled.

---

### Screenshot 04 — CloudFront Cache Settings

![CloudFront Cache Settings](screenshots/04-cloudfront-cache-settings.png)

Shows the recommended cache configuration for S3 content.

---

### Screenshot 05 — CloudFront Security

![CloudFront Security](screenshots/05-cloudfront-security.png)

Shows the CloudFront security configuration.

---

### Screenshot 06 — CloudFront Review

![CloudFront Review](screenshots/06-cloudfront-review.png)

Shows the reviewed CloudFront configuration before distribution creation.

---

### Screenshot 07 — CloudFront Distribution Created

![CloudFront Distribution](screenshots/07-cloudfront-created.png)

Shows the successfully created CloudFront distribution and its domain name.

---

### Screenshot 08 — Default Root Object

![Default Root Object](screenshots/08-default-root-object.png)

Shows `index.html` configured as the default root object.

---

### Screenshot 09 — Final Deployed Website

![Final Website](screenshots/09-final-deployed-website.png)

Shows the final static webpage loaded through the CloudFront HTTPS URL.

---

# ❓ Viva Questions and Answers

### 1. What is Amazon S3?

Amazon S3 is an object storage service used to store and retrieve files as objects inside buckets.

### 2. Why is S3 suitable for static websites?

Static websites consist of files such as HTML, CSS, JavaScript, images, and other static assets that can be stored as S3 objects.

### 3. What is Amazon CloudFront?

Amazon CloudFront is AWS's Content Delivery Network used to deliver content through a distributed network of edge locations.

### 4. Why is CloudFront used with S3?

S3 provides storage while CloudFront provides caching, global content delivery, and HTTPS access.

### 5. What is an origin?

An origin is the backend source from which CloudFront retrieves content. In this experiment, the origin is the S3 bucket.

### 6. What is a cache hit?

A cache hit occurs when CloudFront already has the requested object available in its cache.

### 7. What is a cache miss?

A cache miss occurs when CloudFront does not have the requested object in its cache and must retrieve it from the origin.

### 8. Why was the S3 bucket kept private?

The bucket was kept private to avoid unnecessarily exposing the storage origin and to make CloudFront the controlled public delivery layer.

### 9. What is the default root object?

The default root object is the file CloudFront returns when the distribution root URL is requested. In this experiment it is `index.html`.

### 10. Why was `index.html` configured as the default root object?

It allows users to open the CloudFront root URL without explicitly typing `/index.html`.

### 11. What is an edge location?

An edge location is a CloudFront delivery location where content can be cached and served closer to users.

### 12. What is the difference between S3 and CloudFront?

S3 is used for storage, while CloudFront is used for content delivery and caching.

### 13. Why is HTTPS important?

HTTPS encrypts communication between the browser and the CloudFront endpoint.

### 14. Can S3 execute backend code?

No. S3 is object storage and does not execute traditional server-side application logic.

### 15. Can this architecture host a dynamic application?

The static frontend can be delivered this way, but dynamic backend functionality requires additional services such as Lambda, API Gateway, EC2, containers, or another backend platform.

### 16. What happens during a CloudFront cache miss?

CloudFront retrieves the requested object from the configured origin and then returns it to the viewer.

### 17. Why is a CDN useful?

A CDN can reduce latency, improve content delivery performance, reduce repeated origin requests, and improve scalability.

### 18. Why was Route 53 not used?

A custom domain was not required. The CloudFront-generated domain was sufficient for this experiment.

### 19. What is the overall architecture?

```text
Browser → CloudFront → Private S3 Origin → index.html
```

### 20. What is the main advantage of this architecture?

It separates storage from content delivery while providing scalable, cached, and HTTPS-based access to static content.

---

# 📚 Learning Outcomes

After completing this experiment, the following concepts were understood:

- Static website deployment
- Amazon S3 object storage
- S3 buckets and objects
- S3 public-access controls
- Amazon CloudFront
- CloudFront origins
- CDN edge locations
- Cache hits and cache misses
- CloudFront caching
- HTTPS delivery
- Private S3 origin architecture
- CloudFront-to-S3 access
- Default root objects
- AWS Management Console
- Cloud-based static application deployment

---

# ✅ Result

The static web application was successfully deployed using Amazon S3 and Amazon CloudFront.

The website file:

```text
index.html
```

was stored in the private S3 bucket:

```text
nitanshu-cloud-development-lab-1
```

The S3 bucket was configured as the CloudFront origin, private S3 access was enabled, recommended cache settings were used, and `index.html` was configured as the default root object.

The final application was made available through:

```text
https://dk81xb1bby19.cloudfront.net
```

Therefore, the experiment successfully demonstrated the deployment and delivery of a static web application using Amazon S3 and Amazon CloudFront.

---

# 🏁 Conclusion

This experiment demonstrated a complete cloud-based static web deployment using Amazon S3 and Amazon CloudFront.

Amazon S3 provided the storage layer for the static website, while CloudFront provided the public delivery layer, caching, and HTTPS access. Keeping the S3 bucket private and allowing CloudFront to access it provided a more secure architecture than directly exposing the storage bucket.

The experiment also demonstrated how a CDN can reduce repeated origin requests through caching and deliver content efficiently to users. Configuring `index.html` as the default root object allowed the CloudFront distribution to behave like a normal website when its root URL was opened.

The final result was a successfully deployed static website accessible through an HTTPS CloudFront domain.

---

## 🔗 Deployment URL

```text
https://dk81xb1bby19.cloudfront.net
```

---

## 👨‍💻 Author

**Nitanshu Tak**

Cloud Application Development Lab — Experiment 01
