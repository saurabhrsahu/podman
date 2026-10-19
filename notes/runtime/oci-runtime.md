# OCI runtime (crun / runc)

**Layer:** Low-level runtime  
**Index:** [runtime.md](../runtime.md)

## Role

The **OCI runtime** starts the container process from an **OCI bundle** (config + rootfs): creates **namespaces** (PID, network, mount, …), **cgroups**, sets user/group, then execs the container entrypoint.

Podman picks a runtime (often **`crun`** on Fedora/modern installs, **`runc`** elsewhere) via [containers.conf](../config/containers-conf.md).

## You rarely call it directly

Podman invokes the runtime; debugging sometimes needs the runtime name from `podman info`.

```bash
podman info | grep -i runtime
podman inspect web --format '{{.OCIConfigPath}}'   # bundle-related paths
```

## crun vs runc

| | **crun** | **runc** |
|--|----------|----------|
| Focus | Fast, low memory | Reference implementation |
| Common on | Fedora, newer Podman defaults | Many distros, older docs |

Both implement the [OCI Runtime Spec](https://github.com/opencontainers/runtime-spec).

## What I learned

-
- Container “isolation” (namespaces, cgroups) happens **here**, not in the Podman CLI.

## Open questions / next time

- [ ] Switch default runtime in `containers.conf` (lab only)
- [ ] `runsc` / other runtimes (gVisor) if mentioned in `info`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [conmon.md](./conmon.md) — runs alongside each container
- [crun](https://github.com/containers/crun) · [runc](https://github.com/opencontainers/runc)
