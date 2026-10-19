# Podman cheatsheet (personal)

Curate this from your [notes](./notes/). Full install and command reference: [PODMAN_SETUP.md](./PODMAN_SETUP.md).

## Mac: before anything else

```bash
podman machine start
podman machine list
```

## Daily commands

_Add rows as you learn._

| Task | Command |
|------|---------|
| Test install | `podman run --rm hello-world` |
| Running containers | `podman ps` |
| All containers | `podman ps -a` |
| Images | `podman images` |
| Logs | `podman logs <name>` |
| Shell in container | `podman exec -it <name> /bin/sh` |
| Stop / remove | `podman stop <name>` · `podman rm <name>` |
| Compose up | `podman compose up -d --build` |
| Compose down | `podman compose down` |
| Prune unused | `podman system prune` |

## Component map

Quick link: [docs/podman-components.md](./docs/podman-components.md).
