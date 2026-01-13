# 3. Service naming

Date: 2026-01-07

## Status

Accepted

## Context

As the number of services increases, inconsistent naming makes it difficult to identify their purpose. This complicates troubleshooting, automation and monitoring. A standardized naming convention is required to ensure consistency across all services.

## Decision

Standardize service naming format to the following where applicable:

[nodeName]-[serviceName]-[instanceNumber]

Example: `pve-pihole-01`

## Consequences

- Services are easier to identify, search and manage
- Naming consistency improves readability and reduces ambiguity
- Some services may impose naming constraints that require deviation from the standard format
