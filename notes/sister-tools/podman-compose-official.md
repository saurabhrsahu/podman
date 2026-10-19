# podman compose (official)

**Ecosystem role:** Multi-service stacks via Compose spec  
**Index:** [sister-tools.md](../sister-tools.md)  
**Related:** [cli/compose.md](../cli/compose.md)

## What it is

**`podman compose`** is Podman’s **official** integration for [Compose](https://compose-spec.io/) files (`compose.yaml`, `docker-compose.yaml`). Podman runs containers, networks, and volumes; there is **no separate long-lived Compose daemon** like some Docker setups.

It is a **subcommand of Podman**, not a separate binary named `podman-compose`.

```bash
podman compose up -d
podman compose down
```

## How it fits the stack

```text
compose.yaml  →  podman compose  →  podman (containers, networks, volumes)
```

Same idea as `docker compose`, but the engine is Podman (rootless on Linux, machine VM on Mac).

## Requirements

- Podman version with compose support bundled or via compose provider (check `podman compose version`).
- Compose file v3.x / Compose Specification features—**not every** Docker Compose feature is implemented; note gaps when something fails.

## vs Docker Compose

| Topic | Notes |
|-------|--------|
| Command | `podman compose` (space), not legacy `docker-compose` binary |
| Backend | Podman, not dockerd |
| Desktop | Podman Desktop can manage stacks; CLI is still `podman compose` |

## What I learned

-
- Prefer this over the Python **`podman-compose`** project unless you depend on legacy behavior—see [podman-compose-python.md](./podman-compose-python.md).

## Open questions / next time

- [ ] Feature parity list for a stack you care about
- [ ] `compose watch` / profiles on your Podman version

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [cli/compose.md](../cli/compose.md) — command cheat sheet for this repo
- [podman compose documentation](https://docs.podman.io/en/latest/markdown/podman-compose.1.html)
