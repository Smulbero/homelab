# Service

Service description

## Deployment

- Platform: Proxmox
- Virtualization: Unprivileged LXC containers
- Operating system: Debian
- Deployment model:
    - Current: Manually provisioned
    - Target state: Terraform managed (with Ansible if needed)

## Instances

| Name               | Role             | IP address  |
| :-                 | :-               | :-          |
| service-name       | service-role     | service-ip  |


IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.