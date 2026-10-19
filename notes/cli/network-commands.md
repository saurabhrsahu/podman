# CLI: Networks

**Command family:** Connectivity  
**Related objects:** [Network](../objects/network.md) · [Container](../objects/container.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Create **user-defined networks**, attach containers, get **DNS by name** on that network.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman network create` | New network |
| `podman network ls` | List networks |
| `podman network inspect` | Subnets, plugins, connected containers |
| `podman network rm` | Remove unused network |
| `podman network prune` | Remove unused networks |
| `podman run --network NAME` | Attach container to network |
| `podman network connect` / `disconnect` | Add/remove running container from network |

## Examples

```bash
podman network create app-net
podman network ls
podman run -d --name api --network app-net nginx:alpine
podman run -d --name client --network app-net alpine sleep 3600
podman exec client wget -qO- http://api/

podman network inspect app-net
podman network rm app-net
```

## What I learned

- **`--network`** on `run` is the usual attach point.
- Default **bridge** vs custom **app-net** affects DNS isolation.
- `-p` publishes to host; internal traffic uses container names on shared network.
- [Compose](./compose.md) creates networks automatically from the compose file.

## Snippets to keep

```bash
podman network create app-net
podman run -d --name api --network app-net nginx:alpine
```

## Open questions / next time

- [ ] `--network host` on Mac vs Linux
- [ ] Multiple networks on one container

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [objects/network.md](../objects/network.md)
- [volume-commands.md](./volume-commands.md)
