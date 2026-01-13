# 4. Hypervisor

Date: 2026-01-07

## Status

Accepted

## Context

The homelab requires hypervisor capable of running multiple services for learning, experimantation and long-term usage.

## Decision

Proxmox VE was selected as the hypervisor platform based on recommendations from many homelabbers as it provides:
- Native support for virtual machines and containers
- Centralized web based management console
- API support for automation and monitoring

## Consequences

- Easy to store services as templates and rebuild them
- Clear separation of services
- Less commonly used in enterprise environments compared to VMware