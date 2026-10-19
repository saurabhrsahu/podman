# registries.conf

**Layer:** Configuration  
**Index:** [config.md](../config.md)  
**Related:** [runtime/containers-image.md](../runtime/containers-image.md)

## Role

Defines how **short image names** resolve and how registries behave:

- **`unqualified-search-registries`** — e.g. `alpine` → `docker.io/library/alpine`
- **Mirrors** — redirect pulls to internal cache
- **Insecure** registries (HTTP or skip TLS)—lab/corporate only

## Typical locations (Linux)

| Scope | Path |
|-------|------|
| System | `/etc/containers/registries.conf` |
| Drop-ins | `/etc/containers/registries.conf.d/` |
| User | `~/.config/containers/registries.conf` |

## Example behavior

```bash
podman pull alpine    # uses unqualified-search-registries order
```

## What I learned

-
- “Wrong registry” or “short name ambiguous” errors start here.
- Corporate mirrors require entries in this file (or drop-ins).

## Open questions / next time

- [ ] Add a mirror entry in a lab VM

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [registries.conf man](https://github.com/containers/image/blob/main/docs/containers-registries.conf.5.md)
