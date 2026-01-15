# Jellyfin

Jellyfin is a free media server and suite of multimedia applications designed to organize, manage and share digital media files to networked devices.

This service is intended for local network use only. <br>
Remote access is intentionally not configured.

## Deployment

- Platform: Proxmox
- Virtualization: Unprivileged LXC container
- Operating system: Debian
- Deployment model:
    - Current: Manually provisioned
    - Target state: Terraform managed (with Ansible if needed)

## Instances

| Name               | Role             | IP address  |
| :-                 | :-               | :-          |
| pve-jellyfin-srv   | Media share      | jellyfin-ip |


IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.