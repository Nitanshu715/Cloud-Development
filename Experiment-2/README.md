# Experiment 2 — Introduction to Amazon EC2


## Aim


To launch an Amazon EC2 instance, configure basic network access, connect to the instance, and explore its operating system, CPU, memory, storage, and network information.


## AWS Services Used


- Amazon EC2

- EC2 Instance Connect

- Amazon Linux 2023

- Security Groups


## Experiment Overview


Amazon EC2 (Elastic Compute Cloud) provides resizable virtual servers in the AWS cloud. In this experiment, a free-tier eligible EC2 instance was launched in the **Asia Pacific (Mumbai) / ap-south-1** region.


The instance was configured with **Amazon Linux 2023** and a **t3.micro** instance type. After the instance passed its status checks, access was configured through the associated Security Group and the instance was opened using **EC2 Instance Connect**.


## Procedure


1. Open the AWS Management Console and navigate to **EC2**.

2. Select the **Asia Pacific (Mumbai)** region.

3. Launch a new EC2 instance using a free-tier eligible configuration.

4. Select **Amazon Linux 2023** as the operating system.

5. Select the **t3.micro** instance type.

6. Configure the required Security Group rules for SSH access on **TCP port 22**.

7. Launch the instance and wait until its status checks pass.

8. Open the instance using **EC2 Instance Connect**.

9. Run basic Linux commands to inspect the system.

10. Verify the operating system, CPU, memory, disk, hostname, and network configuration.

11. Stop/terminate the instance after completing the experiment when it is no longer required.


## Commands Used


| Command | Purpose |

|---|---|

| `whoami` | Displays the current user. |

| `pwd` | Displays the current working directory. |

| `cat /etc/os-release` | Displays operating-system information. |

| `hostname` | Displays the instance hostname. |

| `lscpu` | Displays CPU and virtualization information. |

| `free -h` | Displays memory usage. |

| `df -h` | Displays filesystem and disk usage. |

| `ip addr` | Displays network interfaces and IP addresses. |


## Observations


- The EC2 instance successfully entered the **Running** state.

- The instance passed its required status checks.

- The operating system was identified as **Amazon Linux 2023**.

- The system exposed CPU information through `lscpu`.

- Memory and storage usage were inspected using `free -h` and `df -h`.

- Network interfaces and the private IP address were verified using `ip addr`.

- The instance was successfully accessed remotely using EC2 Instance Connect.


## Result


The EC2 instance was successfully launched and accessed. Basic system and network information was inspected through the Linux command line, demonstrating the fundamental operation of an AWS cloud-based virtual machine.


## Key Concepts Demonstrated


- Cloud-based virtual machines

- EC2 instance provisioning

- AMIs and operating systems

- Instance types

- Security Groups

- SSH access

- EC2 Instance Connect

- Linux system administration

- Basic cloud networking


## Repository Structure


```text

cloud-development/

└── experiment-2/

    └── README.md

```


## Conclusion


This experiment provided a practical introduction to Amazon EC2 and demonstrated how a virtual server can be provisioned, secured, accessed, and inspected in the AWS cloud.
