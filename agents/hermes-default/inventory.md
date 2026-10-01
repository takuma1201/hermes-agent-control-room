# hermes-default - Inventory

Measured 2026-10-01.

## Role

Primary Hermes agent used from the Hermes desktop app: business planning, strategy,
decision logs, implementation planning and review.

## Where It Runs

- Host: local Mac (macOS)
- Deployment style: native install (no container)
- Install dir: `~/.hermes/hermes-agent` (Hermes Agent v0.21.5)
- Data dir: `~/.hermes`
- Gateway: running manually, not installed as a service (`hermes gateway install` not done)
- Profile multiplexing: on (`gateway.multiplex_profiles: true`), also serves `lleval`

## Model

- Provider: `omniroute`, model `auto/pro-coding`, base_url `http://localhost:21128/v1`
- Delegation: `max_concurrent_children: 10`, `child_timeout_seconds: 600`

## Ports

Gateway uses a local socket (`~/.hermes/gateway.sock`); no TCP listener observed.
Dashboard is started on demand with `hermes dashboard`.

## Messaging Integrations

- Telegram: disabled (no bot token)
- Slack / Discord: not configured

## Credentials

See `env-map.md`. Do not paste values here.

## Memory & Skills

- Memory: `~/.hermes/memories/MEMORY.md`, `USER.md`
- Persona: `~/.hermes/SOUL.md`
- Skills: `~/.hermes/skills` (48 category dirs, 1634 `SKILL.md`)
- Crons: none scheduled
- Kanban: `~/.hermes/kanban.db`

## Allowed Work

- Planning, research, implementation, browser automation

## Forbidden Work

- Destructive operations without explicit approval
- Editing other profiles' skills/plugins/cron/memories without explicit direction

## Owner

- Takuma
