# Homepage manual installation

This document contains the manual steps to provision Homepage container before infrastructure automation is introduced.

## Prerequirities

- Proxmox host
- LXC template: Debian 13
- Static IP allocation

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
apt install git -y
apt install npm -y
```

## Installation

Homepage is installed from source following the official documentation.

Reference documentation: <br>
https://gethomepage.dev/installation/source/

```bash
# Clone repository
git clone https://github.com/gethomepage/homepage.git /tmp/git
cd /tmp/git/homepage

#  Install pnpm
npm install -g pnpm

# Install dependencies
npm install

# Build the production bundle
pnpm install
pnpm build

# If this is your first time starting, copy the src/skeleton directory to config/ to populate initial example config files.

# Run the server
HOMEPAGE_ALLOWED_HOSTS=gethomepage.dev:1234 pnpm start
```

### Post-install

- Verify web UI accessability
    - homepagesrv.ip/