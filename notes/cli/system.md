# CLI: System

**Command family:** Health and cleanup  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Engine **info**, **version**, **disk cleanup**, and **remote connections** (SSH/other hosts).

## Main commands

| Command | Purpose |
|---------|---------|
| `podman version` | Client + server (API) versions |
| `podman info` | Store path, registries, security, rootless, … |
| `podman system prune` | Remove unused containers, networks, images (optional `-a`) |
| `podman system df` | Disk usage summary |
| `podman system reset` | **Destructive** — wipe local Podman data |
| `podman system connection list` | Remote endpoints |
| `podman system connection add` | Define remote Podman over SSH |

## Examples

```bash
podman version
podman info
podman system df

# Careful: removes stopped containers, unused networks, dangling images
podman system prune

# Remove all unused images too
podman system prune -a

# Remote (advanced)
podman system connection list
```

## What I learned

- **`info`** is the first debug command for “where is storage?” and “rootless?”.
- **`prune`** is safe-ish for dev; read the prompt before confirming.
- **`system reset`** nukes images/containers on that connection—avoid on shared machines.
- On Mac, `info` reflects the **machine** environment.

## Snippets to keep

```bash
podman info
podman system df
podman system prune
```

## Open questions / next time

- [ ] When to use `system connection` vs default machine
- [ ] `podman system renumber` (legacy migration)

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [machine.md](./machine.md) (Mac/Windows VM)
- [PODMAN_SETUP.md — Verification](../../PODMAN_SETUP.md)
