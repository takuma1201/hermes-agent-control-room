# hermes-default - Runbook

## Talk To The Agent

- Desktop: Hermes desktop app
- CLI: `hermes`

## Check Status

```bash
hermes --version
hermes gateway status
hermes profile list
hermes doctor
```

## Restart Gateway

```bash
hermes gateway restart
```

## Model Route Health

```bash
lsof -nP -iTCP:21128 -sTCP:LISTEN   # OmniRoute must be listening
launchctl list | grep omniroute
```

## Rotate A Key

1. Create the new key in the provider dashboard.
2. Update `~/.hermes/.env`.
3. `hermes gateway restart`.
4. Revoke the old key.
5. Update `env-map.md` (rotation date only).

## Restore From Backup

See `backup.md`.
