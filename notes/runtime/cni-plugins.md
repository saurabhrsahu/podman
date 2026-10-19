# CNI plugins

**Layer:** Networking (legacy / alternate)  
**Index:** [runtime.md](../runtime.md)  
**Related:** [netavark.md](./netavark.md)

## Role

**CNI** (Container Network Interface) **plugins** configure container network interfaces—bridge, vlan, firewall, port mapping—in a plugin chain. Older Podman and many tutorials reference **CNI** paths and config under `/etc/cni/net.d/`.

On newer installs, **netavark** is often the default; CNI remains relevant when:

- Docs or distros still set `network_backend = "cni"`
- You inherit cluster-style CNI configs
- You troubleshoot older machines

## What to check

```bash
podman info | grep -i -E 'network|cni|netavark'
ls /etc/cni/net.d/ 2>/dev/null    # Linux or podman machine ssh
```

## What I learned

-
- “Network broken after upgrade” sometimes = switch from CNI to netavark (or the reverse)—check release notes.

## Open questions / next time

- [ ] Custom CNI config vs `podman network create`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [CNI spec](https://github.com/containernetworking/cni)
- [netavark.md](./netavark.md)
