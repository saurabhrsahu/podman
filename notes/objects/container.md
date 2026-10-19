# Container

**Component:** Container  
**See also:** [Image](./image.md) · [Volume](./volume.md) · [Network](./network.md) · [Secret](./secret.md) · [Pod](./pod.md) · [Index](../core-object-types.md)

## What it is

A **runnable instance**: an [image](./image.md) plus **runtime config**—command, env, port maps, mounts, network, labels, restart policy. Can be **running** or **stopped** until you `rm` it.

| Idea | Detail |
|------|--------|
| Lifecycle | create → start → stop → start again → rm |
| Ephemeral vs named | `--rm` deletes on exit; `--name` keeps for reuse |
| State | Writable layer; filesystem changes lost on `rm` unless on a [volume](./volume.md) |

## Commands

```bash
podman run -d --name web -p 8080:80 docker.io/library/nginx:alpine
podman ps                    # running
podman ps -a                 # all
podman logs -f web
podman exec -it web /bin/sh
podman stop web && podman start web
podman inspect web
podman update --restart unless-stopped web
podman rm -f web
podman container prune       # remove stopped containers
```

## What I learned

- `run` = create + start (most common).
- `-p 8080:80` is **host:container** (on Mac, host is your Mac via the machine).
- Stopped containers still use disk until removed.
- Standalone containers join [networks](./network.md); pod members use [pod](./pod.md) networking.

## Snippets to keep

```bash
podman run -d --name web -p 8080:80 nginx:alpine
podman logs -f web
podman exec -it web /bin/sh
```

## Open questions / next time

- [ ] `--restart unless-stopped` vs `always`
- [ ] `create` + `start` vs single `run`

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [PODMAN_SETUP.md — Container operations](../../PODMAN_SETUP.md)
