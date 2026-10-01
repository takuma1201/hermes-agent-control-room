# openfang - Inventory (FROZEN)

Measured 2026-10-01. Status: installed, intentionally NOT in use.

## Decision

Frozen on 2026-10-01. Not uninstalled, not running, no autostart.
Reason: its core model (orchestrator + specialist agents + model routing + skills) duplicates
what Hermes and OpenCode already do here. Adding it would add a daemon, a secrets file and a
port without covering a gap.

## Facts

- Binary: `~/.cargo/bin/openfang` v0.6.9 (Rust, 48 MB)
- Data dir: `~/.openfang` (config.toml, secrets.env, data/openfang.db)
- API would listen on `127.0.0.1:4200`; daemon is NOT running
- Agents dir contains 30 entries, all stock samples (hello-world, recruiter, tutor...).
  Cron jobs: 0. No evidence of real use.
- Secrets in `~/.openfang/secrets.env`: `OMNIROUTER_API_KEY`, `HF_API_KEY` (names only)
- Upstream `RightNow-AI/openfang`: Apache-2.0, 18.2k stars, last push 2026-07-02

## What is genuinely NOT duplicated

From the kernel boot log (`openfang start`): 61 bundled skills and 9 bundled "Hands"
(clip, lead, collector, predictor, researcher, twitter, browser, trader, infisical-sync).
Hands are prepackaged autonomous jobs — Hermes has no equivalent concept.
Config also has free-tier model routing by prompt size (simple/medium/complex -> OpenRouter
free models).

## Unfreeze criteria

Revisit only if a concrete need appears, most plausibly:
scoring recorded predictions over time (predictor Hand) to measure decision quality.
Until then, do not spend time learning it.

## Note

The marketing claims around it ("16 security layers", WASM sandbox, Merkle audit trail) are
UNVERIFIED here. Verify before trusting it with credentials.
