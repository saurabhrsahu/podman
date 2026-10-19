# containers/storage

**Layer:** Image and container disk layout  
**Index:** [runtime.md](../runtime.md)  
**Related:** [objects/image.md](../objects/image.md) · [objects/volume.md](../objects/volume.md) · [config/storage-conf.md](../config/storage-conf.md)

## Role

**containers/storage** is the library Podman/Buildah use for the **local store**:

- Image **layers** (shared between images)
- Container **read-write** layer on top of an image
- **Graph driver** / storage driver options (overlay, etc.)

Configured mainly via [storage.conf](../config/storage-conf.md).

## What to check

```bash
podman info | grep -i -A5 store
podman system df
```

On **Mac**, the store lives **inside the Podman machine VM**, not directly on macOS paths—explains “where did my disk go?”

## What I learned

-
- Removing containers/images frees store space; [volumes](../objects/volume.md) are separate objects but also have backing storage.
- `podman system prune` vs `volume prune` hit different parts of the store.

## Open questions / next time

- [ ] `podman machine ssh` → inspect graph root on Mac
- [ ] Storage driver `overlay` vs `vfs` (lab)

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [containers/storage GitHub](https://github.com/containers/storage)
