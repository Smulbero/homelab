# Pi-hole manual installation

This document contains the manual steps to provision Pi-hole containers before infrastructure automation is introduced.

## Prerequirities

- Proxmox host
- LXC template: Debian 13
- Static IP allocation for two instances

## LXC container settings

- Type: Unprivileged container
- System requirements
    - CPU: 1 core
    - Memory: 512 MB
    - Storage: 4 GB 
- Network
    - IPv4: Static
    - Gateway: (ROUTER_IP_ADDRESS)

## OS preparation

```bash
apt update && apt upgrade -y

# Packages
apt install curl -y
```

## Installation

Reference documentation: <br>
https://docs.pi-hole.net/main/basic-install/

```bash
curl -sSL https://install.pi-hole.net | bash
```

### Post-install

- Set admin password
    ```bash
    pihole setpassword
    ```
- Verify admin UI accessability
    - piholesrv.ip/admin
-  Configure router or clients to use Pi-hole as DNS