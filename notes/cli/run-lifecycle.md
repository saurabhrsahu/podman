# CLI: Run lifecycle

**Command family:** Create and control containers  
**Related objects:** [Container](../objects/container.md) · [Image](../objects/image.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Create containers from images and move them through **running → stopped → removed**. Most day-to-day work starts with `run`.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman run` | Create + start a container |
| `podman start` | Start an existing stopped container |
| `podman stop` | Graceful stop (SIGTERM, then SIGKILL) |
| `podman restart` | Stop + start |
| `podman rm` | Remove container (must be stopped unless `-f`) |
| `podman pause` / `unpause` | Freeze / resume processes (Cgroups freezer) |
| `podman create` | Create without starting (advanced) |
| `podman kill` | Send signal (default SIGKILL) |

## Examples

```bash
# Foreground (rm when exit)
podman run --rm -it alpine sh

# Detached, named, port map
podman run -d --name web -p 8080:80 docker.io/library/nginx:alpine

# Lifecycle
podman stop web
podman start web
podman restart web
podman rm -f web

# Restart policy
podman run -d --name web --restart unless-stopped nginx:alpine
```

## What I learned

- `run` = `create` + `start` in one step.
- `--rm` avoids leftover stopped containers during experiments.
- `-d` detached; without it, logs attach to your terminal.
- Stopped containers keep disk until `rm` or `container prune`.

## Snippets to keep

```bash
podman run -d --name web -p 8080:80 nginx:alpine
podman stop web && podman rm web
```

## Open questions / next time

- [ ] `stop -t` timeout behavior
- [ ] `podman update` for restart policy on existing container

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — Container operations](../../PODMAN_SETUP.md)
