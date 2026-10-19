# Rootless vs rootful

**Layer:** Identity and permissions (uses same runtime stack)  
**Index:** [runtime.md](../runtime.md)  
**Related:** [platform/linux-host.md](../platform/linux-host.md) · [platform/podman-machine-platform.md](../platform/podman-machine-platform.md)

## Role

Same low-level pieces ([OCI runtime](./oci-runtime.md), [netavark](./netavark.md), [storage](./containers-storage.md)); different **UID/GID mapping** and **capabilities**:

| Mode | Who runs containers on Linux |
|------|------------------------------|
| **Rootless** | Your user; **subuid/subgid** map IDs inside containers |
| **Rootful** | Root on host |

On **Mac/Windows**, the engine runs in the **machine VM**; rootless vs rootful is configured on that guest (`podman machine set --rootful`).

## Linux checks

```bash
podman info | grep -i rootless
grep ^$(whoami): /etc/subuid /etc/subgid
```

## What I learned

-
- Rootless is the recommended dev default on Linux; permission errors on bind mounts often trace here.
- Mac users still hit permission/path issues via the VM layer—not the same as Linux rootless docs.

## Open questions / next time

- [ ] `--userns=keep-id` behavior on your version

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — Linux post-install rootless](../../PODMAN_SETUP.md)
