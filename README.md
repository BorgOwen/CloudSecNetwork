# 🌩️ CloudSecNetwork

This repository contains hands-on tasks completed as part of the **CloudSecNetwork** course, focusing on AWS cloud security, networking, and infrastructure deployment.

---

## ✅ Task List

### 🔹 Task 1: Create AWS Account
- Set up a new AWS account.

### 🔹 Task 2: AWS Identity Center
- Create an **AWS Identity Center**
- Add a new user
- Assign a permission set using the predefined **SecurityAudit** job function policy.

### 🔹 Task 3: Launch EC2 Instance (Windows)
- Launch a **Windows Server 2019** EC2 instance using the Amazon-provided AMI.
- Ensure it's deployed in a **public subnet**.
- Configure a **security group** to allow **RDP (port 3389)** **only from your public IP address**.

### 🔹 Task 4: VPC Setup
- Create **two separate VPCs** to simulate a **multi-VPC architecture**.

### 🔹 Task 5: Deploy Grafana on ECS Fargate
- Deploy **Grafana (Docker image)** using **Amazon ECS with the Fargate launch type**.

### 🔹 Task 6: Deploy Metabase with RDS
- Deploy **Metabase** on ECS Fargate.
- Connect it to a **PostgreSQL database** hosted on **Amazon RDS**.

### 🔹 Task 7: Deploy NGINX with CloudWatch Monitoring
- Deploy **NGINX** on ECS using Fargate in a **public subnet**.
- Add a **CloudWatch dashboard** with widgets for:
  - **CPUUtilization**
  - **MemoryUtilization**
- Simulate load using stress testing and monitor real-time metrics.

### 🔹 Task 8: Deploy a Static Website on S3 + CloudFront
- Upload a personal static website (resume, portfolio, or about me page) to **Amazon S3**.
- Enable **static website hosting** and configure public access.
- Use **Amazon CloudFront** with the S3 bucket as origin to securely deliver content.

### 🔹 Task 9: _(Pending)_

### 🔹 Task 10: _(Pending)_

---

## 📁 Structure

Each task may have associated:
- Screenshots
- Terraform/IaC templates
- Notes or scripts

> Stay tuned as I complete the remaining tasks and add more automation and monitoring tools!

---

## 🚀 Author
**Toluwabori Ogunwenmo**  
CloudSecNetwork Participant | AWS & DevOps Enthusiast
