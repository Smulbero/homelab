# Pi-hole installation

## Prerequirities
- Proxmox host
- LXC template: Debian 13
- Static IP allocation
    - pihole-srv-1 (PIHOLE_ONE_IP_ADDRESS)
    - pihole-srv-2 (PIHOLE_TWO_IP_ADDRESS)

## LXC creation
- Type: Unprivileged container
- System requirements
    - CPU: 1 core
    - Memory: 512 MB
    - Storage: 2 GB, 4 GB recommended
- Network
    - IPv4: Static
    - Gateway: (ROUTER_IP_ADDRESS)

## OS preparation
```bash
apt update && apt upgrade -y
apt install curl -y
```

## [Installation](https://docs.pi-hole.net/main/basic-install/)
```bash
curl -sSL https://install.pi-hole.net | bash
```

### Installer selections
- Upstream: Google
- Blocklists: Include
- Query logging: Enable
    - Show Everything

### Post-install
- Set pihole password
    ```bash
    pihole setpassword
    ```
- Test web interface accessability
    - http://x.x.x.x/admin

#### [Updating](https://docs.pi-hole.net/main/update/)
```bash
pihole -up
```

#### [Pihole commands](https://docs.pi-hole.net/main/pihole-command/)