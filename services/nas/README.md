# NAS

A lightweight NAS built on Debian for use with the Proxmox homelab.

---

## Purpose

This NAS provides:

- NFS storage for Proxmox
- SMB (Samba) shares for Windows
- Central storage for Jellyfin media
- Web-based management through Cockpit
- Disk health monitoring

---

## Hardware

- Spare PC
- Single storage disk
- Static IP reserved from the router

## Installed Packages

- cockpit
- cockpit-storaged
- nfs-kernel-server
- samba
- smartmontools
- avahi-daemon