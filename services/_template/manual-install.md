# Service manual installation

This document contains the manual steps to provision service container before infrastructure automation is introduced.

## Prerequirities

- Proxmox host
- LXC template: Debian 13
- Static IP allocation

## LXC container settings

- Type: Unprivileged container
- System requirements
    - CPU: TBD
    - Memory: TBD
    - Storage: TBD 
- Network
    - IPv4: Static
    - Gateway: (ROUTER_IP_ADDRESS)

## OS preparation

```bash
apt update && apt upgrade -y

# Packages
TBD
```

## Installation

Reference documentation: <br>
link to documentation

```bash
TBD
```

### Post-install

TBD