# 🚀 Static Website Hosting on AWS S3

This project demonstrates how to host a static website using Amazon S3. It covers bucket creation, public access configuration, and static website hosting setup.

---

## 📌 Project Overview

In this project, I deployed a simple static website using **Amazon S3**.

The website includes:

* `index.html` (main page)
* `error.html` (error handling page)

---

## 🧠 Key Concepts Learned

* Static website hosting on S3
* Bucket policies and public access
* Object storage fundamentals
* Cloud-based deployment

---

## 🏗️ Architecture

User → Browser → S3 Bucket → Static Website Files

---

## ⚙️ Steps to Deploy

### 1. Create S3 Bucket

* Created a unique S3 bucket
* Selected region (Mumbai)
* Disabled "Block all public access"

### 2. Upload Website Files

* Uploaded `index.html` and `error.html`

### 3. Enable Static Website Hosting

* Enabled static hosting in bucket properties
* Set:

  * Index document: `index.html`
  * Error document: `error.html`

### 4. Configure Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::aws-project-website-rohit/*"]
    }
  ]
}
```

### 5. Access Website

* Used S3 static website endpoint URL to access the website
* http://aws-project-website-rohit.s3-website.ap-south-1.amazonaws.com

---

## 📸 Project Screenshots



---

## 🚀 Future Improvements

* Add CDN using **Amazon CloudFront**
* Configure custom domain with **Amazon Route 53**
* Automate deployment using CI/CD pipeline
* Infrastructure as Code using Terraform

---

## 🛠️ Tools & Services Used

* Amazon Web Services
* Amazon S3

---

## 📚 What I Learned

This project helped me understand how cloud storage can be used to host websites, manage permissions, and deliver content globally.

---

## 🙌 Author

**Rohit Tambadkar**
Aspiring DevOps Engineer

---

