# Local adaptation (Takuma / macOS)

This copy of `shannhk/hermes-agent-control-room` (upstream commit `48a1a5a`) is adapted
for a **single macOS machine**, not a VPS.

## What is different from upstream

| Upstream assumption | This machine |
|---|---|
| Ubuntu VPS, `/root/agent-control-room` | macOS, `~/workspace/agent-control-room` |
| One Docker container per agent, `/srv/<agent>/data` | Native install, Hermes profiles under `~/.hermes` and `~/.hermes/profiles/<name>` |
| `/srv/agent-bus` file task bus | Built-in `hermes kanban` (SQLite `~/.hermes/kanban.db`) and `delegate_task` |
| `docker.md` per agent | Not used (no containers). Deployment details live in `inventory.md` |

## Skills: do NOT use

- `skills/create-vps` — Hetzner provisioning; `hcloud` is not installed and no VPS is planned.
- `skills/setup-control-room` — runs `curl | bash` installers as root and symlinks skills into
  `~/.claude/skills`. Not applicable to this machine.

The remaining skills (`agent-control-room`, `agent-registry-manager`, `agent-backup-manager`,
`agent-security-auditor`, `agent-task-router`, `agent-team-cron-planner`) are plain checklists
and can be read as reference.

## Where things are

- `registry/agents.yaml` — every agent and local AI service on this machine (ports, owner, exposure).
- `agents/<slug>/` — per-agent inventory, env-map (names only), runbook, backup.
- `audits/` — dated security audit results.

## Rules

- Never write secret values. Key names and locations only.
- Facts here were measured on the date shown in each file; re-measure before acting on them.
- Upstream updates: `git fetch origin && git log HEAD..origin/main` then merge by hand.
