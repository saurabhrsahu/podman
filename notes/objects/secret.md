# Secret

**Component:** Secret  
**See also:** [Container](./container.md) · [Index](../core-object-types.md)

## What it is

Sensitive **data at runtime** (password, token, TLS key)—given to [containers](./container.md) **without baking into the [image](./image.md)**. Prefer secrets over committing credentials or only using `-e` in production-minded setups.

| Idea | Detail |
|------|--------|
| Create | From file (`podman secret create`) |
| Use | Mounted as file at run time (`--secret`) |
| vs env | `-e VAR=...` is easier to leak via inspect/history |

## Commands

```bash
echo 'my-db-password' > scratch/db.pass
podman secret create db_password scratch/db.pass
podman secret ls
podman secret inspect db_password
podman run --rm --secret db_password alpine cat /run/secrets/db_password
podman secret rm db_password
rm scratch/db.pass
```

## What I learned

- Default mount path is often **`/run/secrets/<secret-name>`**—confirm with `podman secret inspect` on your version.
- Protect the **source file** on the host; rotation = new secret + recreate container.
- Compose supports `secrets:`—pair with a later compose note.

## Snippets to keep

```bash
podman secret create db_password ./scratch/db.pass
podman run --rm --secret db_password alpine cat /run/secrets/db_password
```

## Open questions / next time

- [ ] Compose + Postgres with secrets
- [ ] Secret vs env for local dev only

## What I ran (session log)

**Date:**  
**Context:**

```bash
# paste commands
```

**What happened:**

## Links

- [Podman secrets documentation](https://docs.podman.io/en/latest/markdown/podman-secret.1.html)
