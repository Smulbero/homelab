# Service manual installation

This document contains the manual steps to provision service container before infrastructure automation is introduced.

## Prerequirities

- Proxmox host
- LXC template: Debian 13
- Static IP allocation

## LXC container settings

- Type: Unprivileged container
- System requirements
    - CPU: 1 core
    - Memory: 512 MB
    - Storage: 1 GB 
- Network
    - IPv4: Static
    - Gateway: (ROUTER_IP_ADDRESS)

## OS preparation

```bash
apt update && apt upgrade -y
```

## Installation

Reference documentation: <br>
https://www.wireguard.com/install/

```bash
sudo apt install wireguard
```

### Post-install

TBD