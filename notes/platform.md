# Platform-specific components — index

Where Podman **runs** depends on your OS.

| Platform | Note | Extra component |
|----------|------|-----------------|
| macOS / Windows | [platform/podman-machine-platform.md](./platform/podman-machine-platform.md) | **Podman Machine** — Linux VM; CLI native, engine in VM |
| Linux | [platform/linux-host.md](./platform/linux-host.md) | No machine; optional **user socket** for Docker API |
| All (optional) | [platform/podman-desktop.md](./platform/podman-desktop.md) | **Podman Desktop** — GUI |

Overview: [docs/podman-components.md](../docs/podman-components.md).

## Typical flows

```text
Mac/Win:  podman machine start  →  podman run ...
Linux:    podman run ...        (rootless user session)
Any:      Podman Desktop  →  same backend as CLI
```

## Session log

| Date | Platform notes | Dated note link |
|------|----------------|-----------------|
| | | |
