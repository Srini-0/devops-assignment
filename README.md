# AWS DevOps Engineer Intern Assignment

**Name:** Srinivasalu
**College:** Vels University (VISTAS)
**Branch:** BCA (Arts and Sciences)
**Email:** srinivj46@gmail.com
**Date:** 10-07-2026

## Objective
Deploy a simple website on an AWS EC2 instance and document the process.

## Live Website
- **EC2 Public IP:** `54.193.65.119`
- **URL:** `http:54.193.65.119`

---

## 1. EC2 Instance Setup

1. Launched an **Ubuntu Server 22.04 LTS** instance (`t2.micro`, free tier).
2. Created a new key pair (`devops-key.pem`) for SSH access.
3. Configured a Security Group with inbound rules:
   - Port 22 (SSH) — for remote access
   - Port 80 (HTTP) — for website access
4. Connected to the instance via SSH:
   ```bash
   chmod 400 devops-key.pem
   ssh -i devops-key.pem ubuntu@54.193.65.119
   ```

## 2. Linux Basics

Commands used to set up and verify the server environment:

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Nginx web server
sudo apt install nginx -y

# Check Nginx status
sudo systemctl status nginx

# Restart Nginx
sudo systemctl restart nginx

# Check disk usage
df -h

# Check memory usage
free -h

# View running processes
ps aux
```

## 3. Website Deployment

Replaced the default Nginx landing page with a custom HTML page containing my Name, College, Branch, Email, and Current Date.

```bash
sudo nano /var/www/html/index.html
# pasted custom HTML content

sudo systemctl restart nginx
```

The site was then verified by visiting `http://54.193.65.119` in a browser.

## 4. Bonus Task — Shell Script to Restart Nginx

Created `restart_nginx.sh` to automate restarting the Nginx service:

```bash
#!/bin/bash
sudo systemctl restart nginx
echo "Nginx restarted at $(date)"
```

Made it executable and ran it:
```bash
chmod +x restart_nginx.sh
./restart_nginx.sh
```

---

## Problems Faced
No major issues were encountered during this assignment. The setup went smoothly from instance launch through to website deployment.
 
## Learnings
- Already familiar with Linux basics and AWS EC2 from prior projects, this assignment added hands-on experience with Nginx installing it, checking its status, and restarting it using systemctl.
- Basic shell scripting to automate a repetitive task writing and running restart_nginx.sh to restart Nginx with a single command.
- 
## Total Time Taken
~30 minutes
 
## AWS Services Used
- Amazon EC2 (Ubuntu instance, compute)
- EC2 Security Groups (network access control)
 
