# Podman (center of the stack)

**Ecosystem role:** Run and manage containers, pods, networks, volumes  
**Index:** [sister-tools.md](../sister-tools.md)

## What it is

**Podman** is the main CLI/engine for **running** OCI containers and related resources on a host (or inside a **machine** VM on Mac/Windows). Pull, push, and build are integrated, but build and registry-heavy workflows often involve **Buildah** and **Skopeo** too.

## Split of responsibilities

| Tool | Mnemonic |
|------|----------|
| **Podman** | **Run** (and manage lifecycle, pods, compose, kube play) |
| [Buildah](./buildah.md) | **Build** images |
| [Skopeo](./skopeo.md) | **Move / inspect** images (especially registry ↔ registry) |
| [podman compose](./podman-compose-official.md) | **Multi-service** from Compose files |

## Where to go in this repo

- Objects: [core-object-types.md](../core-object-types.md)
- CLI families: [podman-cli.md](../podman-cli.md)
- Install: [PODMAN_SETUP.md](../../PODMAN_SETUP.md)

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**
