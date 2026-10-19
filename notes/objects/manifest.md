# Manifest / image index

**Component:** Manifest  
**See also:** [Image](./image.md) · [Index](../core-object-types.md)

## What it is

A **meta-image** on a registry: points to **multiple platform-specific [images](./image.md)** (amd64, arm64, …) or related digests. When you `podman pull` a multi-arch tag, the client resolves the right manifest for your CPU.

| Idea | Detail |
|------|--------|
| Multi-arch | One tag → manifest **list** → per-arch images |
| Pinning | `@sha256:digest...` pins exact content; tags can move |
| Advanced | `podman manifest create/push` to publish multi-arch lists |

## Commands

```bash
podman pull docker.io/library/alpine:latest
podman inspect docker.io/library/alpine:latest | grep -i arch
podman images --digests

# Pull by digest (example shape)
# podman pull docker.io/library/alpine@sha256:<digest>

# Remote manifest inspect (when available for the reference)
podman manifest inspect docker.io/library/alpine:latest
```

## What I learned

- Your local `podman images` shows the **image you pulled**, not the whole index tree.
- Building multi-arch: build per platform, assemble with **`podman manifest create`**, push—often with Buildah/Skopeo in the loop.
- **Skopeo** copies manifest lists between registries without running a container.

## Snippets to keep

```bash
podman pull alpine:latest
podman images --digests
podman inspect alpine:latest
```

## Open questions / next time

- [ ] Pull by digest in a deploy script
- [ ] Create and push a small multi-arch manifest

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [Skopeo](https://github.com/containers/skopeo)
- [docs/podman-components.md — Sister tools](../../docs/podman-components.md)
