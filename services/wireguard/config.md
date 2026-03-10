# Configuration

Reference documentation: <br>
https://www.wireguard.com/quickstart/#quick-start

## Server side setup

### Interface setup

```bash
# Create new network interface
ip link add dev wg0 type wireguard

# Assign ip to the interface
ip address add dev wg0 [vpn_interface_ip_address]

# Activate the interface
ip link set up dev wg0
```

### Key generation

```bash
# Change default file permissions
umask 077

# Generate new private key
wg genkey > privatekey

# Generate the public key from the private key
wg pubkey < privatekey > publickey
```

### Setup a peer with a client

This part requires public key from the client

```bash
# Get listening port
wg

# Setup a peer
wg set wg0 peer [client_public_key] allowed-ips [client_interface_ip_address/32] endpoint [server_ip_address:wireguad_port]
```

## Client side setup

### Setup a peer with a server

#### Linux client

##### Interface setup

```bash
# Create new network interface
ip link add dev wg0 type wireguard

# Assign ip to the interface
ip address add dev wg0 [client_interface_ip_address]

# Activate the interface
ip link set up dev wg0
```

```bash
# Get listening port
wg

# Setup a peer
wg set wg0 peer [server_public_key] allowed-ips [vpn_interface_ip_address/32] endpoint [public_ip_address:wireguard_port]
```