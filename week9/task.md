# 📦 Serve a secure, custom-domain website from S3 via CloudFront with HTTPS using a free Freenom domain and Route 53 DNS.

## 📝 Description

Register a free domain name on freenom.com and connect it to AWS ROUTE 53 by updating the nameservers with those from your hosted zone. 

Create a cloudfront distribution that serves your S3 static website, then request and validate a free SSL certificate using ACM with DNS validation in route 53.

---

## ✅ Deliverables

- [x] Route 53 hosted zone
- [x] Validated SSL in AWS Certificate Manager
- [x] CloudFront settings with custom domain
- [x] Live website loading over HTTPS

---

### 🧩 Prerequisites:

* S3 bucket with static website hosting enabled (`index.html`, etc.)
* AWS account access
* A verified email for Freenom

---

## 🧭 STEP-BY-STEP SETUP

---

### **1️⃣ Register a Free Domain on Freenom**

1. Go to [https://www.freenom.com](https://www.freenom.com)
2. Search for a free domain (e.g. `mycloudsite.ml`)
3. Click “Get it now” → Checkout
4. Choose **12 months FREE**, and register
5. Open **Freenom Client Area > My Domains**
6. Click **Manage Domain > Management Tools > Nameservers**

   * Change from `Use default` to:

     ```
     Use custom nameservers:
     ns-xxxx.awsdns-xx.org
     ns-xxxx.awsdns-xx.co.uk
     ns-xxxx.awsdns-xx.com
     ns-xxxx.awsdns-xx.net
     ```
   * These come from your Route 53 Hosted Zone (we’ll get them in the next step)

✅ Save — but DNS updates may take 10–30 minutes to propagate

---

### **2️⃣ Create a Hosted Zone in Route 53**

1. Go to **Route 53 > Hosted Zones**
2. Click **Create hosted zone**

   * Domain name: `yourdomain.ml` (exactly as registered)
   * Type: **Public hosted zone**
3. Click **Create**

You'll now see **4 nameservers** under **NS record**. Copy these and paste them into **Freenom** (step above).

---

### **3️⃣ Upload Your Website to S3**

1. Create an S3 bucket named **exactly your domain**, e.g., `mycloudsite.ml`
2. Enable **static website hosting**
3. Upload your `index.html` (and optional `error.html`)
4. Set a **bucket policy** to allow public access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mycloudsite.ml/*"
    }
  ]
}
```

---

### **4️⃣ Request SSL Certificate from ACM (for HTTPS)**

1. Go to **ACM (AWS Certificate Manager)**
2. Click **Request certificate**

   * Choose **Request a public certificate**
   * Add domain: `mycloudsite.ml`
   * Add another: `www.mycloudsite.ml` (optional redirect)
3. Choose **DNS validation**
4. Click **Next** > **Request**

Now ACM gives you a **CNAME record** for validation.

---

### **5️⃣ Validate Domain in Route 53**

1. Go back to your Hosted Zone
2. Click **Create record**
3. Paste the **CNAME name** and **value** ACM gave you
4. Save

✅ ACM will automatically validate it (within 5–15 mins). When done, status becomes **“Issued”**.

---

### **6️⃣ Create CloudFront Distribution**

1. Go to **CloudFront > Create Distribution**
2. Origin settings:

   * **Origin domain**: select your **S3 static website endpoint**
     (*Looks like: `mycloudsite.ml.s3-website-us-east-1.amazonaws.com` — must be the **website endpoint**, not the REST API endpoint*)
   * **Protocol**: HTTP only
3. Default behavior:

   * Viewer Protocol Policy: **Redirect HTTP to HTTPS**
   * Allow all methods: GET, HEAD
4. Alternate domain (CNAME):

   * Add: `mycloudsite.ml`
   * Add: `www.mycloudsite.ml` (optional)
5. **SSL Certificate**:

   * Select **“Custom SSL Certificate (ACM)”**
   * Choose the one you requested earlier
6. Default root object: `index.html`
7. Click **Create Distribution**

Wait for status to become **“Deployed”** (\~10–20 minutes)

---

### **7️⃣ Add Route 53 Alias Record to Point to CloudFront**

1. Go to **Route 53 > Hosted Zones**
2. Click your domain
3. Create a **new record**

   * Name: leave empty (this means root domain)
   * Type: **A – IPv4**
   * Alias: **Yes**
   * **Alias Target**: Select your CloudFront distribution
4. (Optional) Create another for `www` subdomain pointing to CloudFront

✅ This connects your **domain name to CloudFront**.

---

### **8️⃣ Test Your Site**

* Visit: `https://mycloudsite.ml`
  ✅ You should see your static site load securely via HTTPS!

---

## 🔐 Summary of Services Used:

| Service        | Purpose                      |
| -------------- | ---------------------------- |
| **Freenom**    | Domain registration          |
| **Route 53**   | DNS + certificate validation |
| **S3**         | Static website files         |
| **ACM**        | Free SSL certificate         |
| **CloudFront** | CDN + HTTPS frontend         |

---
