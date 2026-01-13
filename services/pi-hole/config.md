# Configuration

## Unbound

Reference documentation: <br>
https://docs.pi-hole.net/guides/dns/unbound/

Unbound is a local, validating, recursive DNS resolver used as the sole upstream DNS provider for Pi-hole.

In this setup, Pi-hole forwards DNS queries to Unbound instead of external DNS services (e.g. Google or Cloudflare). Unbound resolves queries directly by contacting authoritative DNS servers keeping DNS resolution fully within the local infrastructure.

This approach improves privacy, security and control over DNS resolution.

### Installation and Setup
Unbound installation and baseline configuration follow the official Pi-hole [documentation](https://docs.pi-hole.net/guides/dns/unbound/#setting-up-pi-hole-as-a-recursive-dns-server-solution) <br>

### Local configuration

Homelab specific configuration is maintained locally: <br>
/etc/unbound/unbound.conf.d/pi-hole.conf

The version used in this homelab is stored in this repository for reproducibility: <br>
./unbound/pi-hole.conf