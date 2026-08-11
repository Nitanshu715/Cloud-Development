# ☁️ Experiment 2: Introduction to Amazon EC2


**Cloud Development Lab** · **AWS EC2** · **ap-south-1 (Mumbai)**


> **Objective:** Launch a cloud-based virtual machine, configure secure access, connect to it remotely, and inspect its basic system and network resources.


---


## 📋 Experiment Details


| Item | Configuration |

|---|---|

| **AWS Service** | Amazon EC2 |

| **Region** | Asia Pacific (Mumbai) — `ap-south-1` |

| **Instance Type** | `t3.micro` |

| **Operating System** | Amazon Linux 2023 |

| **Access** | EC2 Instance Connect |

| **Security** | Security Group + SSH |

| **SSH Port** | `22` |


---


## 🎯 Aim


To understand the basic workflow of **Amazon EC2** by creating a virtual server, configuring network access, connecting to the instance, and examining its operating system and available resources.


---


## 🚀 Experiment Workflow


```text

AWS Console

    │

    ▼

Launch EC2 Instance

    │

    ├── Amazon Linux 2023

    ├── t3.micro

    └── Security Group

            │

            ▼

      SSH / Port 22

            │

            ▼

  EC2 Instance Connect

            │

            ▼

   Linux System Inspection

```


---


## 🛠️ Steps Performed


1. Opened **Amazon EC2** from the AWS Management Console.

2. Selected the **Mumbai (`ap-south-1`)** AWS region.

3. Launched a free-tier eligible `t3.micro` instance.

4. Selected **Amazon Linux 2023** as the AMI.

5. Configured the associated Security Group for SSH access on port `22`.

6. Waited for the instance to reach the **Running** state and pass its status checks.

7. Connected to the instance using **EC2 Instance Connect**.

8. Used Linux commands to inspect the virtual machine.

9. Verified the operating system, CPU, memory, storage, hostname, and network configuration.

10. Completed the experiment and cleaned up the AWS resource when no longer required.


---


## 💻 Linux Commands


| Command | Purpose |

|---|---|

| `whoami` | Displays the current user |

| `pwd` | Displays the current working directory |

| `cat /etc/os-release` | Displays OS information |

| `hostname` | Displays the instance hostname |

| `lscpu` | Displays CPU and virtualization details |

| `free -h` | Displays memory usage |

| `df -h` | Displays disk/filesystem usage |

| `ip addr` | Displays network interfaces and IP addresses |


---


## 🔎 Observations


- The EC2 instance was successfully launched.

- The instance reached the **Running** state.

- All required instance status checks passed.

- **Amazon Linux 2023** was verified from the terminal.

- CPU and virtualization details were inspected.

- Memory and disk utilization were checked.

- The instance's private network interface and IP address were identified.

- Remote shell access was successfully established through **EC2 Instance Connect**.


---


## 🧠 Concepts Covered


**EC2** — Provides virtual compute capacity in AWS.


**AMI** — A template containing the operating system and configuration used to launch an instance.


**Instance Type** — Defines the compute resources allocated to an EC2 instance.


**Security Group** — Acts as a virtual firewall controlling inbound and outbound traffic.


**SSH** — Secure protocol used for remote command-line access.


**EC2 Instance Connect** — Provides browser-based SSH access to an EC2 instance.


---


## 📸 Screenshots


Screenshots from the practical execution can be added below:


1. EC2 instance launch / running state

2. Security Group configuration

3. EC2 Instance Connect terminal

4. Amazon Linux 2023 verification

5. CPU, memory, and storage information

6. Network configuration


---


## 📁 Repository Structure


```text

cloud-development/

└── experiment-2/

    └── README.md

```


---


## ✅ Result


The EC2 instance was successfully **created, configured, accessed, and inspected**. The experiment demonstrated the fundamental workflow of provisioning and working with a cloud-based Linux virtual machine using Amazon EC2.


---


### 🏁 Conclusion


This experiment provided a practical introduction to **AWS EC2**, covering instance provisioning, Security Groups, remote access, and basic Linux system administration.


**Experiment 2 — Completed Successfully. 🚀**
