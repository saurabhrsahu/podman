# CLI: Inspect / logs

**Command family:** Observability  
**Related objects:** [Container](../objects/container.md) · [Pod](../objects/pod.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

See **what is running**, **what happened** (logs), and **low-level config** (inspect, events, resource use).

## Main commands

| Command | Purpose |
|---------|---------|
| `podman ps` | List running containers |
| `podman ps -a` | All containers |
| `podman logs` | Stdout/stderr from container |
| `podman inspect` | JSON config/state (container, image, network, …) |
| `podman top` | Processes inside container |
| `podman stats` | Live CPU/memory (like top for containers) |
| `podman events` | Stream lifecycle events |
| `podman port` | Show port mappings |
| `podman diff` | Changed files vs image |

Pod variants: `podman pod ps`, `podman pod inspect`, `podman pod logs`.

## Examples

```bash
podman ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
podman logs -f --tail 50 web
podman inspect web --format '{{.NetworkSettings.IPAddress}}'
podman top web
podman stats --no-stream
podman events --since 10m
```

## What I learned

- `logs -f` follows; `--tail N` limits history.
- `inspect` accepts Go templates with `--format` for scripts.
- `ps` filters: `--filter status=exited`, `--filter name=web`.
- `events` useful for debugging automation and restarts.

## Snippets to keep

```bash
podman ps -a
podman logs -f web
podman inspect web
```

## Open questions / next time

- [ ] `journald` logging driver on Linux
- [ ] Filter syntax for `events`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — Basic commands](../../PODMAN_SETUP.md)
