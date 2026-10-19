# CLI: Pods

**Command family:** Pod lifecycle  
**Related objects:** [Pod](../objects/pod.md) · [Container](../objects/container.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Create a **pod** (shared network namespace), add containers with `--pod`, start/stop/remove the group.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman pod create` | New empty pod (optional `-p` ports) |
| `podman pod ps` | List pods |
| `podman pod start` / `stop` / `restart` | Pod-level lifecycle |
| `podman pod rm` | Remove pod (containers must be handled per flags) |
| `podman pod inspect` | Pod JSON |
| `podman pod logs` | Logs from pod infra / containers (version-dependent) |
| `podman run --pod NAME` | Run container inside pod |

## Examples

```bash
podman pod create --name app-pod -p 8080:80
podman run -d --pod app-pod --name web nginx:alpine
podman run -d --pod app-pod --name sidecar busybox sleep 3600

podman pod ps
podman pod inspect app-pod
podman pod stop app-pod
podman pod rm -f app-pod
```

## What I learned

- Publish ports on **pod create** when containers share the pod network.
- Stopping the pod stops member containers (typical workflow).
- Use with [kube commands](./kube.md): `generate kube`, `kube play`.

## Snippets to keep

```bash
podman pod create --name app-pod -p 8080:80
podman run -d --pod app-pod --name web nginx:alpine
podman pod ps
```

## Open questions / next time

- [ ] `pod rm` vs removing containers first
- [ ] Infra container in pod (automatic vs explicit)

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [objects/pod.md](../objects/pod.md)
- [PODMAN_SETUP.md — Pod operations](../../PODMAN_SETUP.md)
