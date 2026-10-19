# Configuration & policy — index

Not separate binaries—**files** that change pull, storage, runtime, and auth behavior.

| File / concept | Note | What it controls |
|----------------|------|------------------|
| containers.conf | [config/containers-conf.md](./config/containers-conf.md) | Engine defaults: runtime, network backend, cgroups, flags |
| storage.conf | [config/storage-conf.md](./config/storage-conf.md) | Graph root, storage driver |
| registries.conf | [config/registries-conf.md](./config/registries-conf.md) | Short names, mirrors, insecure registries |
| policy.json | [config/policy-json.md](./config/policy-json.md) | Image signature verification |
| auth.json | [config/auth-json.md](./config/auth-json.md) | `podman login` credentials |

## Where files live

| OS | Where to look |
|----|----------------|
| Linux | `/etc/containers/` and `~/.config/containers/` |
| macOS / Windows | Same paths **inside Podman machine** — `podman machine ssh` |

Start debugging with:

```bash
podman info
```

Overview: [docs/podman-components.md](../docs/podman-components.md).

## Session log

| Date | Config files inspected | Dated note link |
|------|------------------------|-----------------|
| | | |
