# NAS Configuration

This document describes the NAS configuration used in the homelab.

---

## Table of Contents

- [Install Packages](#install-packages)
- [NFS Configuration](#nfs-configuration)
- [Proxmox Configuration](#proxmox-configuration)
- [Passing Storage Into an LXC](#passing-storage-into-an-lxc)
- [Samba (Windows Share)](#samba-windows-share)
- [Storage Permissions](#storage-permissions)
- [Cockpit](#cockpit)
- [Useful Commands](#useful-commands)
- [References](#references)

---

## Install Packages

### Update the System

```bash
sudo apt update
sudo apt upgrade
```

### Install Required Packages

```bash
sudo apt install \
    cockpit \
    cockpit-storaged \
    nfs-kernel-server \
    samba \
    smartmontools \
```

---

## NFS Configuration

### Create Network Share

Edit:

```
/etc/exports
```

Add the following line:

```text
/<local-storage-path> <lan-address-space/cidr>(rw,sync,no_subtree_check)
```

### Reload exports:

```bash
sudo exportfs -ra
```

### Restart NFS:

```bash
sudo systemctl restart nfs-kernel-server
```

### Verify exports:

```bash
sudo exportfs -v
```

---

## Proxmox Configuration

### Install NFS client (if required)

```bash
apt install nfs-common
```

### Create mount point

```bash
mkdir -p /mnt/<mount-path>
```

### Mount manually

```bash
mount -t nfs <nas-ip-address>:/<storage-path> /mnt/<mount-path>
```

### Verify

```bash
findmnt /mnt/<mount-path>
```

### Persistent mount

Recommended:

Configure the NAS as NFS Storage through the Proxmox Datacenter -> Storage menu.

Alternatively add an `/etc/fstab` entry.

```text
<nas-ip-address>:/<storage-path> <mount-point-on-proxmox> nfs defaults,_netdev,x-systemd.automount,nofail
```

Options used:

- `defaults` - Standard mount options
- `_netdev` - Wait until networking is available before mounting
- `x-systemd.automount` - Mount on first access instead of during boot
- `nofail` - Continue boot even if the NAS is unavailable

---

## Passing Storage Into an LXC

### Container Configuration

Edit the container configuration file on the Proxmox host
`/etc/pve/nodes/<pve-node-name>/lxc/<container-id>.conf`

Example:

```
mp0: /mnt/NAS/,mp=/mnt/NAS/,ro=0
```

Restart container

---

## Samba (Windows Share)

### Create Linux user

```bash
sudo adduser <username>
```

### Add Samba password

```bash
sudo smbpasswd -a <username>
```

### Samba Configuration

Edit the configuration file
`/etc/samba/smb.conf`

Add the following:

```ini
# Example
[storage]
    path = /storage
    browseable = yes
    writable = yes
    valid users = <username>
```

Restart Samba

```bash
sudo systemctl restart smbd
```

### Verify

```bash
sudo testparm
```

### Add the File Share on Windows

Open Explorer and add a network location:

```
\\<nas-ip-address>\<path-to-storage>
```

Login using Linux username and Samba password

---

## Storage Permissions

### Set Ownership

```bash
sudo chown -R <username>:<username> <storage-path>
```

### Set Permissions

```bash
sudo chmod -R 775 <storage-path>
```

---

## Cockpit

Cockpit is the primary web-based administration interface for the NAS.

### Features Overview

Displays real-time system information, including:

- CPU utilization
- Memory usage
- Disk activity
- Network traffic
- System uptime
- Operating system version

Provides management layer for:

- Storage (cockpit-storaged)
- Networking
- Services
- Logs
- Accounts
- Terminal

### Enable Cockpit:

```bash
sudo systemctl enable --now cockpit.socket
```

### Cockpit Web UI:

```
https://<nas-ip-address>:9090
```

Log in using a local Linux user account

---

## Useful Commands

### Show exported NFS shares

```bash
showmount -e <nas-ip-address>
```

### Restart NFS

```bash
sudo systemctl restart nfs-kernel-server
```

### Restart Samba

```bash
sudo systemctl restart smbd
```

### Verify mounted shares

```bash
findmnt
```

### List Samba configuration

```bash
testparm -s
```

---

## References

- [Cockpit](https://cockpit-project.org/documentation.html)
- [Debian NFS](https://wiki.debian.org/NFS)
- [Samba](https://wiki.samba.org/)
- [Proxmox Storage](https://pve.proxmox.com/pve-docs/)