# netavark

**Layer:** Networking  
**Index:** [runtime.md](../runtime.md)  
**Related:** [objects/network.md](../objects/network.md) · [aardvark-dns.md](./aardvark-dns.md)

## Role

**netavark** creates and manages **container networks** on many modern Podman installs—bridges, firewall rules, container interface setup. Replaces or supersedes **CNI-only** paths for default networking in rootful/rootless setups (version/distro dependent).

User-facing commands stay **`podman network *`**; netavark works behind `podman network create` and default bridge behavior.

## What to check

```bash
podman info | grep -i network
podman network inspect podman
```

## vs CNI

| | **netavark** | **CNI plugins** |
|--|--------------|-----------------|
| Era | Newer default on many installs | Older docs, some custom setups |
| DNS | Works with [aardvark-dns](./aardvark-dns.md) | Often `dnsname` plugin |

See [cni-plugins.md](./cni-plugins.md) if your docs mention CNI.

## What I learned

-
- Custom networks from [network-commands.md](../cli/network-commands.md) are implemented by this stack on netavark systems.

## Open questions / next time

- [ ] `network_backend` in `containers.conf`

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [netavark GitHub](https://github.com/containers/netavark)
