# Hi, I'm Carlo 👋
### Cloud Engineering Student | Systems Architecture & Automation

Based in Cebu, Philippines, I am a technology student actively transitioning into Cloud Computing and DevOps. I believe the best way to learn is by building and getting my hands dirty in the terminal.

This portfolio documents my hands-on engineering labs, showcasing my progression from foundational Linux administration to cloud provisioning, scripting, and network automation. 

---
 Linux- [https://github.com/cruzcarlo/Linux-] 
## 🐧 1. Linux Systems Administration
**Objective:** Master the command-line interface and internal server environments.

Before touching the cloud, I needed to understand the operating system that runs it. I practiced core Linux administration by navigating file systems, enforcing security through file permissions, and monitoring system processes. This foundational knowledge allows me to confidently troubleshoot headless server environments.

**Execution Proof:**
```bash
ls -l            # Inspect directory contents and current permissions
chmod 755 file   # Enforce secure read/write/execute permissions
ps aux           # Audit all running system processes
top              # Monitor real-time CPU and memory allocation

   AWS-BASICS    [https://github.com/cruzcarlo/AWS-BASICS]
## ☁️ 2. AWS Cloud Provisioning & Web Hosting
**Objective:** Deploy and manage remote infrastructure.

I provisioned an Amazon EC2 instance to understand how cloud computing works under the hood. I successfully navigated SSH key authentication (.pem files) to securely connect to my remote server and installed an Nginx web server to host a live webpage.

Execution Proof:

Bash
# Securely connecting to the remote AWS EC2 instance
ssh -i ~/Downloads/mylab-key.pem ec2-user@<public-ip>

# Updating packages and installing the Nginx web server
sudo dnf install nginx -y

Scripting Using Cron    [https://github.com/cruzcarlo/Scripting-]
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

-The-Sentinel-System-Network-Auditor-     [https://github.com/cruzcarlo/-The-Sentinel-System-Network-Auditor-]
## 🛡️ 4. The Sentinel System: Network Auditor
**Objective:**  Monitor system security and analyze network traffic.

I built the "Sentinel System" to act as an automated network auditor. This lab focused on identifying open ports, monitoring active connections, and capturing raw network packets to ensure the server wasn't exposed to unwanted traffic or unauthorized access.

Execution Proof:

Bash
netstat -tulnp   # List all active listening ports and their PIDs
ss -ltn          # Quickly audit TCP socket connections
tcpdump -i eth0  # Capture and analyze live network packets on the main interface

Terraform    [https://github.com/cruzcarlo/Terraform]
## 🏗️ 5. Infrastructure as Code (Terraform)
**Objective:** Replace manual "click-ops" with version-controlled code to prevent configuration drift.

I implemented a Local-First strategy using Terraform to master the resource lifecycle without incurring cloud costs. By managing the State File (.tfstate), I ensured that my infrastructure is idempotent—meaning the code always results in the exact same environment regardless of how many times it is run.

Execution Proof:

Bash
terraform init          # Initialize the directory and local provider
terraform plan          # Preview the "Infrastructure Receipt" before building
terraform apply         # Execute the code to provision the resource

Kurbenetes    [https://github.com/cruzcarlo/Kurbenetes]
## 🚢 6. Container Orchestration (Kubernetes)
**Objective:** Build high-availability systems that automatically recover from server failures.

I moved beyond basic Docker containers to a managed cluster using Minikube. I successfully performed a "Chaos Test" to verify Kubernetes' self-healing capabilities.

Execution Proof:

Bash
kubectl get pods        # Identify active web server instances
kubectl delete pod <id> # Simulate a server crash by deleting a pod
kubectl get pods -w     # Watch Kubernetes instantly respawn a replacement

 CI-CD    [https://github.com/cruzcarlo/CI-CD]
## 🚀 7. CI/CD & Automation (GitHub Actions)
**Objective:** Automate the build, test, and deployment pipeline to ensure fast and reliable software delivery.

I explored the basics of CI/CD pipelines to eliminate manual deployments. By using triggers and secrets management, I learned how to move code from a repository to a running environment automatically upon a "git push".

Key Concepts Applied:

Workflows: Defining the automated steps for the server to follow.

Secrets Management: Safely storing API keys and credentials so they aren't exposed in the code.

Monitoring-and-Observability    [https://github.com/cruzcarlo/Monitoring-and-Observability]
# 🚀 8. Local Cloud & Observability Stack
## 📖 Overview
This project is a localized simulation of a modern DevOps and Site Reliability Engineering (SRE) environment. It demonstrates the ability to provision infrastructure as code, deploy self-healing applications, and monitor system metrics in real-time.

## 🛠️ Tech Stack
*   **Container Orchestration:** Kubernetes (Minikube)
*   **Infrastructure as Code (IaC):** Terraform (HCL)
*   **Containerization:** Docker & Docker Compose
*   **Observability & Monitoring:** Prometheus & Grafana
*   **Environment:** WSL (Ubuntu) on Windows

## 🏗️ Project Architecture
1.  **Kubernetes Deployment:** Deployed a highly available Nginx web server demonstrating pod lifecycle management and self-healing capabilities.
2.  **Terraform Provisioning:** Authored HCL scripts to define and plan AWS EC2 instances (simulated deployment in `ap-southeast-1`).
3.  **Observability Pipeline:** 
    *   Configured **Prometheus** to scrape system and application metrics at 15-second intervals.
    *   Connected **Grafana** to Prometheus to visualize time-series data, specifically tracking `prometheus_http_requests_total` to monitor live traffic spikes.

## 🐛 Challenges & Troubleshooting
During this build, I encountered and resolved several real-world infrastructure issues:
*   **Architecture Mismatch:** Resolved an `exec format error` by identifying processor architecture (ARM vs x86) and downloading the strictly compatible binaries for Minikube.
*   **Network Unreachable Errors:** Overcame WSL to Ubuntu archive connection failures by forcing IPv4 package resolution (`-o Acquire::ForceIPv4=true`) during the Docker Compose installation.

## 🚀 How to Run the Monitoring Stack
To spin up the Prometheus and Grafana instances locally:
1. Navigate to the monitoring directory: `cd ~/cloud-labs/monitoring`
2. Start the containers in detached mode: `docker-compose up -d`
3. Access Grafana at `http://localhost:3000` (Default credentials: admin/admin)
4. To shut down and clean up resources: `docker-compose down`

Linux-Deep    [https://github.com/cruzcarlo/Linux-Deep]
# 🌐 8. Deep Linux Networking & Container Internals (Advanced)
**Objective:** Moving beyond the "magic" of Docker to understand and manually engineer the underlying Linux network primitives that power modern Cloud and SRE environments. 

As a 3rd-year IT student, I wanted to prove that I don't just know how to run containers, but I know how they actually work at the kernel level.

**Core Achievements:**
*   **Manual Container Networking:** Engineered logical network boundaries from scratch. I created isolated Linux **Network Namespaces (`ip netns`)** and linked them using virtual ethernet (`veth`) cables to simulate exactly how Docker isolates application traffic.
*   **Kernel-Level Traffic Control:** Configured packet filtering using **iptables** to act as a "Cloud Bouncer," enforcing strict ingress/egress security policies (e.g., blocking malicious IPs and opening Port 80 for web traffic).
*   **Deep Packet Inspection (DPI):** Captured raw network streams utilizing **tcpdump** on Port 443, exporting `.pcap` files for advanced forensic analysis.
*   **Advanced Diagnostics:** Upgraded my troubleshooting toolkit by replacing legacy tools with modern equivalents: `ss` (Socket Statistics), `nc` (Netcat for port probing), and `dig` (DNS resolution).

#### 🐛 Debugging & Troubleshooting Log
Real engineering is about fixing things when they break. Here are the specific issues I encountered and resolved during this module:

1.  **The "Command Not Found" / Package Resolution Error**
    *   *Symptom:* When attempting to run `tcpdump`, the system returned a "command not found" error. Standard `apt-get install` commands failed due to a broken IPv6 network bridge in WSL.
    *   *The Fix:* I bypassed the broken routing by forcing the package manager to strictly resolve via IPv4 using the command: `sudo apt-get install tcpdump -y -o Acquire::ForceIPv4=true`.
2.  **The "Hung" Packet Capture**
    *   *Symptom:* Running `tcpdump -i any port 443 -c 50` resulted in a terminal that appeared completely frozen because it was waiting for 50 specific packets to pass through a quiet interface.
    *   *The Fix:* Instead of just waiting, I diagnosed the traffic flow. I realized Port 443 requires active HTTPS requests. I manually generated secure web traffic via a browser to force the packets through the interface, instantly satisfying the `-c 50` parameter and successfully writing the `.pcap` file.

#### 💻 Execution Proof (Simulating Docker's Core Engine)
```bash
# Creating isolated namespaces (simulating two containers)
sudo ip netns add red
sudo ip netns add blue

# Creating the virtual cable and plugging them in
sudo ip link add veth-red type veth peer name veth-blue
sudo ip link set veth-red netns red
sudo ip link set veth-blue netns blue

# Activating the network and proving isolation via Ping
sudo ip netns exec red ip addr add 10.0.0.1/24 dev veth-red
sudo ip netns exec red ip link set veth-red up
# Result: Successful manual namespace communication.

Ansible [https://github.com/cruzcarlo/Ansible]
# 🚀 9 Automated Configuration Management with Ansible
Lab Author: Carlo | 3rd Year BSIT Student
Executive Summary
This lab demonstrates my ability to transition from manual server configuration to Infrastructure as Code (IaC). Using Ansible, I engineered a system to automatically provision, configure, and manage a web server environment on Linux. This project highlights my understanding of Idempotency, which is the industry-standard approach for ensuring system stability and preventing configuration drift.

Core Technical Concepts
1. Idempotency (Desired State Engineering)
The hallmark of this lab is the principle of Idempotency. Unlike traditional scripts that fail if run twice, my Ansible Playbooks check the current state of the server.

Proof of Concept: On the first execution, Ansible installed Nginx (changed=1). On the second execution, Ansible verified the server already matched the code and safely made zero changes (changed=0).

2. Inventory & Task Management
Inventory Control: Configured a modular inventory to target specific host groups (e.g., [webservers]), allowing for scalable management of multiple nodes.

Privilege Escalation: Utilized the become: yes directive to securely execute administrative tasks (sudo) across managed nodes.

3. Dynamic Content Deployment
Automated Provisioning: Used the apt and service modules to handle software lifecycles.

Custom Deployment: Automated the injection of custom web content into the /var/www/html directory, proving the ability to handle file-system management through code.

Hands-on Implementation
The Playbook (web-setup.yml)
YAML
---
- name: Configure Nginx Web Server
  hosts: webservers
  become: yes

  tasks:
    - name: Ensure Nginx is installed
      apt:
        name: nginx
        state: present

    - name: Ensure Nginx service is running
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Deploy custom index.html
      copy:
        dest: /var/www/html/index.html
        content: "<h1>Automated by Ansible</h1>"
Execution Workflow
Bash
# Running the automation
ansible-playbook -i inventory.ini web-setup.yml -K
Portfolio Evidence
In the final verification step, the server was confirmed to be live at localhost, displaying the content injected by the Ansible playbook. This confirms a successful end-to-end automation cycle.

Technical Toolstack
Automation: Ansible

Language: YAML

Web Engine: Nginx

Environment: Linux (WSL/Ubuntu)
