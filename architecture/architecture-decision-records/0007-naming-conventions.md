# 7. Naming Conventions

Date: 2026-01-15

## Status

Accepted
Supersede [3. Service naming](0003-service-naming.md)

## Context

As the number of services increases, inconsistent naming makes it difficult to identify their purpose. This complicates troubleshooting, automation and monitoring. A standardized naming convention is required to ensure consistency across all services.

## Decision

Standardize service naming format to the following where applicable:

### Container names

nodeName-serviceName-srv-instanceNumber

Example: `pve-pihole-srv-01`

### Local DNS records

serviceName.domainName.eTLD

Example: `pihole.homelab.lan`

## Consequences

- Services are easier to identify, search and manage
- Naming consistency improves readability and reduces ambiguity
- Some services may impose naming constraints that require deviation from the standard format