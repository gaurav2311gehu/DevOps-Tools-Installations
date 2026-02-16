# Jenkins Installation using Docker

This directory contains an automated Bash script to install Jenkins on Ubuntu using Docker.

The script performs the following actions:

- Installs Docker
- Starts and enables Docker service
- Creates persistent Jenkins volume
- Runs Jenkins container
- Retrieves initial admin password

---

## Prerequisites

- Ubuntu Server (20.04 / 22.04 / 24.04)
- sudo privileges
- Internet connection
- Open port **8080** in firewall/security group

---

##  Installation Steps

### 1️ Clone the Repository

```bash
git clone https://github.com/gaurav2311gehu/DevOps-Tools-Installations.git
cd DevOps-Tools-Installations/jenkins

## Grant Execute Permission
chmod +x jenkins.sh

## Run the Installation Script
./jenkins.sh
or
bash jenkins.sh

### Access Jenkins | After installation completes, open:
http://<SERVER-IP>:8080

### Get Initial Admin Password (if needed)
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

Thanks!!!