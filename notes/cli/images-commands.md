# CLI: Images

**Command family:** Image workflow  
**Related objects:** [Image](../objects/image.md) · [Manifest](../objects/manifest.md)  
**Index:** [podman-cli.md](../podman-cli.md)

## Role

Get images from **registries** or **builds**, list/tag them, move tarballs, push to registries.

## Main commands

| Command | Purpose |
|---------|---------|
| `podman pull` | Download from registry |
| `podman push` | Upload to registry |
| `podman build` | Build from Containerfile/Dockerfile (Buildah) |
| `podman images` | List local images |
| `podman rmi` | Remove image(s) |
| `podman tag` | Add another name:tag to same image ID |
| `podman load` | Import from tar |
| `podman save` | Export to tar |
| `podman login` / `logout` | Registry auth |
| `podman image prune` | Remove unused images |

## Examples

```bash
podman pull docker.io/library/alpine:latest
podman images
podman build -t myapp:dev -f Containerfile .
podman tag myapp:dev localhost/myapp:1.0
podman save -o scratch/myapp.tar myapp:dev
podman rmi myapp:dev
podman load -i scratch/myapp.tar

podman login docker.io
podman push localhost/myapp:1.0 docker.io/myuser/myapp:1.0
```

## What I learned

- `build -t name:tag` tags the result; `.` is build context directory.
- `rmi` fails if a container still references the image.
- `pull` uses `registries.conf` for short names (e.g. `alpine` → docker.io).
- `push` needs `login` and correct tag prefix matching the registry.

## Snippets to keep

```bash
podman pull alpine:latest
podman build -t myapp:dev .
podman images
```

## Open questions / next time

- [ ] `--platform` on pull/build (multi-arch)
- [ ] `build --target` multi-stage

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [objects/image.md](../objects/image.md)
- [PODMAN_SETUP.md — Image operations](../../PODMAN_SETUP.md)
