# Skopeo

**Ecosystem role:** Move and inspect images without running containers  
**Index:** [sister-tools.md](../sister-tools.md)  
**Related:** [objects/image.md](../objects/image.md) · [objects/manifest.md](../objects/manifest.md) · [cli/images-commands.md](../cli/images-commands.md)

## What it is

**Skopeo** operates on **container images** in registries and local storage **without** starting a workload container on the host. Copy between registries, inspect manifests, sync air-gapped mirrors, sign and verify.

Podman **`pull` / `push`** overlap for day-to-day use; Skopeo shines for **registry ↔ registry** copies and **manifest-list** work where you never need `run`.

## Typical jobs

| Job | Skopeo angle |
|-----|----------------|
| Mirror images to internal registry | `skopeo copy docker://... docker://...` |
| Inspect remote tag/digest | `skopeo inspect docker://registry/repo:tag` |
| Copy only multi-arch manifest list | `copy` with `--all` |
| Delete remote tag | `skopeo delete` (permissions required) |
| Sign / verify | `skopeo copy` with signing policy |

## Examples

```bash
# Inspect remote image (no pull into podman yet)
skopeo inspect docker://docker.io/library/alpine:latest

# Copy image into local storage (containers-storage:)
skopeo copy docker://docker.io/library/alpine:latest \
  containers-storage:localhost/alpine:mirrored

# Registry to registry (no local run)
skopeo copy docker://docker.io/library/alpine:latest \
  docker://registry.example.com/mirror/alpine:latest

# Copy all architectures in a manifest list
skopeo copy --all docker://docker.io/library/alpine:latest \
  docker://registry.example.com/mirror/alpine:latest
```

## vs Podman

| Task | Podman | Skopeo |
|------|--------|--------|
| Dev laptop: pull and run | `podman pull`, `podman run` | Overkill |
| CI mirror 500 images overnight | Possible with pull/tag/push | **`copy`** is the usual tool |
| Check if tag exists before deploy | `podman pull` (heavy) | **`inspect`** (light) |

## What I learned

-
- Transport prefixes: `docker://`, `containers-storage:`, `dir:`, `oci:`.

## Open questions / next time

- [ ] Install Skopeo on Mac (`brew install skopeo`) and retry examples
- [ ] Signing policy with `policy.json`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [Skopeo GitHub](https://github.com/containers/skopeo)
- [Skopeo man pages](https://github.com/containers/skopeo/blob/main/docs/skopeo.1.md)
