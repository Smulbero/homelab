# 5. Local DNS

Date: 2026-01-15

## Status

Accepted

## Context

Initially services in the homelab were accessed directly using IP addresses and ports. As number of services and IP addresses grew it became inconvenient for day-to-day use. 

DNS-based solution was required to:
- Provide network wide DNS resolution
- Support both LAN and VPN clients
- Avoid external DNS providers where possible

## Decision

Pi-hole was selected as primary DNS service for this homelab as it provides:
- Built-in DNS based ad blocking
- Native support for local DNS records

To avoid reliance on third party DNS providers, Unbound is used as local recursive resolver. DNS queries are forwarded to Unbound, which resolves requests directly from authoritative DNS servers.

## Consequences

- Network wide ad blocking
- Local DNS resolution for internal services
- Improved privacy by avoiding public DNS providers
- Increased operational complexity
- DNS availability depends on internal services 