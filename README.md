# Data-Migration-with-DataSync
# 🚀 AWS Data Migration using AWS DataSync

## 📘 Project Overview
This project demonstrates **data migration from an Amazon S3 bucket to Amazon EFS** using **AWS DataSync**.  
AWS DataSync simplifies and automates large-scale data transfers between on-premises storage and AWS storage services — achieving speeds up to **10x faster** than traditional tools.

---

## 🧠 Objective
Migrate data securely and efficiently from **S3 (Source)** to **EFS (Destination)** using **AWS DataSync Agent** running on an **EC2 instance**.

---

## 🏗️ Architecture Diagram
![AWS DataSync Architecture](1.png)

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
- Create a **Private S3 Bucket** (example: `prathamesh-s3-source`)
- Upload a few sample objects

### 2️⃣ Create Destination
- Create an **EFS file system** (example: `prathamesh-efs-target`)

### 3️⃣ Deploy DataSync Agent
- Launch an **EC2 instance** using **AWS DataSync Agent AMI**
- Connect the agent in the **DataSync Console**

### 4️⃣ Configure Security Group
- Allow **NFS (2049)**, **SSH (22)**, and **HTTP (80)**

### 5️⃣ Create a Task in DataSync
- **Source Location:** S3 bucket  
- **Destination Location:** EFS file system  
- Configure options and run the task

### 6️⃣ Verify Migration
- Launch another EC2 instance  
- Mount the EFS and verify the migrated files:
  ```bash
  sudo yum install -y nfs-utils
  sudo mkdir /mnt/efs
  sudo mount -t nfs4 <EFS_DNS_NAME>:/ /mnt/efs
  cd /mnt/efs
  ls

