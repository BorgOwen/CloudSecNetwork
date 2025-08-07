
---

```md
# 🖥️ Launch Windows Server EC2 Instance on AWS

## 📝 Description

This project involves launching a new **Windows Server 2019 EC2 instance** using the official Amazon Windows Server Base AMI.  
The instance will be deployed in a **public subnet** and secured using a **security group** that allows **Remote Desktop Protocol (RDP)** access (`port 3389`) only from your **public IP address** for security.

---

## 🎯 Deliverables

Include screenshots of:

- ✅ Running **EC2 instance**
- ✅ Configured **Security Group** (showing inbound RDP access on port 3389 from your public IP)
- ✅ A **successful Remote Desktop Connection** to the instance

---

## 🚀 Steps to Deploy

### ✅ STEP 1: Launch EC2 Instance

1. Go to the **EC2 Dashboard** → Click **“Launch Instance”**
2. Name your instance (e.g., `Windows-RDP-Server`)
3. Under **Amazon Machine Image (AMI)**:
   - Choose: `Microsoft Windows Server 2019 Base`
4. Instance type: `t2.micro` (free tier eligible)
5. Choose or create a **key pair** for login
6. Under **Network settings**:
   - Select a **VPC** with a **public subnet**
   - Enable **Auto-assign public IP**
   - Configure **Security Group** (see step 2)

---

### ✅ STEP 2: Configure Security Group

1. Create a **new security group** or modify an existing one
2. Add an **inbound rule**:
   - Type: `RDP`
   - Port Range: `3389`
   - Source: `My IP` (your current public IP will be auto-filled)
3. This ensures **only you** can remotely access the server

---

### ✅ STEP 3: Connect to the EC2 Instance

1. Wait for instance state to become **Running**
2. Select the instance → Click **“Connect”** → Choose **RDP Client**
3. Download the **Remote Desktop File** and decrypt the **admin password** using your key pair
4. Open the RDP file and connect using the retrieved credentials

---

## 📸 Example Screenshots to Include

- 💻 **Running EC2 Instance Security Group**   
  ![EC2 Running](windows%20server%20ec2.png)

- 🔌 **Successful RDP Connection**   
  ![RDP Success](successful%20RDP.png)

---

## 🔒 Important Notes

- Never expose port `3389` to the world (e.g., `0.0.0.0/0`)
- Always use your **current IP address** when creating RDP access rules
- Consider using a **bastion host or VPN** for production-level access security

---
```