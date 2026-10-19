# CLI: Exec / attach

**Command family:** Debug and file copy  
**Related objects:** [Container](../objects/container.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Get **inside** a running container (`exec`, `attach`) or move **files** between host and container (`cp`).

## Main commands

| Command | Purpose |
|---------|---------|
| `podman exec` | Run a command in a **running** container |
| `podman attach` | Attach to container’s main process stdin/stdout |
| `podman cp` | Copy files/folders host ↔ container |

## Examples

```bash
# Interactive shell (common debug path)
podman exec -it web /bin/sh

# One-off command
podman exec web nginx -t

# Attach to PID 1 (careful: Ctrl+C may stop container depending on flags)
podman attach web

# Copy
podman cp web:/etc/nginx/nginx.conf scratch/nginx.conf
podman cp scratch/index.html web:/usr/share/nginx/html/
```

## What I learned

- Prefer **`exec`** for debugging; **`attach`** binds to the original process.
- `exec -it` needs a shell in the image (`/bin/sh`, `/bin/bash`).
- `cp` works on stopped containers in many cases; paths are container:path and host:path.
- On Mac, “host” for `cp` is relative to where the CLI runs (your Mac); container paths are inside the container.

## Snippets to keep

```bash
podman exec -it web /bin/sh
podman cp web:/path/in/container ./scratch/
```

## Open questions / next time

- [ ] `exec --user` for permission debugging
- [ ] `attach --sig-proxy` behavior

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [PODMAN_SETUP.md — exec](../../PODMAN_SETUP.md)
