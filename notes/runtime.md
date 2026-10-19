# Low-level runtime — index

Pieces **behind** the Podman CLI. You rarely invoke them directly; they explain logs, networking, storage, and pull behavior.

| Component | Note | Role |
|-----------|------|------|
| OCI runtime | [runtime/oci-runtime.md](./runtime/oci-runtime.md) | Namespaces, cgroups, run container process (`crun` / `runc`) |
| conmon | [runtime/conmon.md](./runtime/conmon.md) | Per-container monitor, exit status, logging pipes |
| netavark | [runtime/netavark.md](./runtime/netavark.md) | Create/manage networks (modern default) |
| aardvark-dns | [runtime/aardvark-dns.md](./runtime/aardvark-dns.md) | DNS for names on netavark networks |
| CNI plugins | [runtime/cni-plugins.md](./runtime/cni-plugins.md) | Older/alternate networking path |
| containers/storage | [runtime/containers-storage.md](./runtime/containers-storage.md) | Layer store, graph driver, disk layout |
| containers/image | [runtime/containers-image.md](./runtime/containers-image.md) | Pull/push transports (`docker://`, `oci:`, …) |
| Rootless vs rootful | [runtime/rootless-rootful.md](./runtime/rootless-rootful.md) | UID mapping and permissions |

Overview: [docs/podman-components.md](../docs/podman-components.md).

## Flow (simplified)

```text
podman run
  → containers/storage (image layers + RW layer)
  → netavark + aardvark-dns (if custom network / DNS)
  → OCI runtime (crun/runc) starts process
  → conmon monitors + logs
  → containers/image (on pull/push, not each run)
```

## Session log

| Date | Runtime notes read/tried | Dated note link |
|------|--------------------------|-----------------|
| | | |
