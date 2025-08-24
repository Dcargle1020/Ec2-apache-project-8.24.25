# Ec2-apache-project-8.24.25
# 🚀 EC2 + Apache Project  

This project demonstrates how to launch an **AWS EC2 instance** and use **User Data scripts** to automatically install and run the Apache web server.  

It also compares doing the setup **manually inside Linux** vs. **automating with user-data**, showing why automation saves time and ensures consistency.  

🔍 Key Learnings
User Data scripts automate server setup at launch.
Manual setup is good for learning and debugging, but automation saves time.
Security groups are critical to allow external access (port 80 for HTTP).
EC2 + Apache is a foundational cloud project, showing how infrastructure and software come together.
---

## 📂 Project Files
- `user_data_apache.sh` → Script for **Amazon Linux 2** (uses `yum`)
- `user_data_apache_ubuntu.sh` → Script for **Ubuntu/Debian** (uses `apt-get`)
- `screenshots/` → Contains proof of successful deployment (EC2 login, Apache “It works” page, etc.)

---

## 🛠️ Steps to Recreate

### 1. Launch EC2 Instance
- Open the **AWS Management Console** → EC2 → Launch Instance.  
- Choose either:
  - Amazon Linux 2 AMI  
  - Ubuntu 22.04+ AMI  

### 2. Add User Data Script
Paste the appropriate script in the **User Data** field under **Advanced Settings**:

#### Amazon Linux 2
```bash
#!/bin/bash
apt-get update -y
apt-get upgrade -y

apt-get install -y apache2

systemctl enable apache2
systemctl start apache2

3. Configure Security Group
Allow HTTP (port 80) inbound from 0.0.0.0/0

4. Verify Apache
SSH into your instance (with .pem key).
Run: curl http://localhost

Entered the Public IPv4 address of the instance.
And seen Apache default test page (“It works!”). 🎉
http://18-237-175-81
