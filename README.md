# Podman learning repo

Personal notes and reference for learning [Podman](https://podman.io/)—containers, images, compose, and the wider containers ecosystem.

## Start here

| Doc | Purpose |
|-----|---------|
| [PODMAN_SETUP.md](./PODMAN_SETUP.md) | Install Podman (Windows, Linux, macOS), verify, basic CLI, troubleshooting |
| [docs/podman-components.md](./docs/podman-components.md) | What Podman is made of: objects, CLI, Buildah/Skopeo, runtime, networking, config |
| [docs/learning-notes-guide.md](./docs/learning-notes-guide.md) | How to use this repo as learning notes (templates, rhythm, index) |
| [cheatsheet.md](./cheatsheet.md) | Short list of commands you actually use (curate as you learn) |

## Notes index

Add links here as you write notes (newest first):

- [Core object types (index)](notes/core-object-types.md)
  - [Image](notes/objects/image.md) · [Container](notes/objects/container.md) · [Pod](notes/objects/pod.md) · [Volume](notes/objects/volume.md) · [Network](notes/objects/network.md) · [Secret](notes/objects/secret.md) · [Manifest](notes/objects/manifest.md)
- [Podman CLI (index)](notes/podman-cli.md)
  - [Run lifecycle](notes/cli/run-lifecycle.md) · [Inspect / logs](notes/cli/inspect-logs.md) · [Exec / attach](notes/cli/exec-attach.md) · [Images](notes/cli/images-commands.md) · [Pods](notes/cli/pod-commands.md) · [Volumes](notes/cli/volume-commands.md) · [Networks](notes/cli/network-commands.md) · [System](notes/cli/system.md) · [Machine](notes/cli/machine.md) · [Kube](notes/cli/kube.md) · [Compose](notes/cli/compose.md)
- [Sister tools (index)](notes/sister-tools.md)
  - [Podman](notes/sister-tools/podman.md) · [Buildah](notes/sister-tools/buildah.md) · [Skopeo](notes/sister-tools/skopeo.md) · [podman compose](notes/sister-tools/podman-compose-official.md) · [podman-compose (Python)](notes/sister-tools/podman-compose-python.md)
- [Runtime (index)](notes/runtime.md)
  - [OCI runtime](notes/runtime/oci-runtime.md) · [conmon](notes/runtime/conmon.md) · [netavark](notes/runtime/netavark.md) · [aardvark-dns](notes/runtime/aardvark-dns.md) · [CNI](notes/runtime/cni-plugins.md) · [containers/storage](notes/runtime/containers-storage.md) · [containers/image](notes/runtime/containers-image.md) · [Rootless vs rootful](notes/runtime/rootless-rootful.md)
- [Platform (index)](notes/platform.md)
  - [Podman Machine](notes/platform/podman-machine-platform.md) · [Linux host](notes/platform/linux-host.md) · [Podman Desktop](notes/platform/podman-desktop.md)
- [Config & policy (index)](notes/config.md)
  - [containers.conf](notes/config/containers-conf.md) · [storage.conf](notes/config/storage-conf.md) · [registries.conf](notes/config/registries-conf.md) · [policy.json](notes/config/policy-json.md) · [auth.json](notes/config/auth-json.md)

<!-- Dated notes:
- [2026-10-18 First machine](notes/2026-10-18-first-machine-and-hello-world.md)
-->

Copy [notes/_template.md](./notes/_template.md) for new dated notes.

## Topics checklist

Tick mentally or in a note when you’ve tried each area:

- [ ] Machine & CLI (Mac/Windows: `podman machine`; Linux: rootless)
- [ ] Images (pull, tag, build)
- [ ] Container lifecycle (`run`, logs, `exec`, restart)
- [ ] Volumes (named vs bind mounts; Mac + VM)
- [ ] Networking (ports, DNS between containers)
- [ ] Compose (`podman compose`)
- [ ] Pods & kube (`pod`, `generate kube`, `kube play`)
- [ ] Registry (login, push, Skopeo-style workflows)
- [ ] Security (non-root in image, secrets, rootless on Linux)
- [ ] Ops extras (Quadlet, auto-update — mainly Linux)

## Scratch

Throwaway experiments live in [`scratch/`](./scratch/). Link each experiment from a note in `notes/`; the note is the artifact worth keeping.
