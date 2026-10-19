# Image

**Component:** Image  
**See also:** [Container](./container.md) · [Manifest](./manifest.md) · [Index](../core-object-types.md)

## What it is

Read-only **template**: stacked **layers** plus **metadata** (default env, entrypoint, exposed ports, labels). An image is not a running process—you **run** it to get a [container](./container.md).

| Idea | Detail |
|------|--------|
| Source | `podman pull` from a registry, or `podman build` from a Containerfile |
| Identity | `registry/repo:tag` (e.g. `docker.io/library/nginx:latest`) or image ID |
| Writable data | Only appears when you create a **container** from the image |

## Commands

```bash
podman pull docker.io/library/alpine:latest
podman images
podman image inspect docker.io/library/alpine:latest
podman rmi alpine:latest          # remove if no container uses it
podman build -t myapp:dev -f Containerfile .
podman tag myapp:dev localhost/myapp:1.0
podman save -o myapp.tar myapp:dev
podman load -i myapp.tar
```

## What I learned

- `podman run` creates a **new container**; the image stays read-only.
- `:latest` is just a tag—pin versions in real projects.
- `podman images -a` can show intermediate build layers.
- Multi-arch tags use a [manifest](./manifest.md) behind the scenes on registries.

## Snippets to keep

```bash
podman pull docker.io/library/alpine:latest
podman images
podman build -t myapp:dev .
```

## Open questions / next time

- [ ] Where on disk? (`podman info` → store; on Mac, inside the Podman machine VM.)
- [ ] Difference between `rmi` and `image prune`

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [PODMAN_SETUP.md — Image operations](../../PODMAN_SETUP.md)
