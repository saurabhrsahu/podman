# CLI: Volumes

**Command family:** Storage (named volumes)  
**Related objects:** [Volume](../objects/volume.md) · [Container](../objects/container.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Manage **named volumes** and mount them at **`podman run`** (bind mounts use `-v` too—see [volume object note](../objects/volume.md)).

## Main commands

| Command | Purpose |
|---------|---------|
| `podman volume create` | New named volume |
| `podman volume ls` | List volumes |
| `podman volume inspect` | Mountpoint, labels, timestamps |
| `podman volume rm` | Delete (not if in use) |
| `podman volume prune` | Remove unused volumes |
| `podman run -v NAME:/path` | Mount named volume |

## Examples

```bash
podman volume create pgdata
podman volume ls
podman volume inspect pgdata

podman run -d --name db \
  -v pgdata:/var/lib/postgresql/data \
  docker.io/library/postgres:16-alpine

podman volume rm pgdata
podman volume prune
```

## What I learned

- Volume **name** before colon: `-v pgdata:/data`.
- Bind mount: `-v /host/path:/container/path` (host path rules differ on Mac—document your tries).
- `inspect` shows **Mountpoint** on Linux; useful for backups on Linux hosts.

## Snippets to keep

```bash
podman volume create pgdata
podman run -d -v pgdata:/data myimage
podman volume ls
```

## Open questions / next time

- [ ] `:ro`, `:Z` flags in practice on your OS

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [objects/volume.md](../objects/volume.md)
- [network-commands.md](./network-commands.md)
