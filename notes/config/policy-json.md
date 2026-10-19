# policy.json

**Layer:** Configuration / policy  
**Index:** [config.md](../config.md)

## Role

**Signature verification policy** for images: which transports/registries require signed images, reject rules, etc. Used on pull/copy when signature checking is enabled.

## Typical location (Linux)

| Path |
|------|
| `/etc/containers/policy.json` |

User-level policy is less common; enterprise images often lock this at system level.

## When you hit it

- Pull fails with **signature** or **policy** errors
- Registries requiring **signed** containers (OpenShift-style workflows)

## What to check

```bash
cat /etc/containers/policy.json   # Linux or machine ssh
podman pull --help | grep -i sign
```

## What I learned

-
- Default on many laptops: permissive `insecureAcceptAnything` for docker transport in dev—**do not assume** that in production.

## Open questions / next time

- [ ] Relationship to `sigstore` / cosign in your Podman version

## What I ran (session log)

**Date:**  
**Context:**

```bash

```

**What happened:**

## Links

- [containers/image policy.json](https://github.com/containers/image/blob/main/docs/policy.json.md)
