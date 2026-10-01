# hermes-default - Env / Secret Map

Names and locations only. Measured 2026-10-01.

## Locations

- `~/.hermes/.env` — provider API keys
- `~/.hermes/auth.json` — OAuth / provider auth state
- Hermes vault — saved website logins (managed by Hermes, values never shown)

## Keys in `~/.hermes/.env`

| Key | Purpose | Last rotated |
|---|---|---|
| `HERMES_CUSTOM_OMNIROUTE_API_KEY` | OmniRoute (primary model route) | TBD |
| `HERMES_CUSTOM_9ROUTER_API_KEY` | 9router | TBD |
| `HERMES_CUSTOM_OPENCODEX_API_KEY` | OpenCodex route | TBD |
| `OPENROUTER_API_KEY` | OpenRouter | TBD |
| `DEEPSEEK_API_KEY` | DeepSeek | TBD |
| `MINIMAX_API_KEY` | MiniMax | TBD |

Non-secret settings in the same file: `OLLAMA_BASE_URL`, `TERMINAL_*`, `BROWSER*`, `*_DEBUG`.

## Rules

- Do not paste raw values in this file.
- Rotate any key pasted into chat.
