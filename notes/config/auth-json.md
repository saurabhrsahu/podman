# auth.json

**Layer:** Configuration / credentials  
**Index:** [config.md](../config.md)  
**Related:** [cli/images-commands.md](../cli/images-commands.md)

## Role

Stores **registry credentials** from **`podman login`**. Used on **push** and **private pull**.

## Typical locations

| Context | Path |
|---------|------|
| Rootless user | `~/.config/containers/auth.json` |
| Root | `/run/containers/0/auth.json` or root config tree (varies) |

On Mac, file is usually **inside the machine** user home when you `podman login` from CLI connected to machine.

## Commands

```bash
podman login docker.io
podman login registry.example.com
podman logout docker.io
```

**Do not commit** `auth.json` to git.

## What I learned

-
- Login is per-registry host key in JSON; wrong registry URL in tag vs login host breaks push.
- Credential helpers / Docker `config.json` migration—note if you use `docker login` alias.

## Open questions / next time

- [ ] `auth.json` path via `podman machine ssh` on Mac

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md](../../PODMAN_SETUP.md)
