# podman-compose (Python, third-party)

**Ecosystem role:** Legacy Compose runner — **not** official  
**Index:** [sister-tools.md](../sister-tools.md)  
**Related:** [podman-compose-official.md](./podman-compose-official.md) · [cli/compose.md](../cli/compose.md)

## What it is

**podman-compose** is a **separate open-source project** (historically **Python**) that reads Compose files and invokes **`podman`** commands. It is **not** the same as:

```bash
podman compose   # official: subcommand built into Podman
```

```bash
podman-compose   # third-party: often a standalone script/entry point
```

Names differ by one hyphen vs a space—easy to confuse in docs and tutorials.

## Comparison

| | **`podman compose`** (official) | **podman-compose** (Python) |
|--|--------------------------------|-----------------------------|
| Maintainer | Podman / Red Hat ecosystem | Community project |
| Install | With Podman | `pip install podman-compose`, package managers, etc. |
| Invoke | `podman compose up` | `podman-compose up` |
| Default choice | **Yes** for new work | Only if you already rely on it |

## When you might still see podman-compose

- Old blog posts, courses, or repos that say `podman-compose` explicitly.
- Environments where someone standardized on the Python tool before `podman compose` matured.

## Migration hint

Replace:

```bash
podman-compose up -d
```

With:

```bash
podman compose up -d
```

Re-test volumes, networks, and `depends_on`—fix compose file or Podman version if behavior differs.

## What I learned

-
- Check which tool a tutorial uses: **`podman compose -h`** vs **`podman-compose --help`**.

## Open questions / next time

- [ ] Diff a failing legacy repo after switching to `podman compose`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [podman-compose on GitHub](https://github.com/containers/podman-compose)
- [podman-compose-official.md](./podman-compose-official.md)
