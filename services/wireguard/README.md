# WireGuard

WireGuard is a VPN service that creates encrypted tunnel between devices and a private network.

In this setup it allows remote devices such as a phone or laptop to securely access internal homelab services when outside of the local network.

## Deployment

- Platform: Proxmox
- Virtualization: Unprivileged LXC containers
- Operating system: Debian
- Deployment model:
    - Current: Manually provisioned
    - Target state: Terraform managed (with Ansible if needed)

## Instances

| Name               | Role             | IP address   |
| :-                 | :-               | :-           |
| pve-wireguard-srv  | VPN              | wireguard-ip |


IP addresses are statically assigned according to the homelab IP plan. <br>
Reference IP assingments datastore for correct IP addresses.