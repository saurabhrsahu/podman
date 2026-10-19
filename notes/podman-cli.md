# Podman CLI — index

Command families for the **`podman`** main interface. Each area has its own note under [`cli/`](./cli/).

| Area | Note | Examples | Role |
|------|------|----------|------|
| Run lifecycle | [cli/run-lifecycle.md](./cli/run-lifecycle.md) | `run`, `start`, `stop`, `restart`, `rm`, `pause` | Create and control containers |
| Inspect / logs | [cli/inspect-logs.md](./cli/inspect-logs.md) | `ps`, `logs`, `inspect`, `top`, `stats`, `events` | Observability |
| Exec / attach | [cli/exec-attach.md](./cli/exec-attach.md) | `exec`, `attach`, `cp` | Debug and file copy |
| Images | [cli/images-commands.md](./cli/images-commands.md) | `pull`, `push`, `build`, `images`, `rmi`, `tag`, `load`, `save` | Image workflow |
| Pods | [cli/pod-commands.md](./cli/pod-commands.md) | `pod create`, `pod ps`, `pod start/stop/rm` | Pod lifecycle |
| Volumes | [cli/volume-commands.md](./cli/volume-commands.md) | `volume *` | Named storage |
| Networks | [cli/network-commands.md](./cli/network-commands.md) | `network *` | Connectivity + DNS |
| System | [cli/system.md](./cli/system.md) | `info`, `version`, `system prune`, `system connection` | Health and cleanup |
| Machine | [cli/machine.md](./cli/machine.md) | `machine init/start/stop/ssh` | Local Linux VM (Mac/Win) |
| Kube | [cli/kube.md](./cli/kube.md) | `kube play`, `generate kube` | YAML ↔ pods/containers |
| Compose | [cli/compose.md](./cli/compose.md) | `compose up/down/build` | Multi-service stacks |

Overview: [docs/podman-components.md](../docs/podman-components.md).  
Object types (what commands manage): [core-object-types.md](./core-object-types.md).

## Optional: REST API

On Linux, enabling the **Podman socket** exposes a Docker-compatible HTTP API for tools that expect a daemon. Not required for normal CLI use—document in a dated note if you try it.

## Suggested practice order

1. [Machine](./cli/machine.md) (Mac/Win) → [System](./cli/system.md) (`info`, `version`)  
2. [Images](./cli/images-commands.md) → [Run lifecycle](./cli/run-lifecycle.md)  
3. [Inspect / logs](./cli/inspect-logs.md) → [Exec / attach](./cli/exec-attach.md)  
4. [Volume](./cli/volume-commands.md) + [Network](./cli/network-commands.md) commands  
5. [Compose](./cli/compose.md)  
6. [Pod](./cli/pod-commands.md) + [Kube](./cli/kube.md)

## Session log

| Date | CLI notes practiced | Dated note link |
|------|---------------------|-----------------|
| | | |
