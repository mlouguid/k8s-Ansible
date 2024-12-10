# Kubernetes Deployment Using Ansible

This guide outlines the steps to deploy Kubernetes on a target machine or cluster using Ansible. The playbook automates the installation and configuration of Kubernetes components on the target system.

## Prerequisites

Before you begin, ensure the following prerequisites are met:

- A **control machine** where Ansible is installed.  
  You can install Ansible using the following commands:
  - For Ubuntu/Debian:
    ```bash
    sudo apt update
    sudo apt install ansible
    ```

- A **target machine** (or multiple nodes) where:
  - Python 3 is installed and accessible.
  - `sudo` privileges are available for the user running the Ansible playbook.

## Step 1: Setting Up the Inventory File

Create an inventory file to define the hosts (target machine) for Kubernetes deployment. The following example shows how to configure the target machine IP:

```yaml
all:
  children:
    kubernetes:
      hosts:
        localhost:
          ansible_connection: local
          ansible_python_interpreter: /usr/bin/python3
```
## Step 2: Cloning the Project

Clone the Kubernetes deployment project from the repository (or use your own project):
```
git clone https://github.com/mlouguid/k8b-Ansible.git
cd k8b-Ansible
```
## Step 3: Kubernetes Role Structure

Ensure your kubernetes role has the following directory structure:
```
roles/
└── kubernetes/
    ├── tasks/
    │   ├── main.yml
    │   ├── install_k8s.yml
    │   ├── containerd.yml
    │   └── kube_prereqs.yml
    ├── handlers/
      └── main.yml
```
## step 4: deploy the playbook
```
ansible-playbook kubernetes_playbook.yml -i inventories/local/hosts --limit=kubernetes --ask-become-pass
```
