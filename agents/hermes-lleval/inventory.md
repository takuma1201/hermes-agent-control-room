# hermes-lleval - Inventory

Measured 2026-10-01.

## Role

Isolated local-LLM comparison profile. No cloud provider, no fallback.

## Where It Runs

- Deployment style: Hermes profile (native)
- Data dir: `~/.hermes/profiles/lleval`
- Gateway: served by the default-profile multiplexer
- Model: `lleval` / `qwen36-35b-a3b` via llama-server `http://127.0.0.1:18500/v1`
  (also defined: `qwen38-27b`, `devstral2-24b`, `plano-30b-a3b`)
- llama-server was not listening at measurement time (started on demand)

## Tools

- `toolsets: [terminal, file]`, `max_turns: 40`, `run_budget_seconds: 1200`

## Credentials

- `~/.hermes/profiles/lleval/.env`: `LLEVAL_SERVER_KEY` (value not recorded)

## Allowed Work

- Local LLM benchmarking (see skill `local-llm-evaluation`)

## Forbidden Work

- Cloud model calls, production work

## Backup / Runbook

- Use `hermes -p lleval ...` for every command.
- Backup: `hermes -p lleval backup -q`.

## Owner

- Takuma
