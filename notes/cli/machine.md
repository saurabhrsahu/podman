# CLI: Machine (macOS / Windows)

**Command family:** Local Linux VM  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

On **Mac and Windows**, Podman runs inside a **Linux VM**. The `machine` subcommands create, start, and manage that VM. Linux hosts skip this family.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman machine init` | Create VM (cpus, memory, disk) |
| `podman machine start` | Boot VM |
| `podman machine stop` | Shut down VM |
| `podman machine list` | Status of machines |
| `podman machine ssh` | Shell into the VM |
| `podman machine rm` | Delete VM |
| `podman machine info` | VM details |
| `podman machine set` | e.g. `--rootful` |

## Examples

```bash
podman machine list
podman machine start

# First-time setup (example sizing)
podman machine init --cpus 4 --memory 4096 --disk-size 100
podman machine start

podman machine ssh -- uname -a
podman machine stop
```

## What I learned

- **`machine start`** before any `run`/`build` on Mac/Win.
- Resource changes often need **stop → rm → init** (see PODMAN_SETUP.md).
- Files/bind mounts: paths can be confusing between Mac host and VM—log what works in [volume object note](../objects/volume.md).
- Podman Desktop can manage the same machine graphically.

## Snippets to keep

```bash
podman machine start
podman machine list
```

## Open questions / next time

- [ ] SSH vs default connection for troubleshooting
- [ ] Rootful machine when permissions bite

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — macOS / Windows machine](../../PODMAN_SETUP.md)
- [system.md](./system.md)
