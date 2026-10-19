# Buildah

**Ecosystem role:** Build OCI images  
**Index:** [sister-tools.md](../sister-tools.md)  
**Related:** [objects/image.md](../objects/image.md) · [cli/images-commands.md](../cli/images-commands.md)

## What it is

**Buildah** builds **OCI-compliant images** from a **Containerfile** or **Dockerfile**. It focuses on image construction—not on running long-lived app containers like Podman.

Podman delegates image builds to Buildah: **`podman build`** is Buildah under the hood. You can also install and use **`buildah`** directly when you want finer control or scripting without the full Podman CLI surface.

## Why it exists (vs classic Docker build)

| Idea | Detail |
|------|--------|
| No “builder daemon” | Fits the daemonless containers stack |
| Scriptable | `buildah bud`, `buildah from`, `buildah run`, `buildah commit` for step-by-step images |
| Rootless builds | Common on Linux with mapped UIDs |
| Same output | OCI images Podman runs |

## When to use which

| Use | Tool |
|-----|------|
| Everyday “build my app image” | `podman build -t myapp .` |
| Learning how images are assembled layer by layer | `buildah` commands |
| CI scripts that only build, never run | Often `buildah` or `podman build` |

## Buildah CLI (common)

```bash
# Similar to podman build
buildah bud -t myapp:dev -f Containerfile .

# Interactive / manual workflow (learning)
buildah from alpine
# → prints working container name, e.g. alpine-working-container
buildah run alpine-working-container -- dnf install -y httpd
buildah commit alpine-working-container myhttpd:local
buildah rm alpine-working-container

buildah images
```

## Podman equivalent

```bash
podman build -t myapp:dev -f Containerfile .
```

## What I learned

-
- Multi-stage builds work in Containerfile for both `podman build` and `buildah bud`.

## Open questions / next time

- [ ] `buildah --layers` / cache behavior vs `podman build`
- [ ] `buildah manifest` and multi-arch with Buildah-only workflow

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [Buildah GitHub](https://github.com/containers/buildah)
- [Buildah tutorial](https://github.com/containers/buildah/blob/main/docs/tutorials/README.md)
