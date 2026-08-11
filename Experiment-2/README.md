# ☁️ Experiment 2 — Introduction to Amazon EC2


> **Cloud Development Lab**  

> Launch, access, and explore a virtual server using **Amazon EC2**.


![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)

![OS](https://img.shields.io/badge/OS-Amazon%20Linux%202023-blue)

![Region](https://img.shields.io/badge/Region-ap--south--1-purple)

![Instance](https://img.shields.io/badge/Instance-t3.micro-green)


---


## 🎯 Aim


To launch an Amazon EC2 virtual machine, configure basic network access, connect to the instance, and inspect its system resources using Linux commands.


## 🧰 AWS Resources Used


| Resource | Configuration |

|---|---|

| **Service** | Amazon EC2 |

| **Region** | Asia Pacific (Mumbai) — `ap-south-1` |

| **Instance Type** | `t3.micro` |

| **Operating System** | Amazon Linux 2023 |

| **Access Method** | EC2 Instance Connect |

| **Network Security** | Security Group / SSH |

| **SSH Port** | TCP `22` |


---


## 🚀 What Was Done


1. Opened **Amazon EC2** in the AWS Management Console.

2. Selected the **Mumbai (`ap-south-1`)** region.

3. Launched a free-tier eligible **t3.micro** instance.

4. Selected **Amazon Linux 2023** as the AMI.

5. Configured the Security Group for SSH access.

6. Waited for the instance to become **Running** and pass its status checks.

7. Connected to the instance using **EC2 Instance Connect**.

8. Executed Linux commands to inspect the virtual machine.

9. Verified its OS, CPU, memory, storage, hostname, and network configuration.

10. Cleaned up the instance after completing the lab.


---


## 💻 Commands Used


```bash

whoami

```

Shows the currently logged-in user.


```bash

pwd

```

Displays the current working directory.


```bash

cat /etc/os-release

```

Displays operating-system details.


```bash

hostname

```

Displays the instance hostname.


```bash

lscpu

```

Displays CPU and virtualization information.


```bash

free -h

```

Displays memory usage in a human-readable format.


```bash

df -h

```

Displays filesystem and disk usage.


```bash

ip addr

```

Displays network interfaces and IP addresses.


---


## 🔍 Key Observations


- ✅ EC2 instance launched successfully.

- ✅ Instance reached the **Running** state.

- ✅ Status checks passed successfully.

- ✅ **Amazon Linux 2023** was verified.

- ✅ CPU and virtualization information were inspected.

- ✅ Memory and disk usage were verified.

- ✅ Network interfaces and private IP information were inspected.

- ✅ Remote terminal access was established through **EC2 Instance Connect**.


---


## 🧠 Concepts Demonstrated


**EC2** → Cloud-based virtual computing  

**AMI** → Template used to create the instance  

**Instance Type** → Defines compute resources  

**Security Group** → Virtual firewall controlling traffic  

**SSH** → Secure remote access protocol  

**EC2 Instance Connect** → Browser-based connection to the instance  

**Linux CLI** → Used to inspect and manage the virtual machine


---


## 📸 Screenshots


Screenshots captured during the experiment can be added here.


```text

1. EC2 Instance Launch / Running State


2. Security Group Configuration


3. EC2 Instance Connect Terminal


4. Operating System Verification


5. CPU / Memory / Storage Information


6. Network Configuration

```


---


## 📁 Repository Structure


```text

cloud-development/

└── experiment-2/

    └── README.md

```


---


## ✅ Result


The Amazon EC2 instance was successfully **launched, configured, accessed, and inspected**. The experiment provided a practical introduction to cloud-based virtual machines and basic Linux system administration on AWS.


---


### 🏁 Conclusion


This experiment demonstrated the complete basic workflow of an EC2 virtual machine — from **provisioning and network security to remote access and system inspection**.


**Experiment 2 completed successfully. 🚀**
