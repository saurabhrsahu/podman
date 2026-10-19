# CLI: Compose

**Command family:** Multi-service stacks (Compose spec)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Run **multiple containers** from a `compose.yaml` (Docker Compose format) using **`podman compose`**—Podman as the backend, not Docker Desktop.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman compose up` | Create/start services |
| `podman compose down` | Stop and remove services/networks |
| `podman compose build` | Build service images |
| `podman compose ps` | Service status |
| `podman compose logs` | Service logs |
| `podman compose exec` | Run command in a service container |
| `podman compose pull` | Pull service images |

Run from directory with `compose.yaml` or `docker-compose.yaml`, or use `-f`.

## Examples

```bash
cd scratch/my-stack   # contains compose.yaml
podman compose up -d --build
podman compose ps
podman compose logs -f api
podman compose exec api sh
podman compose down

podman compose -f compose.yaml -f compose.override.yaml up -d
```

## What I learned

- Prefer **`podman compose`** (official) over legacy **`podman-compose`** (Python)—see [podman-compose-official.md](../sister-tools/podman-compose-official.md) and [podman-compose-python.md](../sister-tools/podman-compose-python.md).
- Service **names** become DNS on the project network → talk `http://db:5432` etc.
- Volumes and networks in YAML map to [volume](../objects/volume.md) / [network](../objects/network.md) objects.
- Some Compose features differ from Docker—note gaps when something fails.

## Snippets to keep

```bash
podman compose up -d --build
podman compose down
podman compose logs -f
```

## Open questions / next time

- [ ] `profiles`, `depends_on`, healthchecks in a real stack
- [ ] Secrets block in compose with Podman

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [network-commands.md](./network-commands.md)
- [Podman compose documentation](https://docs.podman.io/en/latest/markdown/podman-compose.1.html)
