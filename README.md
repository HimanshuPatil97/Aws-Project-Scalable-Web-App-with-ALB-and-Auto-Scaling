# Scalable Web Application using AWS ALB and Auto Scaling

## 📌 Project Overview

This project demonstrates how to deploy a scalable and highly available web application using AWS Application Load Balancer (ALB), Auto Scaling Group, and Amazon EC2 instances.

The ALB distributes incoming traffic across multiple EC2 instances, while Auto Scaling automatically launches or terminates instances based on demand.

---

## 🧰 AWS Services Used

- Amazon EC2
- Application Load Balancer (ALB)
- Auto Scaling Group (ASG)
- Target Groups
- Security Groups

---

## 🚀 Implementation Steps

### 1. Launch EC2 Instances

Created Amazon Linux EC2 instances and configured:
- HTTP (Port 80)
- SSH (Port 22)

Installed Apache Web Server:

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

Created test pages:

```bash
echo "Hello from $(hostname)" | sudo tee /var/www/html/index.html
```

---

### 2. Create Target Group

Configured:
- Protocol: HTTP
- Port: 80
- Health Check Path: /

Registered EC2 instances into the target group.

---

### 3. Create Application Load Balancer

Configured:
- Internet-facing ALB
- HTTP Listener on Port 80
- Connected to target group

The ALB distributes incoming traffic among healthy EC2 instances.

---

### 4. Create Launch Template

Created a launch template containing:
- Amazon Linux AMI
- Instance type
- Security group
- Apache installation configuration

---

### 5. Create Auto Scaling Group

Configured Auto Scaling Group with:
- Desired Capacity: 2
- Minimum Capacity: 1
- Maximum Capacity: 4

Attached the Auto Scaling Group to the ALB target group.

---

### 6. Test Load Balancing

Opened the ALB DNS in browser:

```text
http://<ALB-DNS>
```

Refreshing the page displayed responses from different EC2 instances.

---

## 🎯 Features

- Load Balancing
- Auto Scaling
- High Availability
- Fault Tolerance
- Scalable Architecture

---

## 📸 Output

The ALB successfully distributed traffic across multiple EC2 instances, while Auto Scaling automatically managed instance scaling based on demand.

