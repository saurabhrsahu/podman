# Podman Machine (macOS / Windows)

**Layer:** Platform  
**Index:** [platform.md](../platform.md)  
**Related:** [cli/machine.md](../cli/machine.md)

## Role

On **macOS and Windows**, Podman runs inside a **Linux VM** (often Fedora-based). Your **native CLI** talks to the engine in that VM.

| Part | Where |
|------|--------|
| `podman` CLI | Mac/Windows host |
| Engine, images, containers | Inside **Podman Machine** |

## Typical workflow

```bash
podman machine start
podman machine list
podman run --rm hello-world
```

CLI commands: [cli/machine.md](../cli/machine.md).

## What I learned

-
- Bind mounts and disk paths: host Mac path vs VM path—document in [objects/volume.md](../objects/volume.md).
- Config files ([config/](../config/)) for engine behavior live **in the VM**—use `podman machine ssh` to inspect when debugging.

## Open questions / next time

- [ ] Resize CPU/RAM/disk (stop → rm → init)
- [ ] Rootful machine when permissions bite

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — macOS / Windows](../../PODMAN_SETUP.md)
