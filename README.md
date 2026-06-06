# quick-start
[🇷🇺 Русский (Russian)](RU-README.md)

A quick start instruction repository for setting up the Jia server and web clients using Docker Compose and Ansible.

## Deployment with Ansible

This repository includes an Ansible playbook that orchestrates the entire deployment of Jia. It will automatically build and start the Go backend, PostgreSQL database, Minio S3 storage, and the React frontends.

### Prerequisites
- Docker and Docker Compose installed
- Ansible installed (`pip install ansible` or `apt install ansible`)

### Running the Setup Script

To deploy all repositories in one run, execute the following command:

```bash
ansible-playbook deploy.yml -K
```
> **Note**: The `-K` (`--ask-become-pass`) flag is required if you choose `yes` for Nginx setup, as Ansible will need sudo privileges to install and configure Nginx on the host system.

During the execution, the playbook will ask you for several parameters (e.g., ports, domain name, API URLs, database password). It will then:
1. Generate the required `.env` files across the `server`, `web-admin`, and `web-client` projects.
2. Render a unified `docker-compose.yml` file.
3. Build and bring up the Docker containers.
4. (Optional) Install and configure an Nginx reverse proxy.
