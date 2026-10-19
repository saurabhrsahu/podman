# CLI: Kube

**Command family:** YAML ↔ pods/containers  
**Related objects:** [Pod](../objects/pod.md) · [Container](../objects/container.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

**Export** running pods/containers to Kubernetes-style YAML, or **apply** YAML locally with Podman (not a full cluster).

## Main commands

| Command | Purpose |
|---------|---------|
| `podman generate kube` | Write YAML from pod/container |
| `podman kube play` | Create pods/containers from YAML |
| `podman kube down` | Tear down resources from YAML |
| `podman kube generate` | (alias / related — check `podman kube --help` on your version) |

## Examples

```bash
# Export existing pod
podman pod create --name demo -p 8080:80
podman run -d --pod demo nginx:alpine
podman generate kube demo > scratch/demo-kube.yaml

# Apply YAML
podman kube play scratch/demo-kube.yaml
podman kube down scratch/demo-kube.yaml
```

## What I learned

- Good **learning bridge** to Kubernetes object shapes (Pod, Service-like ports).
- Not every K8s field is supported—expect to simplify real cluster YAML.
- Pairs with [pod commands](./pod-commands.md) and [compose](./compose.md) as three ways to run multi-unit apps.

## Snippets to keep

```bash
podman generate kube mypod > scratch/mypod.yaml
podman kube play scratch/mypod.yaml
```

## Open questions / next time

- [ ] `kube play` with ConfigMap/Secret in YAML
- [ ] Diff generated YAML vs hand-written K8s

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [objects/pod.md](../objects/pod.md)
- [Podman kube documentation](https://docs.podman.io/en/latest/markdown/podman-kube.1.html)
