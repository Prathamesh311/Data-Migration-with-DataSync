# Data-Migration-with-DataSync
# 🚀 AWS Data Migration using AWS DataSync

## 📘 Project Overview
This project demonstrates **data migration from an Amazon S3 bucket to Amazon EFS** using **AWS DataSync**.  
AWS DataSync simplifies and automates large-scale data transfers between on-premises storage and AWS storage services — achieving speeds up to **10x faster** than traditional tools.

---

## 🧠 Objective
Migrate data securely and efficiently from **S3 (Source)** to **EFS (Destination)** using **AWS DataSync Agent** running on an **EC2 instance**.

---

## ⚙️ AWS Services Used
| Service | Purpose |
|----------|----------|
| **Amazon S3** | Source location containing sample objects |
| **Amazon EFS** | Destination file system for migrated data |
| **AWS DataSync** | Automates data transfer between S3 and EFS |
| **Amazon EC2** | Hosts the DataSync agent |
| **Security Groups** | Allow required ports (NFS, SSH, HTTP) |

---

## 🧩 Implementation Steps

### 1️⃣ Create Source
- Create a **Private S3 Bucket** 
### Source S3 Bucket
![Source S3 Bucket](PRO-SS/data-sync-source-1.png)



### 2️⃣ Create Destination
- Create an **EFS file system** 
![EFS](DataSync-EFS.png)

### 3️⃣ Deploy DataSync Agent
- Launch an **EC2 instance** using **AWS DataSync Agent AMI**
![EC2](EC2.png)

- Connect the agent in the **DataSync Console**
![DataSynceagent](Agent.png)

### 5️⃣ Create a Task in DataSync
- **Source Location:** S3 bucket  
- **Destination Location:** EFS file system  
- Configure options and run the task
![task](Task.png)
![task2](TaskExc.png)

### 6️⃣ Verify Migration
- Launch another EC2 instance 
![console](console.png) 
- Mount the EFS and verify the migrated files:
  ```bash
  ec2-user
  yum install -y nfs-utils
  mkdir efs
  mount -t nfs4 :/ /efs
  cd efs
  ls

