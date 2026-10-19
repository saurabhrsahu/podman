# Sister tools — index

Red Hat’s **containers** stack splits work across tools. Podman is the hub; these sit beside it (not always one binary).

**Mnemonic:** **Podman** = run · **Buildah** = build · **Skopeo** = move/inspect images

| Tool | Note | Purpose |
|------|------|---------|
| **Podman** | [sister-tools/podman.md](./sister-tools/podman.md) | Run/manage containers, pods, networks, volumes; integrated pull/push/build |
| **Buildah** | [sister-tools/buildah.md](./sister-tools/buildah.md) | Build OCI images; `podman build` uses Buildah |
| **Skopeo** | [sister-tools/skopeo.md](./sister-tools/skopeo.md) | Copy, inspect, delete, sign images without running a workload container |
| **podman compose** | [sister-tools/podman-compose-official.md](./sister-tools/podman-compose-official.md) | Official Compose integration (`podman compose`) |
| **podman-compose** | [sister-tools/podman-compose-python.md](./sister-tools/podman-compose-python.md) | Older Python third-party; **not** the same as `podman compose` |

Overview: [docs/podman-components.md](../docs/podman-components.md).

## How they connect

```text
                    ┌─────────────┐
                    │   Skopeo    │  registry ↔ registry, inspect
                    └──────┬──────┘
                           │
┌─────────────┐     ┌──────▼──────┐     ┌──────────────────┐
│   Buildah   │────►│   Podman    │◄────│  podman compose  │
│ build image │     │ run / manage│     │  (compose.yaml)  │
└─────────────┘     └─────────────┘     └──────────────────┘
       ▲                    │
       │                    │
   podman build              │
   (same engine)             ▼
                      containers, pods,
                      volumes, networks
```

## Suggested learning order

1. [Podman](./sister-tools/podman.md) — run + [CLI notes](./podman-cli.md)  
2. [Buildah](./sister-tools/buildah.md) — after `podman build`  
3. [podman compose](./sister-tools/podman-compose-official.md) — multi-service  
4. [Skopeo](./sister-tools/skopeo.md) — when pull/push isn’t enough  
5. [podman-compose Python](./sister-tools/podman-compose-python.md) — read-only unless you hit legacy repos  

## Session log

| Date | Tools practiced | Dated note link |
|------|-----------------|-----------------|
| | | |
