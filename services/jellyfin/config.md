# Configuration

Jellyfin requires access to persistent media library that is stored outside of the container filesystem.

In this homelab, the media library is currently stored on the Proxmox host and mounted into the Jellyfin container. <br>
This is a temporary solution until a dedicated storage solution is introduced.

## Media library

- Host path `/media`
- Container path `/media`
- Mount type: Bind mount
- Access mode: Read-only

Media is stored outside of the container to:
- Persist independently of the container lifecycle
- Allow container recreation without data migration
- Simplify future storage changes

### Container configuration

The `/media` directory is mounted into the container via Proxmox LXC configuration.

This can be configured in one of two ways:

#### Edit container configuration file 

Edit the container configuration file on the Proxmox host: <br>
`/etc/pve/nodes/<PVE_NODE_NAME>/lxc/<CONTAINER_ID>.conf`

```bash
# Add a mount point entry:
mp0: <HOST_DIRECTORY_PATH>,mp=<CONTAINER_DIRECTORY_PATH>,ro=1
```

#### Use `pct`

Apply the mount using the Proxmox CLI:

```bash
pct set <CONTAINER_ID> -mp0 /media,mp=/media,ro=1
```