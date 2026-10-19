# Core object types — index

Podman manages these **resources**. Each has its own note under [`objects/`](./objects/).

| Component | Note | One line |
|-----------|------|----------|
| **Image** | [objects/image.md](./objects/image.md) | Read-only template (layers + metadata) |
| **Container** | [objects/container.md](./objects/container.md) | Running or stopped instance of an image + config |
| **Pod** | [objects/pod.md](./objects/pod.md) | Containers sharing a network namespace |
| **Volume** | [objects/volume.md](./objects/volume.md) | Named persistent storage |
| **Network** | [objects/network.md](./objects/network.md) | Virtual network + DNS between containers |
| **Secret** | [objects/secret.md](./objects/secret.md) | Runtime sensitive blob, not in the image |
| **Manifest** | [objects/manifest.md](./objects/manifest.md) | Multi-arch / image index on registries |

Architecture overview: [docs/podman-components.md](../docs/podman-components.md).

## How the types relate

```text
Registry ──pull──► Image ──run──► Container
                      │              │
                      │              ├── Network
                      │              ├── Volume
                      │              └── Secret
                      │
                      └── Manifest (multi-arch on registry)

Pod = several Containers sharing one network namespace
```

## Suggested hands-on order

1. [Image](./objects/image.md) + [Container](./objects/container.md)  
2. [Volume](./objects/volume.md)  
3. [Network](./objects/network.md)  
4. [Pod](./objects/pod.md)  
5. [Secret](./objects/secret.md)  
6. [Manifest](./objects/manifest.md) (read-only inspect)

After each note, fill **What I ran** in that file or add a dated note from [\_template.md](./_template.md).

## Session log

| Date | Notes touched | Dated note link |
|------|---------------|-----------------|
| | | |
