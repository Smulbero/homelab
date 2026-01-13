# 2. IP addressing

Date: 2026-01-07

## Status

Accepted

## Context

The environment is expected to grow and have multiple workloads for different use cases. Defining IP addressing strategy is critical in order for network expansion not becoming prone to errors or risking overlapping addresses. Address space must be planned to support scalability and isolation in the future.

## Decision

- Allocate /24 address space for LAN Network
- Divide services into 32 usable address segments
- 32 address range enables to use /27 subnet in the future

### IP addressing

- LAN Network: 192.168.0.0/24
- Subnet Mask: 255.255.255.0
- 253 usable host addresses per subnet (excluding network, gateway and broadcast addresses)

### IP ranges

| Range                    | Purpose                |
| :-                       | :-                     |
| 192.168.0.0 - 31         | Network infrastructure |
| 192.168.0.32 - 63        | Applications           |
| 192.168.0.64 - 95        | Monitoring             |
| 192.168.0.96 - 127       | Reserved               |
| 192.168.0.128 - 159      | Reserved               |
| 192.168.0.160 - 191      | Datastore              |
| 192.168.0.192 - 223      | VPN clients            |
| 192.168.0.224 - 255      | End user devices       |

### IP assigments

Device and service assignments are stored in Google Sheets.

## Consequences

- Clear boundaries of different services
- Address segmeting supports vlan configuration
