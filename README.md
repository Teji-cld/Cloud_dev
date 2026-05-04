# 🚀 AWS Production-Style Architecture Project

## 📌 Overview

This project demonstrates the design and deployment of a **production-grade cloud architecture** using Amazon Web Services.

It focuses on **security, scalability, and high availability**, using industry-standard practices such as private subnets, load balancing, and auto scaling.

---

## 🧠 Architecture Diagram

```plaintext
                Internet
                    │
                    ▼
        ┌────────────────────────┐
        │ Application Load       │
        │ Balancer (Public Subnets)
        └────────────────────────┘
                    │
                    ▼
     ┌──────────────────────────────┐
     │ Auto Scaling Group (EC2)     │
     │ Private Subnets              │
     └──────────────────────────────┘
                    │
                    ▼
        ┌────────────────────────┐
        │        Amazon S3       │
        │ (Centralized Storage)  │
        └────────────────────────┘
```

---

## 🧰 Services Used

* Amazon VPC
* Amazon EC2
* Auto Scaling Group
* Application Load Balancer
* Amazon S3
* IAM
* NAT Gateway
* Internet Gateway

---

## 🔐 Key Features

* **Custom VPC (10.0.0.0/16)** with subnet segmentation
* **Public Subnets** for Load Balancer
* **Private Subnets** for EC2 (no direct internet access)
* **Secure traffic routing** via Load Balancer
* **Auto Scaling** for fault tolerance and scalability
* **S3 integration** for centralized and consistent file storage
* **NAT Gateway** for outbound internet access from private instances

---

## ⚙️ How It Works

1. User sends request via internet
2. Load Balancer receives traffic in public subnet
3. Traffic forwarded to EC2 instances in private subnets
4. EC2 instances serve content pulled from S3
5. Auto Scaling maintains availability

---

## 📸 Project Screenshots

### 🔹 Load Balancer (Active)

![Load Balancer](./screenshots/load-balancer.png)

---

### 🔹 Target Group Health (Healthy Instances)

![Target Group](./screenshots/target-group.png)

---

### 🔹 Live Application via Load Balancer DNS

![Website Output](./screenshots/website.png)

---

## ⚠️ Challenges & Fixes

### ❌ Target group had no targets

**Cause:** ASG not attached
**Fix:** Linked Auto Scaling Group to Target Group

---

### ❌ Default Apache page (“It works!”)

**Cause:** S3 file not copied
**Fix:**

* Installed AWS CLI in user data
* Fixed bucket path
* Updated launch template

---

### ❌ S3 static site not loading

**Cause:** Permissions issue
**Fix:**

* Enabled static hosting
* Updated bucket policy
* Disabled block public access

---

### ❌ File not found errors

**Cause:** Incorrect file naming
**Fix:** Ensured exact `index.html` naming

---

## 🧩 Key Learnings

* Designing secure VPC architectures
* Public vs private subnet isolation
* NAT Gateway for outbound-only access
* Load balancing and traffic routing
* Auto Scaling lifecycle management
* IAM role-based access
* Stateless architecture using S3

---

## 🔄 Future Improvements

* Add HTTPS using ACM
* Implement CloudWatch monitoring
* Add CI/CD pipeline
* Use Infrastructure as Code (Terraform / CloudFormation)

---

## 👤 Author

Built as part of a hands-on cloud engineering learning journey focused on real-world AWS architecture.
