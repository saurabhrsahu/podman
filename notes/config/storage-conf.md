# storage.conf

**Layer:** Configuration  
**Index:** [config.md](../config.md)  
**Related:** [runtime/containers-storage.md](../runtime/containers-storage.md)

## Role

Controls **where** image and container layers live and **how** (storage/graph driver, options).

## Typical locations (Linux)

| Scope | Path |
|-------|------|
| System | `/etc/containers/storage.conf` |
| User | `~/.config/containers/storage.conf` |

Mac/Win: inspect inside **Podman machine**.

## Key ideas

| Setting area | Effect |
|--------------|--------|
| `graphroot` | Root directory for layer store |
| `driver` | e.g. `overlay` |
| `runroot` | Temporary runtime state |

## What to check

```bash
podman info | grep -i -A10 store
podman system df
```

## What I learned

-
- “Disk full” on Mac often = **machine disk** size, not only macOS free space.

## Open questions / next time

- [ ] `graphroot` path via `podman machine ssh`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [storage.conf man page](https://github.com/containers/storage/blob/main/docs/containers-storage.conf.5.md)
