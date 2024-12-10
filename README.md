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
