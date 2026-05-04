# Hi, I'm Carlo 👋
### Cloud Engineering Student | Systems Architecture & Automation

Based in Cebu, Philippines, I am a technology student actively transitioning into Cloud Computing and DevOps. I believe the best way to learn is by building and getting my hands dirty in the terminal.

This portfolio documents my hands-on engineering labs, showcasing my progression from foundational Linux administration to cloud provisioning, scripting, and network automation. 

---

## 🐧 1. Linux Systems Administration
**Objective:** Master the command-line interface and internal server environments.

Before touching the cloud, I needed to understand the operating system that runs it. I practiced core Linux administration by navigating file systems, enforcing security through file permissions, and monitoring system processes. This foundational knowledge allows me to confidently troubleshoot headless server environments.

**Execution Proof:**
```bash
ls -l            # Inspect directory contents and current permissions
chmod 755 file   # Enforce secure read/write/execute permissions
ps aux           # Audit all running system processes
top              # Monitor real-time CPU and memory allocation

## ☁️ 2. AWS Cloud Provisioning & Web Hosting
**Objective:** Deploy and manage remote infrastructure.

I provisioned an Amazon EC2 instance to understand how cloud computing works under the hood. I successfully navigated SSH key authentication (.pem files) to securely connect to my remote server and installed an Nginx web server to host a live webpage.

Execution Proof:

Bash
# Securely connecting to the remote AWS EC2 instance
ssh -i ~/Downloads/mylab-key.pem ec2-user@<public-ip>

# Updating packages and installing the Nginx web server
sudo dnf install nginx -y

## ⏰ 3. Automation & Disaster Recovery (Cron)
**Objective:** Eliminate manual intervention for critical system tasks.

To understand automated operations, I developed Bash scripts designed to back up critical web directories. By scheduling these scripts using Linux Cron jobs, I created a reliable, automated disaster recovery process that runs silently in the background every night.

Execution Proof:

Bash
#!/bin/bash
# backup.sh: Logs the time and compresses the web directory
echo "Backup started at $(date)" >> /home/ec2-user/backup.log
tar -czf /home/ec2-user/backup-$(date +%F).tar.gz /var/www/html

# The Crontab entry: Schedules the backup to run automatically at 2:00 AM daily
0 2 * * * /home/ec2-user/backup.sh

## 🛡️ 4. The Sentinel System: Network Auditor
**Objective:**  Monitor system security and analyze network traffic.

I built the "Sentinel System" to act as an automated network auditor. This lab focused on identifying open ports, monitoring active connections, and capturing raw network packets to ensure the server wasn't exposed to unwanted traffic or unauthorized access.

Execution Proof:

Bash
netstat -tulnp   # List all active listening ports and their PIDs
ss -ltn          # Quickly audit TCP socket connections
tcpdump -i eth0  # Capture and analyze live network packets on the main interface

## 🏗️ 5. Infrastructure as Code (Terraform)
**Objective:** Replace manual "click-ops" with version-controlled code to prevent configuration drift.

I implemented a Local-First strategy using Terraform to master the resource lifecycle without incurring cloud costs. By managing the State File (.tfstate), I ensured that my infrastructure is idempotent—meaning the code always results in the exact same environment regardless of how many times it is run.

Execution Proof:

Bash
terraform init          # Initialize the directory and local provider
terraform plan          # Preview the "Infrastructure Receipt" before building
terraform apply         # Execute the code to provision the resource
## 🚢 6. Container Orchestration (Kubernetes)
**Objective:** Build high-availability systems that automatically recover from server failures.

I moved beyond basic Docker containers to a managed cluster using Minikube. I successfully performed a "Chaos Test" to verify Kubernetes' self-healing capabilities.

Execution Proof:

Bash
kubectl get pods        # Identify active web server instances
kubectl delete pod <id> # Simulate a server crash by deleting a pod
kubectl get pods -w     # Watch Kubernetes instantly respawn a replacement

## 🚀 7. CI/CD & Automation (GitHub Actions)
**Objective:** Automate the build, test, and deployment pipeline to ensure fast and reliable software delivery.

I explored the basics of CI/CD pipelines to eliminate manual deployments. By using triggers and secrets management, I learned how to move code from a repository to a running environment automatically upon a "git push".

Key Concepts Applied:

Workflows: Defining the automated steps for the server to follow.

Secrets Management: Safely storing API keys and credentials so they aren't exposed in the code.
