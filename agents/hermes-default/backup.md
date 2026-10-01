# hermes-default - Backup

## Status (2026-10-01)

No scheduled backup. `~/.hermes/backups/` contains only `config/`.

## Built-in command

```bash
hermes backup -q              # quick: config, state.db, .env, auth, cron
hermes backup -o ~/path.zip   # full Hermes home (excludes hermes-agent codebase)
```

Both archives contain secrets (`.env`, `auth.json`). Store them locally or in an encrypted
location only; never commit them to git.

## Durable state worth keeping

- `SOUL.md`, `config.yaml`, `memories/`, `skills/`, `cron/`, `kanban.db`

## Restore

1. Stop the gateway: `hermes gateway stop`.
2. Restore files into `~/.hermes`.
3. Re-check `.env` / `auth.json`.
4. `hermes gateway start` and `hermes doctor`.
