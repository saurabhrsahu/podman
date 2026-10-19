# containers.conf

**Layer:** Configuration  
**Index:** [config.md](../config.md)

## Role

Main **engine defaults**: OCI runtime choice, network backend (netavark vs CNI), cgroup mode, events, engine flags, and many `[containers]` / `[engine]` tunables.

## Typical locations (Linux)

| Scope | Path |
|-------|------|
| System | `/etc/containers/containers.conf` |
| User override | `~/.config/containers/containers.conf` |

On **Mac/Windows**, effective files are inside the **Podman machine** (`podman machine ssh` → same paths on the guest).

Drop-in fragments may live under `containers.conf.d/`.

## When it matters

- Default **runtime** (`crun` vs `runc`)
- **Network backend** — ties to [netavark](../runtime/netavark.md) vs [CNI](../runtime/cni-plugins.md)
- Global defaults you did not pass on `podman run`

## What to check

```bash
podman info
man containers.conf    # Linux / in machine ssh
```

## What I learned

-
- Prefer **user** `~/.config/containers/` overrides over editing `/etc` when learning.

## Open questions / next time

- [ ] Copy relevant `[engine]` section from `podman info` into a dated note

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [containers/common containers.conf](https://github.com/containers/common/blob/main/docs/containers.conf.5.md)
