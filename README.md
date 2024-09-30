Hi, ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)my name is Serhii Shypylov
=========================================================================================================================================

💛 I am a Linux System administrator engineer with DevOps practices. I have several certificates in Linux, Docker, Ansible and Terraform and continue to learn more. I like everything related to Docker, containers and IT technologies in general. I love solving complex IT solutions.
-------------------------------

* 💼 Looking for a job
* 🌍 I'm based in Poznan
* 🖥️ See my [LinkedIn](https://github.com/Shipssv83) profile 
* 👾 Chat with IT pros on [Discord](https://discord.com/shipssv_19055)\
* 📧 Reach me at ships@ukr.net
* 🧠 I'm learning DevOps Practices

### Socials

<p align="left"> <a href="https://github.com/Shipssv83" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" width="32" height="32" /> </picture> </a> <a href="https://www.linkedin.com/in/sergey-shipilov-7262a31b4/" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" width="32" height="32" /> </picture> </a></p>

# GitLab Docker Installation via Ansible

This project contains Ansible playbooks for setting up a GitLab server in a Docker container on a target server. It also includes configuration for Docker, SSH, UFW firewall, and SMTP settings.

## Overview

The installation consists of three main steps:
1. **Server Setup**: Configures the server’s timezone and other essential settings.
2. **Docker Installation**: Installs Docker and Docker Compose.
3. **GitLab Installation**: Sets up GitLab in a Docker container and configures SSH, HTTP, HTTPS, and SMTP settings for the server.

## Playbooks Overview

### 1. Server Installation (`server-install.yml`)

This playbook handles the basic server setup, including timezone configuration.

### 2. Docker Installation (`docker-install.yml`)

This playbook installs Docker and Docker Compose on the target server, ensuring the server is ready to host containers.

### 3. GitLab Docker Installation (`gitlab-docker-install.yml`)

This playbook deploys GitLab in a Docker container, along with the necessary configuration for SSH, web access, and SMTP email notifications.

### 4. Firewall Configuration (`ufw_firewall/firewall-gitlab.yml`)

This playbook configures UFW firewall rules to allow traffic on the required ports for GitLab (SSH, HTTP, HTTPS).

## Variables

You can customize the installation by setting the following variables:

- `timezone`: Server's timezone (default: `Europe/Warsaw`).
- `fqdn`: Fully Qualified Domain Name for the GitLab instance (e.g., `example.com`).
- `gitlab_ssh_host_name`: Hostname for GitLab SSH access (e.g., `ssh.example.com`).
- `gitlab_root_password`: Root password for the GitLab instance.
- `ssh_port_gitlab`: SSH port for GitLab (default: `22`).
- `http_port`: HTTP port for GitLab web access (default: `80`).
- `https_port`: HTTPS port for GitLab web access (default: `443`).
- `ssh_port`: SSH port for the server (default: `2222`).
- `gitlab_docker_version`: GitLab Docker image version (default: `17.4.1-ce.0`).
- `git_pos_user`: GitLab database username.
- `git_pos_pass`: GitLab database password.
- `git_pos_db`: GitLab database name.
- `smtp`: SMTP server for email notifications.
- `smtp_port`: Port for the SMTP server.
- `smtp_domain`: Domain name for SMTP.
- `registration_token`: GitLab registration token for runners or other integrations.

### Example Variable Configuration

```yaml
vars:
  timezone: 'Europe/Warsaw'
  fqdn: 'example.com'
  gitlab_ssh_host_name: 'ssh.example.com'
  gitlab_root_password: 'yourpassword'
  ssh_port_gitlab: '22'
  http_port: '80'
  https_port: '443'
  ssh_port: '2222'
  gitlab_docker_version: '17.4.1-ce.0'
  git_pos_user: 'username'
  git_pos_pass: 'yourpassword'
  git_pos_db: 'gitlab'
  smtp: 'smtp.example.com'
  smtp_port: '587'
  smtp_domain: 'example.com'
  registration_token: 'your_registration_token'
```

# ansible galaxy roles

```
### install role ansible galaxy
ansible-galaxy install -r roles/requirements.yml

### upgrade role ansible galaxy 
ansible-galaxy install -g -f -r roles/requirements.yml
```

# Run the Playbook install
Run the playbook by specifying your inventory file and variable file:

```
ansible-playbook -i inventory --user root --extra-vars "host=host_name" playbooks/rocketchat-install.yml
```

Conclusion
This project automates the setup of a GitLab server in Docker using Ansible, making it easier to deploy and manage your GitLab instance on a remote server.


This **README** provides a step-by-step guide to the GitLab Docker installation with Ansible, detailing playbook usage and customizable variables.


License
This project is licensed under the MIT License