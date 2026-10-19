# aardvark-dns

**Layer:** Networking / DNS  
**Index:** [runtime.md](../runtime.md)  
**Related:** [netavark.md](./netavark.md) · [objects/network.md](../objects/network.md)

## Role

**aardvark-dns** provides **DNS name resolution** for containers on **netavark-managed** networks—so `http://api` or `http://mycontainer` works between containers on the same user-defined network.

Podman does not require you to run a separate `aardvark-dns` command; it is started/managed as part of the networking stack when needed.

## What you observe (CLI level)

```bash
podman network create app-net
podman run -d --name api --network app-net nginx:alpine
podman run -d --name client --network app-net alpine sleep 3600
podman exec client wget -qO- http://api/
```

If name resolution fails, debug network backend ([netavark](./netavark.md)) and that both containers share **`app-net`**.

## What I learned

-
- Compose service names use the same **name → IP** idea on the project network.

## Open questions / next time

- [ ] `/etc/resolv.conf` inside container vs host forwarding

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [aardvark-dns GitHub](https://github.com/containers/aardvark-dns)
