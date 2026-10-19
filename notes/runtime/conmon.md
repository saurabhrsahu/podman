# conmon

**Layer:** Low-level runtime  
**Index:** [runtime.md](../runtime.md)

## Role

**conmon** (container monitor) is a **short-lived helper process per container**. It:

- Tracks the container’s main process **exit status**
- Handles **logging pipes** (stdout/stderr → log driver)
- Supports **attach** and some lifecycle signaling

One conmon per container—not a cluster-wide daemon like `dockerd`.

## You rarely call it directly

Visible when debugging “who owns this container’s logs?” or inspecting process trees.

```bash
# While a container runs — process tree (Linux / inside machine VM)
podman top web -eo pid,comm,args
# Look for conmon + runtime + your app
```

## What I learned

-
- Explains why Podman can be **daemonless** yet still have a small monitor per container.
- Log follow (`podman logs -f`) ultimately ties back to conmon’s pipe handling.

## Open questions / next time

- [ ] conmon vs journald logging driver on Linux

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [oci-runtime.md](./oci-runtime.md)
- [conmon GitHub](https://github.com/containers/conmon)
