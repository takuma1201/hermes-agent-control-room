# openclaw - Inventory

Measured 2026-10-01.

## Role

Telegram front door + scheduled daily brief. Deliberately scoped to ONE job so it does not
overlap with Hermes (which remains the main agent for planning and implementation).

## Where It Runs

- Deployment: native npm install, `openclaw` v2026.7.1-2
- Data dir: `~/.openclaw`
- Gateway: LaunchAgent `ai.openclaw.gateway`, listens `127.0.0.1:18789` (localhost only)
- Log: `~/Library/Logs/openclaw/gateway.log` (note: `~/.openclaw/logs/*.log` is stale, last
  written 2026-06-15 — do not read it when debugging)

## Model

- Provider `omniroute` -> `http://127.0.0.1:21128/v1`, model `auto/pro-coding`
- Shares the OmniRoute key with Hermes (see env-map.md)

## Channels

- Telegram: `@ts1201_openclaw_bot`, allowFrom `8343028869` (private chat)
- ClickClack: installed, not configured

## Scheduled jobs

| Name | Schedule | Delivery |
|---|---|---|
| Morning Brief | `0 8 * * *` (exact) | telegram -> 8343028869 |
| Memory Dreaming Promotion | `0 3 * * *` | none (internal, managed by memory-core) |

Morning Brief content: today's Calendar events, unread Mail summary, non-done
`hermes kanban` tasks. Isolated session, 300s timeout.

## Fixes applied 2026-10-01

Agent turns had been failing 100% before this date. Three separate causes:

1. `agents.defaults.sandbox.mode` was `all`, which requires Docker; Docker was not running.
   -> set to `off`.
2. Default model was `ollama/qwen3:14b`, which does not exist in the local Ollama
   (only `qwen2.5:0.5b` and `nomic-embed-text` are installed).
   -> switched provider to `omniroute`.
3. The configured 9router model `kr/claude-sonnet-4.5` no longer exists in the 9router
   catalogue (zero `kr/` models) and the stored 9router key returns `401 Invalid API key`
   on `/v1/chat/completions`. Note `/v1/models` returns 200 without any key, so a 200 there
   does NOT prove the key is valid.
   -> abandoned 9router for OpenClaw; OmniRoute is used instead.

Delivery pitfall: `--channel telegram --deliver` alone fails with
`agent delivery target missing: Delivering to Telegram requires target <chatId>`.
`--to <chatId>` is mandatory.

## Known config defect (not fixed)

`secrets.providers` contains both `default` and a typo entry `defaul`, both pointing at
`~/.openclaw/secrets.json`. No observed impact.

## Backups

- `~/workspace/backups/openclaw-fix-20261001-165342/openclaw.json` (before sandbox/model change)
- `~/.openclaw/openclaw.json.pre-omniroute`, `~/.openclaw/secrets.json.pre-omniroute`

## Owner

- Takuma
