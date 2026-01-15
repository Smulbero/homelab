# Homepage

Homepage is self-hosted dashboard used as a central entry point to homelab services. It can also provide quick access to favorite internet services through single web interface.

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
| pve-homepage-srv   | Dashboard        | homepage-ip |

IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.