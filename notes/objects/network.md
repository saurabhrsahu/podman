# Network

**Component:** Network  
**See also:** [Container](./container.md) · [Pod](./pod.md) · [Index](../core-object-types.md)

## What it is

A **virtual network**. [Containers](./container.md) (or [pods](./pod.md)) **join** a network, get an IP, and usually **DNS names** for each other—via **netavark** + **aardvark-dns** on modern Podman.

| Idea | Detail |
|------|--------|
| Default | Default network on simple `run`; Compose creates project networks |
| DNS | Container name → IP on user-defined networks |
| Isolation | Separate networks = no direct L2 unless you connect them |

## Commands

```bash
podman network create app-net
podman network ls
podman network inspect app-net
podman run -d --name api --network app-net docker.io/library/nginx:alpine
podman run -d --name client --network app-net alpine sleep 3600
podman exec client wget -qO- http://api/
podman network rm app-net    # after containers gone

# Cleanup unused networks
podman network prune
```

## What I learned

- `-p` publishes ports to the **host**; containers can talk internally without `-p`.
- **`--network host`** (Linux): container uses host stack; behavior on Mac differs—try and document.
- Compose service names act as DNS on the compose network.

## Snippets to keep

```bash
podman network create app-net
podman run -d --name api --network app-net nginx:alpine
podman exec client wget -qO- http://api/
```

## Open questions / next time

- [ ] `network prune` vs manual `network rm`
- [ ] Connect one container to multiple networks

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [docs/podman-components.md — netavark / aardvark-dns](../../docs/podman-components.md)
