# Service manual installation

This document is not applicable at the time of writing since deployment is done by using Proxmox VE Helper script.

## Installation

Proxmox VE Helper script: <br>
https://community-scripts.github.io/ProxmoxVE/scripts?id=nginxproxymanager

```bash
# Subject to change
# Reference Proxmox VE Helper script page
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/nginxproxymanager.sh)"
```

### Post-install

- Verify web UI accessability
    - npm.srv.ip:81
    