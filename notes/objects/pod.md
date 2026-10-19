# Pod

**Component:** Pod  
**See also:** [Container](./container.md) · [Network](./network.md) · [Index](../core-object-types.md)

## What it is

A **group of [containers](./container.md)** on one host that share a **network namespace** (same IP stack; `localhost` between them). Optionally share other namespaces (e.g. IPC). Like one Kubernetes Pod—not a full cluster.

| Idea | Detail |
|------|--------|
| Why use it | Sidecars, app + helper on localhost, `generate kube` |
| vs Compose | Compose = services; pod = lower-level grouping |
| Ports | Often published on the **pod** (`pod create -p`) |

## Commands

```bash
podman pod create --name app-pod -p 8080:80
podman run -d --pod app-pod --name frontend docker.io/library/nginx:alpine
podman run -d --pod app-pod --name sidecar docker.io/library/busybox sleep 3600
podman pod ps
podman pod inspect app-pod
podman pod stop app-pod
podman pod rm -f app-pod

# Kubernetes YAML bridge
podman generate kube app-pod > scratch/app-pod.yaml
```

## What I learned

- Port mapping on the pod feeds the **shared** network namespace.
- Containers in a pod are designed around that shared network—not the same as arbitrary multi-network standalone containers.
- `podman generate kube` exports pod + containers for learning K8s shapes.

## Snippets to keep

```bash
podman pod create --name app-pod -p 8080:80
podman run -d --pod app-pod --name frontend nginx:alpine
podman pod ps
```

## Open questions / next time

- [ ] Pod vs single container vs compose-only stack
- [ ] `kube play` the generated YAML

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [PODMAN_SETUP.md — Pod operations](../../PODMAN_SETUP.md)
