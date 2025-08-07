
---

# 🔐 AWS Identity Center: User with SecurityAudit Permissions

## 📝 Description

This project demonstrates how to **create and configure AWS Identity Center**, formerly known as AWS SSO, by:

- Setting up an **Identity Center instance**
- Creating a **new user**
- Assigning a **permission set** using the predefined **`SecurityAudit` job function policy**

This enables centralized and secure access management across AWS accounts with fine-grained auditing capabilities.

---

## 🎯 Deliverables

Include the following screenshots:

- ✅ Identity Center **instance setup**
- ✅ **User details** in Identity Center
- ✅ **Assigned permission set** showing the `SecurityAudit` policy

---

## 🚀 Steps to Set Up Identity Center

### ✅ STEP 1: Enable AWS Identity Center

1. Go to the **AWS IAM Identity Center** service in the AWS Console  
2. Click **"Enable"** if it hasn’t been set up yet  
3. Choose **AWS Organization** or **Standalone** (based on your use case)  
4. Wait for the Identity Center instance to be created

---

### ✅ STEP 2: Create a New User

1. In the Identity Center dashboard, go to **Users**
2. Click **“Add user”**
3. Enter details like:
   - Username (e.g., `auditor.user`)
   - Email address (for login access)
   - First & last name
4. Click **“Next”** and then **“Add user”**

---

### ✅ STEP 3: Assign a Permission Set

1. Navigate to **AWS Accounts** → Select the desired account
2. Click **“Assign users or groups”**
3. Choose the new user created in Step 2
4. Under **Permission sets**, click **“Create new permission set”**
5. Select:
   - **Predefined job function** → Choose `SecurityAudit`
6. Complete the assignment process

---

## 📸 Screenshots to Include

- ✅ **User and Assigned Permission Set**   
  ![Permission Set](identity%20center.png)

---

## ✅ Notes

- The **`SecurityAudit`** policy allows read-only access to security-relevant info.
- Make sure the user has access to the **AWS access portal** via email.
- You can test by logging in with the user’s credentials to confirm permissions are enforced.

---
