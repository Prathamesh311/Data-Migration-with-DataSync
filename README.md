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
- Create an **EFS file system** to store the migrated data.

📸 *Screenshot:*  
![EFS Destination](PRO-SS/DataSync-EFS.png)

---

### 3️⃣ Deploy DataSync Agent
- Launch an **EC2 instance** using the AWS DataSync Agent AMI.
- Connect the agent in the **DataSync Console**.

📸 *Screenshot:*  
![DataSync Agent](PRO-SS/Agent.png)

---

### 4️⃣ Create and Run DataSync Task
- Source Location → S3 bucket  
- Destination Location → EFS file system  
- Configure task options and **execute the task**.

📸 *Screenshots:*  
![Task Creation](PRO-SS/Task.png)  
![Task Execution](PRO-SS/TaskExc.png)

---

### 5️⃣ Verify Migration
- Launch an **EC2 instance**.
- Mount the EFS and verify migrated files.

📸 *Screenshot:*  
![EC2 Verification](PRO-SS/EC2.png)

```bash
sudo yum install -y nfs-utils
mkdir efs
sudo mount -t nfs4 <EFS-DNS>:/ efs
cd efs
ls

