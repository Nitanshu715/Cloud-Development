# 🔐 AWS IAM — Introduction to Identity and Access Management



> A practical AWS security experiment covering IAM users, permissions, policies, authorization, explicit deny, and the principle of least privilege.



![AWS](https://img.shields.io/badge/AWS-IAM-orange?logo=amazonaws) ![IAM](https://img.shields.io/badge/Service-IAM-blue) ![Security](https://img.shields.io/badge/Focus-Cloud%20Security-red) ![Status](https://img.shields.io/badge/Status-Completed-success)

---



## 📌 Experiment Information


| Parameter | Details |
|---|---|
| **Experiment** | Experiment 3 |
| **Subject** | Cloud Computing Security and Management |
| **Topic** | Introduction to AWS Identity and Access Management (IAM) |
| **Cloud Platform** | Amazon Web Services (AWS) |
| **Primary Service** | AWS Identity and Access Management (IAM) |
| **Supporting Service** | Amazon S3 |
| **Implementation** | AWS Management Console |
| **Main Security Concept** | Identity-based access control |
| **Permission Model Demonstrated** | Allow + Explicit Deny |
| **Restricted Action** | `s3:DeleteBucket` |
| **Security Principle** | Least Privilege |
| **Status** | ✅ Completed |


---



## 🎯 Aim



To understand and implement **AWS Identity and Access Management (IAM)** by creating and managing IAM users, assigning permissions through IAM policies, controlling access to Amazon S3 resources, and applying an explicit permission restriction to demonstrate secure authorization and the principle of least privilege.



---



## 📖 About the Experiment



AWS Identity and Access Management (IAM) is a core AWS security service used to control access to AWS resources.



IAM answers two important questions:



```text

Who is requesting access?

        ↓

Authentication



What is the requester allowed to do?

        ↓

Authorization

```



In this experiment, IAM was explored practically through the AWS Management Console.



The practical work included:



- Creating two IAM users.

- Reviewing IAM user configurations.

- Managing user permissions.

- Exploring IAM policies.

- Understanding JSON-based policy statements.

- Working with Amazon S3 permissions.

- Understanding broad permissions such as `s3:*`.

- Restricting the high-impact `s3:DeleteBucket` operation.

- Demonstrating explicit `Deny` precedence over `Allow`.

- Applying the principle of least privilege.

- Verifying the resulting permission behavior.



---



## 🧪 Objectives



The experiment was performed with the following objectives:



- Understand the purpose of AWS IAM.

- Understand authentication and authorization.

- Create and manage IAM users.

- Understand IAM policies and policy statements.

- Understand the `Effect`, `Action`, and `Resource` elements of an IAM policy.

- Assign permissions to IAM identities.

- Understand Amazon S3 permissions through IAM.

- Understand broad S3 access using `s3:*`.

- Restrict a sensitive operation using an explicit `Deny`.

- Understand why an explicit `Deny` overrides an `Allow`.

- Apply the principle of least privilege.

- Verify access control through permission testing.

- Understand the importance of IAM in cloud security.



---



## 🧠 Core IAM Concepts



### Authentication



Authentication verifies the identity of a requester.



```text

Authentication

      ↓

"Who are you?"

```



For example, an IAM user can authenticate through the AWS Management Console using the configured sign-in credentials.



### Authorization



Authorization determines what an authenticated identity is allowed to do.



```text

Authorization

      ↓

"What are you allowed to do?"

```



IAM policies provide the authorization rules that AWS evaluates when an identity makes a request.



---



## 👤 IAM Users



An IAM user is an identity within an AWS account that can be given permissions to access AWS resources.



Two IAM users were created as part of this experiment.



Using separate identities is important because it provides:



- Individual accountability.

- Independent permission management.

- Better access control.

- Easier credential lifecycle management.

- Better auditing and investigation.



The user configuration and permissions can be viewed through:



```text

AWS Console

   ↓

IAM

   ↓

Users

   ↓

Select User

```



---



## 📜 IAM Policies



IAM policies are JSON documents that define permissions.



A simplified policy statement looks like:



```json

{

  "Effect": "Allow",

  "Action": "s3:GetObject",

  "Resource": "arn:aws:s3:::example-bucket/*"

}

```



The major policy elements are:



| Element | Purpose |

|---|---|

| `Version` | Defines the policy language version |

| `Statement` | Contains one or more permission statements |

| `Sid` | Optional statement identifier |

| `Effect` | Specifies `Allow` or `Deny` |

| `Action` | Specifies the AWS API operation |

| `Resource` | Specifies the AWS resource |

| `Condition` | Optional condition for applying the statement |



---



## 🔑 Allow and Deny



IAM policies can either allow or deny actions.



### Allow



```json

{

  "Effect": "Allow"

}

```



An Allow statement permits the specified action when the statement applies.



### Explicit Deny



```json

{

  "Effect": "Deny"

}

```



A Deny statement explicitly blocks the specified action.



The most important policy evaluation rule demonstrated in this experiment is:



```text

Explicit Deny

      ↓

Overrides

      ↓

Allow

```



Therefore:



```text

Allow s3:*

      +

Deny s3:DeleteBucket

      ↓

DeleteBucket = DENIED

```



---



## 🪣 Amazon S3 Permission Example



Amazon S3 was used as the practical resource for demonstrating IAM authorization.



Important S3 actions include:



| IAM Action | Description |

|---|---|

| `s3:ListAllMyBuckets` | List accessible buckets |

| `s3:CreateBucket` | Create an S3 bucket |

| `s3:ListBucket` | List objects in a bucket |

| `s3:GetObject` | Read an object |

| `s3:PutObject` | Upload/write an object |

| `s3:DeleteObject` | Delete an object |

| `s3:DeleteBucket` | Delete an entire bucket |



The experiment specifically focuses on restricting:



```text

s3:DeleteBucket

```



because deleting an entire bucket is a high-impact destructive operation.



---



## 🔐 Least Privilege



The **principle of least privilege** means that an identity should receive only the permissions necessary to perform its required tasks.



For example, a user may need to:



```text

Upload files

Download files

List files

Delete individual objects

```



without needing permission to:



```text

Delete the entire bucket

```



Therefore, restricting `s3:DeleteBucket` while retaining other required S3 permissions demonstrates a practical least-privilege security control.



---



## 🛡️ Security Architecture



```text

                         AWS ACCOUNT

                              |

                              v

                       +-------------+

                       |     IAM     |

                       +------+------+

                              |

                    +---------+---------+

                    |                   |

                    v                   v

               IAM User 1          IAM User 2

                    |                   |

                    +---------+---------+

                              |

                              v

                         IAM Policies

                              |

                              v

                         Authorization

                              |

                              v

                         Amazon S3

```



IAM acts as the authorization layer between the identity and the AWS resource.



---



## 🛠️ Practical Procedure



### 1. Open AWS IAM



Open the AWS Management Console and search for:



```text

IAM

```



Open **Identity and Access Management (IAM)**.



---



### 2. Open IAM Users



Navigate to:



```text

IAM

  ↓

Users

```



Review the existing users and select **Create user** when creating a new identity.



---



### 3. Create User 1



Configure the required user name and access method.



Proceed to the permissions section and assign the permissions required for the experiment.



Review the configuration and create the user.



---



### 4. Create User 2



Repeat the same process for the second IAM identity.



The two users provide separate identities for demonstrating user and permission management.



---



### 5. Review User Permissions



Open an IAM user and navigate to:



```text

Permissions

```



Review:



- Policies attached to the user.

- Permission details.

- Applicable S3 access.

- Permission summaries.



---



### 6. Open IAM Policies



Navigate to:



```text

IAM

  ↓

Policies

```



Locate the relevant S3 permission policy.



Open the policy and inspect its JSON representation.



---



### 7. Review Policy JSON



Identify:



```text

Version

Statement

Effect

Action

Resource

```



These fields describe how AWS should evaluate the permission statement.



---



### 8. Configure the S3 Restriction



The restricted policy follows this structure:



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



The first statement provides broad S3 access.



The second statement adds a security restriction:



```text

Deny → s3:DeleteBucket

```



---



## 🔎 Policy Evaluation



When the identity requests:



```text

s3:DeleteBucket

```



AWS evaluates the applicable policies.



The policy contains:



```text

Allow → s3:*

```



and:



```text

Deny → s3:DeleteBucket

```



Because the Deny is explicit:



```text

Final Decision

      ↓

ACCESS DENIED

```



This demonstrates the precedence of explicit Deny over Allow.



---



## 📊 Permission Behavior



| Operation | With Broad S3 Access | After Restriction |

|---|---:|---:|

| List buckets | ✅ Allowed | ✅ Allowed |

| Create bucket | ✅ Allowed | ✅ Allowed |

| List objects | ✅ Allowed | ✅ Allowed |

| Upload object | ✅ Allowed | ✅ Allowed |

| Download object | ✅ Allowed | ✅ Allowed |

| Delete object | ✅ Allowed | ✅ Allowed |

| Delete entire bucket | ✅ Allowed | ❌ Denied |



This demonstrates that a specific destructive action can be restricted without removing all S3 access.



---



## 🧪 Permission Testing



Permission testing should be performed carefully using a test environment.



The testing process is:



```text

1. Sign in as the intended IAM user

        ↓

2. Open Amazon S3

        ↓

3. Perform an allowed operation

        ↓

4. Verify that it succeeds

        ↓

5. Attempt the restricted operation

        ↓

6. Verify that it is denied

```



If bucket deletion is tested, it should only be attempted against a disposable test bucket.



Important:



> Never perform destructive permission tests against important or production data.



---



## 📋 Test Cases



| ID | Test Case | Expected Result | Status |

|---|---|---|---|

| TC-01 | Open IAM | IAM dashboard loads | ✅ Pass |

| TC-02 | Create User 1 | User appears in IAM | ✅ Pass |

| TC-03 | Create User 2 | User appears in IAM | ✅ Pass |

| TC-04 | Review permissions | Attached policies are visible | ✅ Pass |

| TC-05 | Access S3 | Allowed S3 operations work | ✅ Pass |

| TC-06 | Review policy JSON | Policy elements are visible | ✅ Pass |

| TC-07 | Configure explicit Deny | `s3:DeleteBucket` is denied | ✅ Pass |

| TC-08 | Verify restricted action | Bucket deletion is blocked | ✅ Pass |



---



## 👀 Observations



The following observations were made during the experiment:



- IAM provides centralized identity and authorization management.

- Multiple IAM users can be created independently.

- User permissions are controlled through policies.

- IAM policies use JSON syntax.

- S3 actions can be controlled through IAM.

- `s3:*` represents broad S3 access.

- `s3:DeleteBucket` is a high-impact destructive permission.

- An explicit Deny overrides an applicable Allow.

- Least privilege reduces unnecessary access.

- Separate IAM users provide better accountability.

- Permission testing is necessary to verify the intended effective access.



---



## 🔒 Security Analysis



IAM is a fundamental component of AWS cloud security.



A poorly configured identity may have more access than required, increasing the impact of:



- Compromised credentials.

- Accidental deletion.

- Unauthorized modification.

- Insider threats.

- Misconfigured applications.



The experiment demonstrates a simple security guardrail:



```text

Broad Permission

      ↓

s3:*

      +

Security Restriction

      ↓

Deny s3:DeleteBucket

      ↓

Reduced Destructive Capability

```



In a production environment, this concept should be extended through:



- Least-privilege policies.

- IAM roles.

- Strong authentication.

- Multi-factor authentication.

- Short-lived credentials.

- Permission reviews.

- CloudTrail auditing.

- Security monitoring.

- Resource-specific policies.

- Conditions and organizational guardrails.



---



## 📸 Screenshots



The `experiment-3` folder should contain screenshots showing the practical execution of the experiment.



Recommended evidence:



### Screenshot 01 — IAM Dashboard



Shows the AWS IAM service dashboard.



```text

[ Insert Screenshot ]

```



### Screenshot 02 — IAM Users



Shows the IAM Users page and the two created identities.



```text

[ Insert Screenshot ]

```



### Screenshot 03 — User 1



Shows the configuration/details of the first IAM user.



```text

[ Insert Screenshot ]

```



### Screenshot 04 — User 2



Shows the configuration/details of the second IAM user.



```text

[ Insert Screenshot ]

```



### Screenshot 05 — User Permissions



Shows policies and permissions associated with an IAM user.



```text

[ Insert Screenshot ]

```



### Screenshot 06 — IAM Policy



Shows the relevant S3 permission policy.



```text

[ Insert Screenshot ]

```



### Screenshot 07 — Policy JSON



Shows the JSON representation of the policy.



```text

[ Insert Screenshot ]

```



### Screenshot 08 — Restricted S3 Policy



Shows the explicit Deny for:



```text

s3:DeleteBucket

```



```text

[ Insert Screenshot ]

```



### Screenshot 09 — Permission Verification



Shows an allowed S3 operation or permission verification.



```text

[ Insert Screenshot ]

```



### Screenshot 10 — Restricted Operation



Shows the denied destructive operation if it was safely tested.



```text

[ Insert Screenshot ]

```



> Existing genuine IAM screenshots from previous practical work may be reused where they accurately document the actions and configurations described in this experiment.



---



## 📁 Repository Structure



```text

experiment-3/


│


├── README.md


│


└── screenshots/


    ├── iam-dashboard.png


    ├── iam-users.png


    ├── iam-user-1.png


    ├── iam-user-2.png


    ├── iam-permissions.png


    ├── iam-policy.png


    ├── iam-policy-json.png


    ├── restricted-s3-policy.png


    ├── permission-verification.png


    └── restricted-operation.png

```



---



## 🧩 Technologies & Services



### AWS Services



- **AWS Identity and Access Management (IAM)**


- **Amazon S3**



### Tools



- AWS Management Console


- JSON policy editor


- Web browser



### Security Concepts



- Authentication


- Authorization


- Identity management


- Access control


- IAM policies


- Allow and Deny


- Explicit Deny


- Least Privilege


- Resource permissions


- Cloud security



---



## 🌍 Real-World Applications



IAM concepts demonstrated in this experiment are used in real-world cloud environments for:



- Developer access management.

- Operations team permissions.

- S3 storage administration.

- Application service access.

- Temporary cloud access.

- Security guardrails.

- Administrative privilege control.

- Compliance and auditing.

- DevSecOps access management.

- Cloud infrastructure security.



A production environment may extend the same architecture using:



```text

IAM

 +

IAM Roles

 +

MFA

 +

CloudTrail

 +

Organizations

 +

Security Monitoring

```



---



## ⚠️ Security Notes



### Do not share AWS credentials



AWS credentials should never be committed to Git repositories.



Never store:



```text

AWS Access Keys

AWS Secret Keys

Passwords

Private Keys

Session Tokens

```



inside this repository.



### Avoid destructive testing



Permission testing involving bucket deletion should only use disposable test resources.



### Use least privilege



Avoid giving users administrator permissions when narrower permissions are sufficient.



### Review permissions regularly



Unused or excessive permissions should be removed.



---



## 🎓 Learning Outcomes



After completing this experiment, the following concepts were understood:



- AWS IAM architecture.

- IAM users.

- IAM groups.

- IAM policies.

- Policy JSON.

- Authentication.

- Authorization.

- S3 permissions.

- Explicit Deny.

- Allow versus Deny.

- Policy evaluation.

- Least privilege.

- Identity-based access control.

- Secure cloud resource management.

- Permission testing.



---



## 📈 Experiment Result



The AWS IAM practical was successfully completed.



The experiment demonstrated:



```text

IAM Users

    ↓

Permissions

    ↓

IAM Policies

    ↓

S3 Access

    ↓

Explicit Deny

    ↓

Restricted Destructive Operation

```



The IAM configuration successfully demonstrated that:



```text

Allow s3:*

      +

Deny s3:DeleteBucket

      ↓

Other S3 Operations → Allowed

Bucket Deletion     → Denied

```



Therefore, the experiment successfully demonstrated IAM-based authorization and a practical application of least-privilege cloud security.



---



## 🏁 Conclusion



This experiment provided practical understanding of **AWS Identity and Access Management** and its role in securing cloud resources.



IAM users were created and managed through the AWS Management Console, permissions were examined through IAM policies, and Amazon S3 was used to demonstrate resource-level authorization.



The most important security concept demonstrated was the use of an explicit Deny to restrict `s3:DeleteBucket` even when broad S3 permissions are available. This showed how IAM policy evaluation can be used to create security guardrails and reduce the impact of destructive operations.



The experiment establishes a foundation for more advanced cloud security topics such as IAM roles, MFA, CloudTrail, AWS Organizations, policy conditions, service control policies, and DevSecOps security controls.



---



## 👨‍💻 Author



**Nitanshu Tak**



B.Tech — Computer Science Engineering



Cloud Computing & Virtualization Technology



---



> 🔐 **Cloud Computing Security & Management — Identify → Authorize → Restrict → Verify**
