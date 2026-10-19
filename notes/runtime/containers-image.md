# containers/image

**Layer:** Pull, push, transports  
**Index:** [runtime.md](../runtime.md)  
**Related:** [cli/images-commands.md](../cli/images-commands.md) · [sister-tools/skopeo.md](../sister-tools/skopeo.md) · [config/registries-conf.md](../config/registries-conf.md)

## Role

**containers/image** implements **pull/push/copy** logic and **transport** types:

| Transport | Meaning |
|-----------|---------|
| `docker://` | Registry (Docker Registry HTTP API) |
| `oci:` | OCI layout on disk |
| `dir:` | Directory tree |
| `containers-storage:` | Local Podman/Buildah store |

`podman pull` / `push` and **Skopeo** `copy`/`inspect` build on this stack.

## What you see at CLI level

```bash
podman pull docker.io/library/alpine:latest
podman push localhost/myapp:1.0 docker.io/myuser/myapp:1.0
```

Short names (`alpine`) resolved via [registries.conf](../config/registries-conf.md).

## vs Skopeo

| | **podman pull/push** | **Skopeo copy** |
|--|----------------------|-----------------|
| Typical use | Dev laptop run images | Registry mirroring, inspect-only |
| Library | containers/image | containers/image |

## What I learned

-
- Pull errors often = registry config + [auth.json](../config/auth-json.md) + network, not the runtime.

## Open questions / next time

- [ ] Pull with `--tls-verify=false` (dev only) vs proper CA trust

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [containers/image GitHub](https://github.com/containers/image)
