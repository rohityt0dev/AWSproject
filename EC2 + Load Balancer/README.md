# 🚀 AWS Project: Deploy Application on EC2 with Load Balancer

## 📌 Project Overview

This project demonstrates how to deploy a simple web application on multiple EC2 instances and distribute traffic using an **Application Load Balancer (ALB)**.

Built using **Amazon EC2** and **Elastic Load Balancing**, this setup ensures high availability and fault tolerance.

---

## 🧱 Architecture

User → Load Balancer → EC2 Instance 1 / EC2 Instance 2

---

## 🎯 What You Will Build

* 2 EC2 instances running a web server
* 1 Application Load Balancer (ALB)
* Simple HTML-based web application
* Public URL to access the application

---

## 🛠️ Step-by-Step Implementation

### 1️⃣ Launch EC2 Instances

Create 2 instances:

* Names: `ec2-1`, `ec2-2`
* AMI: Amazon Linux 2
* Instance Type: `t3.micro`
* Key Pair: Create/download
* Security Group:

  * Allow SSH (22)
  * Allow HTTP (80)

---

### 2️⃣ Connect to EC2

```bash
ssh -i your-key.pem ec2-user@your-public-ip
```

---

### 3️⃣ Install Web Server (Apache)

Run on BOTH instances:

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### 4️⃣ Create Simple Web App

#### Instance 1:

```bash
echo "Hello from Server 1" | sudo tee /var/www/html/index.html
```

#### Instance 2:

```bash
echo "Hello from Server 2" | sudo tee /var/www/html/index.html
```

---

### 5️⃣ Test Individually

Open in browser:

* Instance 1:

```
http://<EC2-1-public-ip>
```

* Instance 2:

```
http://<EC2-2-public-ip>
```

---

### 6️⃣ Create Load Balancer

Go to EC2 → Load Balancers

Choose:
👉 Application Load Balancer (ALB)

Configuration:

* Name: `my-lb`
* Scheme: Internet-facing
* Listener: HTTP (80)

---

### 7️⃣ Configure Security Group for Load Balancer

* Name: `my-sg-lb`
* Allow:

  * HTTP (80) from `0.0.0.0/0`

---

### 8️⃣ Create Target Group

* Type: Instances
* Protocol: HTTP
* Port: 80

👉 Register BOTH EC2 instances

---

### 9️⃣ Attach Target Group to Load Balancer

* Select created target group
* Complete ALB setup

---

### 🔟 Test Load Balancer

* Copy DNS name of Load Balancer
* Open in browser and refresh multiple times

✔ Output:

* "Hello from Server 1"
* "Hello from Server 2"

🎉 Load balancing is working!

---

## 📚 Key Concepts Learned

* EC2 (Virtual Servers)
* Load Balancer (ALB)
* Traffic Distribution
* High Availability
* Basic Linux & Apache Setup

---

## 🧪 Troubleshooting

Common issues you may face:

* ❌ 503 Error → Check target group health
* ❌ Timeout → Check security groups (port 80 open)
* ❌ Instance not reachable → Verify public IP and SSH access

---

## 🌍 Real-World Use Case

* Load Balancer → Handles incoming traffic
* EC2 Instances → Serve application
* Used in production systems for:

  * Scalability
  * Fault tolerance
  * Zero downtime

---

## 🚀 Future Improvements

* Add Auto Scaling Group
* Deploy real app (Node.js / Python)
* Add HTTPS using SSL certificate
* Use Terraform (Infrastructure as Code)
* Implement CI/CD pipeline

---

## 🏁 Conclusion

This project successfully demonstrates how to deploy a highly available web application on AWS using EC2 and an Application Load Balancer.

By distributing traffic across multiple instances, the system improves performance, reliability, and fault tolerance. It also provides hands-on experience with real-world challenges such as health checks, connectivity issues, and load balancing behavior.

This project builds a strong foundation in:

* Infrastructure setup using EC2
* Load balancing and traffic routing
* High availability and scalability
* Troubleshooting AWS deployment issues

---

## 👨‍💻 Author

**Your Name**
Aspiring DevOps Engineer | AWS | Docker | Kubernetes

---

## ⭐ Support

If you found this project helpful, give it a ⭐ on GitHub and connect with me on LinkedIn!

