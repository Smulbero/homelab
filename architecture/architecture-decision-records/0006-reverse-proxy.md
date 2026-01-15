# 6. Reverse Proxy

Date: 2026-01-15

## Status

Accepted

## Context

As local DNS records are introduced, a way to route incoming HTTP requests to the correct services is needed. Many services run on non-standard ports, making direct access inconvenient.

The solution should:
- Allow clean URLs without port numbers
- Remain internal only
- Centralize access to internal services

## Decision

Nging Proxy Manager (NPM) was selected as the internal reverse proxy as it provides:
- Simple web based configuration panel
- Built-in support for SSL certificates if required later

Pi-hole local DNS records point service hostnames to the reverse proxy IP address, which then routes incoming HTTP requests to the correct backend service based on IP address and port.

## Consequences

- Memorable service URLs without port numbers
- Simplified service access
- Service access becomes dependent of reverse proxy
- Increased operational complexity