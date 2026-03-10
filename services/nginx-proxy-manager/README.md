# Nginx Proxy Manager

Nging Proxy Manager is a free reverse proxy service that acts as a gateway for internal services based on hostname and port. It provides web interface for managing proxy hosts, SSL certificates and access to self-hosted services.

## Deployment

At the time of writing, official way to deploy NPM instance is done by using Docker Image. Alternative way for Proxmox specifically is to use helper script.

- Platform: Proxmox
- Virtualization: Unprivileged LXC container
- Operating system: Debian
- Deployment model:
    - Current: Proxmox helper script
    - Target state: Terraform managed (with Ansible if needed)

## Instances

| Name               | Role             | IP address  |
| :-                 | :-               | :-          |
| pve-npm-srv        | Reverse proxy    | npm-ip      |


IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.