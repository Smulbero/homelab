# WireGuard Configuration

This document describes the WireGuard VPN configuration used in the homelab.

## Table of Contents

- [Configuration Files](#configuration-files)
- [Server Configuration](#server-configuration)
- [Client Configuration](#client-configuration)
- [Key Generation](#key-generation)
- [WireGuard Commands](#wireguard-commands)
- [WireGuard Service](#wireguard-service)
- [Router Configuration](#router-configuration)
- [References](#references)

---

## Configuration Files

WireGuard stores interface configurations in:

```bash
/etc/WireGuard/wg0.conf
```

---

## Server Configuration

For private and public keys, see [key generation](#key-generation)

### Interface Setup

Setup WireGuard server interface in `wg0.conf` file:

```ini
[Interface]
PrivateKey = <wg-server-private-key>
ListenPort = <wg-listening-port> # E.g. 51000
Address = <wg-tunnel-ip-address/cidr>
```

### Peer Clients

Setup peer in `wg0.conf` file:

```ini
# Each client gets their own peer block
[Peer]
PublicKey = <wg-client-public-key>
AllowedIPs = <wg-client-ip-address/32>
```

### iptables / NAT

Modify firewall rules to allow routing from VPN to LAN.

The following command enables NAT (masquerading) so that traffic from the WireGuard network can reach the LAN. The rule is temporary and is removed when the system is rebooted.

```bash
sudo iptables -t nat -A POSTROUTING \
    -s <wg-network-address-space/cidr> \
    -o <interface-id-connected-to-lan> # E.g eth0 \
    -j MASQUERADE
```

#### Verify the Rule

```bash
sudo iptables -t nat -L -n -v
```

The output should contain a 'MASQUERADE' rule.

#### Make the Rule Persistent

Install the persistence package:

```bash
sudo apt install iptables-persistent
```

During installation, choose **Yes** when asked whether to save the current IPv4 rules.

If the package was installed before the rule was created, save the current rules manually:

```bash
sudo netfilter-persistent save
```

---

## Client Configuration

For private and public keys, see [key generation](#key-generation)

### Interface Setup

Setup WireGuard client interface in `wg0.conf` file:

```ini
[Interface]
PrivateKey = <wg-client-private-key>
Address = <client-ip-address/cidr>
DNS = <pihole-lan-ip-address>
```

### Peer Server

Setup peer in `wg0.conf` file:

```ini
[Peer]
PublicKey = <wg-server-public-key>
Endpoint = <home-network-public-ip>:<wg-listening-port>
AllowedIPs = <home-network-address-space>, <wg-network-address-space>
PersistentKeepalive = 25 # Optional
```

---

## Key Generation

```bash
# Change default file permissions
umask 077

# Generate new private key
wg genkey > privatekey

# Generate the public key from the private key
wg pubkey < privatekey > publickey
```

---

## WireGuard Commands

### Bring interface up

```bash
sudo wg-quick up wg0
```

### Bring interface down

```bash
sudo wg-quick down wg0
```

### Restart interface

```bash
sudo wg-quick down wg0
sudo wg-quick up wg0
```

---

## WireGuard Service

### Enable WireGuard at boot:

```bash
sudo systemctl enable wg-quick@wg0
```

### Start immediately:

```bash
sudo systemctl start wg-quick@wg0
```

### Verify:

```bash
systemctl status wg-quick@wg0
```

---

## Router Configuration

### Port Forward

| Protocol    | External Port           | Internal IP       | Internal Port           |
|:-           |:-                       |:-                 |:-                       |
| UDP         | `<wg-listening-port>`   | `<wg-host-ip>`    | `<wg-listening-port>`   |

---

## Troubleshooting

### Traffic doens't flow from VPN network to LAN

Verify the following:

- NAT (MASQUERADE) rule exists
- Client `AllowedIPs` includes the LAN subnet

Useful commands:

```bash
sudo wg
sudo iptables -t nat -L -n -v
```

If the NAT rule is missing, see [iptables / NAT](#iptables--nat).

---
## References

- [WireGuard Official Documentation](https://www.wireguard.com/)
- [WireGuard Quick Start](https://www.wireguard.com/quickstart/)
- [wg-quick Manual](https://man7.org/linux/man-pages/man8/wg-quick.8.html)
- [wg Manual](https://man7.org/linux/man-pages/man8/wg.8.html)