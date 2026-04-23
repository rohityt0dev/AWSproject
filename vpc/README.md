# 🚀 AWS VPC Project: Public & Private Subnet Architecture

## 📌 Project Overview

This project demonstrates how to design and implement a secure and scalable network infrastructure using **Amazon VPC**.

The architecture separates resources into **public and private subnets**, following best practices used in real-world production environments.

---

## 🧱 Architecture Diagram

![Architecture](https://github.com/rohityt0dev/AWSproject/blob/1a04b8857bf8e60d8062625106a216c814fc2c7e/vpc/vpc-project.png)

---

## 🎯 Objectives

* Create a custom VPC with CIDR block
* Design public and private subnets
* Enable secure internet access using Internet Gateway & NAT Gateway
* Configure route tables for traffic control
* Deploy EC2 instances in both subnets
* Implement a basic bastion host setup

---

## 🏗️ Architecture Components

### 🌐 Networking

* VPC (10.0.0.0/16)
* Public Subnet (10.0.1.0/24)
* Private Subnet (10.0.2.0/24)

### 🔌 Internet Access

* Internet Gateway (for public subnet)
* NAT Gateway (for private subnet outbound access)

### 🛣️ Routing

* Public Route Table → Internet Gateway
* Private Route Table → NAT Gateway

### 💻 Compute

* Public EC2 Instance (Bastion Host)
* Private EC2 Instance (Backend Server)

---

## 🔐 Security Design

* Public EC2 allows:

  * SSH (22)
  * HTTP (80)
* Private EC2:

  * No public IP
  * SSH access only via Bastion Host
* Controlled traffic using Security Groups

---

## 🛠️ Step-by-Step Setup

### 1️⃣ Create VPC

* CIDR: `10.0.0.0/16`

---

### 2️⃣ Create Subnets

* Public Subnet → `10.0.1.0/24`
* Private Subnet → `10.0.2.0/24`

---

### 3️⃣ Create and Attach Internet Gateway

* Attach IGW to VPC

---

### 4️⃣ Configure Public Route Table

```
Destination: 0.0.0.0/0 → Internet Gateway
```

---

### 5️⃣ Create NAT Gateway

* Place in Public Subnet
* Attach Elastic IP

---

### 6️⃣ Configure Private Route Table

```
Destination: 0.0.0.0/0 → NAT Gateway
```

---

### 7️⃣ Launch EC2 Instances (Amazon EC2)

#### Public Instance

* Public IP enabled
* Used as Bastion Host

#### Private Instance

* No Public IP
* Access via Bastion Host

---

## 🧪 Testing

### ✅ Connect to Public EC2

```bash
ssh -i key.pem ec2-user@<public-ip>
```

### ✅ Connect to Private EC2 from Public

```bash
ssh -i key.pem ec2-user@<private-ip>
```

### ✅ Test Internet from Private Instance

```bash
ping google.com
```

---

## 📊 Key Concepts Learned

* VPC design and CIDR planning
* Public vs Private subnet architecture
* Internet Gateway vs NAT Gateway
* Route table configuration
* Bastion host security model

---

## 🌍 Real-World Use Case

* Public subnet → Load Balancer / Web Tier
* Private subnet → Application + Database Tier
* Secure multi-tier architecture used in production systems

---

## 🚀 Future Improvements

* Add Application Load Balancer
* Implement Auto Scaling Group
* Use Terraform for Infrastructure as Code
* Deploy real application (Node.js / Python)
* Add monitoring with CloudWatch

---

## 👨‍💻 Author

**Your Name**
Aspiring DevOps Engineer | AWS | Docker | Kubernetes

---

## ⭐ If you found this helpful

Give this repo a star ⭐ and connect with me on LinkedIn!
