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
```
### Step 2: Configure SSH Access to EC2 Servers
Ensure you can SSH into your EC2 instances using key-based authentication:
```bash
ssh -i /path/to/your/key.pem ubuntu@your-ec2-ip
```

### Step 3: Set Up Ansible Inventory
Create an inventory file to define the EC2 hosts:

```bash
echo "[ec2_servers]
server1 ansible_host=your-ec2-ip-1 ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/your/key.pem
server2 ansible_host=your-ec2-ip-2 ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/your/key.pem" > inventory.ini
```

### Step 4: Test Connectivity
Run the following command to test connectivity:

```bash
ansible -i inventory.ini ec2_servers -m ping
```

If successful, you should see a "pong" response from each server.

### Step 5: Run an Ansible Playbook
Create a simple playbook to install Nginx on the EC2 servers:

```bash
- name: Install Nginx on EC2 servers
  hosts: ec2_servers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
```
Save this file as install_nginx.yml and execute it:

ansible-playbook -i inventory.ini install_nginx.yml
