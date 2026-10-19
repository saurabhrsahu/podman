# Volume

**Component:** Volume  
**See also:** [Container](./container.md) · [Index](../core-object-types.md)

## What it is

**Named persistent storage** managed by Podman. Survives [container](./container.md) removal until you delete the volume. Different from a **bind mount** (host path → container path).

| Type | What it is |
|------|------------|
| **Named volume** | `podman volume create`; lives in Podman storage (Mac: inside machine VM) |
| **Bind mount** | `-v /host/path:/container/path` — you manage the host path |

## Commands

```bash
# Named volume
podman volume create pgdata
podman volume ls
podman volume inspect pgdata
podman run -d --name db \
  -v pgdata:/var/lib/postgresql/data \
  docker.io/library/postgres:16-alpine
podman run --rm -v pgdata:/data:ro alpine ls -la /data
podman volume rm pgdata    # fails if in use

# Bind mount (repo scratch/)
mkdir -p scratch/html
echo '<h1>hi</h1>' > scratch/html/index.html
podman run -d --name web -p 8080:80 \
  -v $(pwd)/scratch/html:/usr/share/nginx/html:ro \
  docker.io/library/nginx:alpine
```

## What I learned

- Data on a **volume** outlives the container; data only in the container layer is **lost** on `rm`.
- On **macOS**, bind-mount paths are often relative to the **Podman machine**—note what works on your setup.
- `:ro` read-only; `:Z` / `:z` for SELinux on Linux.

## Snippets to keep

```bash
podman volume create pgdata
podman run -d -v pgdata:/data myimage
podman volume ls
```

## Open questions / next time

- [ ] Backup/restore a named volume
- [ ] `podman volume prune`

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [PODMAN_SETUP.md — Volume operations](../../PODMAN_SETUP.md)
