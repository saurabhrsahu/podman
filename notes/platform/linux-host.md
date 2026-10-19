# Linux host (no Machine)

**Layer:** Platform  
**Index:** [platform.md](../platform.md)

## Role

On **Linux**, Podman runs **on the host**—no Podman Machine VM. Engine, storage, and networks are direct on the distro.

| Topic | Notes |
|-------|--------|
| Default | **Rootless** Podman as your user |
| Setup | `subuid`/`subgid`, user namespaces — [PODMAN_SETUP.md](../../PODMAN_SETUP.md) |
| Optional | **Podman socket** for Docker API compatibility |

## Docker API socket (optional)

```bash
systemctl --user enable --now podman.socket
export DOCKER_HOST=unix:///run/user/$UID/podman/podman.sock
```

Tools that expect `dockerd` may work; not required for normal CLI.

## What I learned

-
- [runtime/rootless-rootful.md](../runtime/rootless-rootful.md) matters most on Linux.
- Paths in [config/](../config/) are on the real host under `/etc/containers/` and `~/.config/containers/`.

## Open questions / next time

- [ ] SELinux `:Z` on bind mounts (Fedora/RHEL)

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — Linux installation](../../PODMAN_SETUP.md)
