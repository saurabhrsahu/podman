# Learning notes guide

This repo is a **learning notebook**: you document what you ran, what broke, and what you understood—not a formal course with numbered lesson folders.

## How the pieces fit

| Path | Role |
|------|------|
| [PODMAN_SETUP.md](../PODMAN_SETUP.md) | Stable reference: install, verify, command tables, troubleshooting |
| [docs/podman-components.md](./podman-components.md) | Map of Podman architecture and ecosystem |
| [notes/core-object-types.md](../notes/core-object-types.md) | One note per resource under `notes/objects/` |
| [notes/podman-cli.md](../notes/podman-cli.md) | One note per CLI family under `notes/cli/` |
| [notes/sister-tools.md](../notes/sister-tools.md) | Buildah, Skopeo, Compose tools under `notes/sister-tools/` |
| [notes/runtime.md](../notes/runtime.md) | Low-level runtime under `notes/runtime/` |
| [notes/platform.md](../notes/platform.md) | Mac/Win/Linux/Desktop under `notes/platform/` |
| [notes/config.md](../notes/config.md) | Config files under `notes/config/` |
| [notes/](../notes/) | Your dated and topic notes |
| [cheatsheet.md](../cheatsheet.md) | Commands you actually reuse (curate weekly) |
| [scratch/](../scratch/) | Optional throwaway Containerfiles, compose snippets |

**Rule:** Generic facts from upstream docs → setup doc or components doc. Something that happened **to you** on a given day → a note.

---

## Two note types

| Type | When | Filename example |
|------|------|------------------|
| **Dated** | First attempt or a debugging session | `2026-10-18-first-machine-and-hello-world.md` |
| **Topic** | Theme you revisit and append | `volumes.md`, `compose.md` |

Start with **dated** notes. When one theme gets long (several compose notes), merge into a **topic** note and link from the README index.

Copy [notes/_template.md](../notes/_template.md) for each new note.

---

## Weekly rhythm (low effort)

1. **Do one small thing** (15–30 min): run a container, build an image, add a second service in compose.
2. **Write one dated note** (~10 min) with the template—even if the session failed.
3. **Once a week**, move repeated commands into [cheatsheet.md](../cheatsheet.md) and add a link under **Notes index** in [README.md](../README.md).

---

## Suggested first topics (checklist)

Use the checklist in [README.md](../README.md). Suggested order is flexible; follow whatever you need for a real project.

| Order | Topic | Example note title |
|-------|--------|-------------------|
| 1 | Machine & CLI | `first-machine-and-hello-world` |
| 2 | Run flags, logs, exec | `nginx-ports-and-exec` |
| 3 | Build | `first-containerfile-build` |
| 4 | Volumes on Mac | `volumes-on-mac` |
| 5 | Compose | `compose-app-and-db` |

After that, notes follow **your** project, not a fixed syllabus.

---

## Scratch directory policy

- Put one-off `Containerfile`, `compose.yaml`, or tiny apps in `scratch/`.
- In the note, link to the scratch path: *See `scratch/2026-10-22-build/`.*
- Delete scratch freely; **the note is what you keep**.
- To keep git clean, you can add `scratch/*` to `.gitignore` and only commit when a snippet is worth sharing—or commit scratch folders that match a note.

---

## Podman-specific “aha” lines worth capturing

When they happen, write a sentence in a note:

- **Daemonless** on Linux vs **Podman Machine** on Mac/Windows.
- **`podman compose`** vs legacy **podman-compose** (Python).
- **Rootless** on Linux vs engine inside the VM on Mac.
- **Volume and bind-mount paths on Mac**—data lives in the machine VM unless you know what you mounted.
- **`docker` alias / socket compatibility**—when it helps vs when it confuses.
- **Pods**—shared network; bridge toward Kubernetes (`generate kube`).

Component names for tagging: see [podman-components.md](./podman-components.md#learning-notes-which-component-did-i-touch).
