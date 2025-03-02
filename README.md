# Ansible Setup on WSL for Managing EC2 Ubuntu Servers
This guide walks you through the steps to set up Ansible on your WSL (Ubuntu) machine and use it to manage EC2 Ubuntu servers. You'll be able to configure, manage, and automate tasks on your EC2 instances via Ansible.

## prerequisites
- Before you begin, make sure you have the following:
- WSL (Ubuntu) installed on your Windows machine.
- Two EC2 Ubuntu servers with public IP addresses.
- SSH access configured to the EC2 Ubuntu servers (via key pairs or username/password).
- Ensure Python is installed on your EC2 servers as Ansible requires Python to be present on the managed hosts.

## Steps
### Step 1: Install Ansible on WSL (Ubuntu)
Open your WSL terminal (Ubuntu) and update the package list:
```bash
sudo apt update```
Install Ansible:

bash
Copy
sudo apt install ansible -y
Verify the installation:

bash
Copy
ansible --version
This should return the installed version of Ansible.

