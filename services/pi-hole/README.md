# Pi-hole

Pi-hole provides network wide DNS based ad blocking and DNS filtering. It acst as the primary DNS resolver for LAN and VPN clients.

Two Pi-hole instances are deployed to eliminate single point of failure and provide redundancy.

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
| pve-pihole-srv-1   | Primary DNS      | pihole-1-ip |
| pve-pihole-srv-2   | Secondary DNS    | pihole-2-ip |

IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.