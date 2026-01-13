# Pi-hole

## Overview
Pi-hole provides network wide DNS based ad blocking and DNS filtering. <br> 
It acst as the primary DNS resolver for LAN and VPN connected clients. <br>
<br>
Two Pi-hole instances are deployed to eliminate single point of failure and provide redundancy.

## Goals
- Network wide ad blocking
- High availability
- Minimal resource usage

## Deployment
- Platform: Proxmox
- Virtualization: LXC containers
- Instances:
    - pihole-srv-1 (PIHOLE_ONE_IP_ADDRESS)
    - pihole-srv-2 (PIHOLE_TWO_IP_ADDRESS)

## Failure behavior
- In case of instance failure, clients fall back to secondary instance
- In case of Proxmox server failure, DNS resolving stops working