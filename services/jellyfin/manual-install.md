# Jellyfin manual installation

This document contains the manual steps to provision Jellyfin container before infrastructure automation is introduced.

## Prerequirities

- Proxmox host
- LXC template: Debian 13
- Static IP allocation

## LXC container settings

- Type: Unprivileged container
- System requirements
    - CPU: 1 core
    - Memory: 1024 MB
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
https://jellyfin.org/docs/general/installation/linux/#debuntu-debian-ubuntu-and-derivatives-using-apt

```bash
curl https://repo.jellyfin.org/install-debuntu.sh | sudo bash
```

### Post-install

- Verify web UI accessability
    - jellyfin.srv.ip:8096
- Follow Setup Wizard on the web browser