---
icon: sliders
---

# Configuration

## Tool palettes

| `FINCH_TOOLS`    | Meaning                                        |
| ---------------- | ---------------------------------------------- |
| `core` (default) | Smaller palette — lower LLM context cost       |
| `all`            | Full registered set (**116** tools)            |
| `defi`           | DeFi-focused subset (Base + RH tools included) |

Set in MCP client `env`:

```json
"env": { "FINCH_TOOLS": "all" }
```

Banner / doctor report **exposed** count, not always the full registered total.

## Environment variables

### Account / backend

| Variable              | Required                    | Purpose                        |
| --------------------- | --------------------------- | ------------------------------ |
| `FINCH_SESSION_TOKEN` | Recommended for cloud tools | Session from Finch App / login |
| `FINCH_CONVEX_URL`    | Rarely                      | Override backend site URL      |

### Optional quality

| Variable            | Purpose                                     |
| ------------------- | ------------------------------------------- |
| `FIRECRAWL_API_KEY` | Better web crawl/search                     |
| `GITHUB_TOKEN`      | `github_search_code` and private GitHub ops |
| `ALCHEMY_API_KEY`   | Faster Base RPC (optional)                  |

### Host LLM keys (only when Finch _hosts_ inference)

Tools themselves do **not** need an LLM key. Keys matter for:

* CLI agent loop (`finch run`)
* Cron / scheduled agents with no client model
* Some deep research report modes

| Variable            | Purpose                                                         |
| ------------------- | --------------------------------------------------------------- |
| `BANKR_API_KEY`     | Bankr gateway                                                   |
| `ANTHROPIC_API_KEY` | Claude                                                          |
| `OPENAI_API_KEY`    | OpenAI                                                          |
| `OPENAI_BASE_URL`   | OpenAI-compatible self-host (LiteLLM, vLLM, Ollama, OpenRouter) |
| `GROK_API_KEY`      | xAI Grok                                                        |
| `FINCH_PROVIDER`    | Force `bankr` \| `anthropic` \| `openai` \| `grok`              |

## Guided setup

```bash
npx -y -p @finchagentic/mcp@4.4.1 finch setup
```

Picks providers and can enable local vault/memory.

## App (Convex) env — operators only

Finch App backend uses Convex dashboard secrets (not Vite `VITE_*` for Alchemy):

| Secret | Role |
|--------|------|
| `ALCHEMY_API_KEY` | RPC / balances via server routes |
| `CUSTOM_LLM_*` / `NINE_ROUTER_KEY` | Terminal / Build models |
| `BANKR_API_KEY` | Platform chat gateway |
| Wallet encryption keys | Custodial execution wallets |
| `MARKET_SETTLEMENT_LIVE` | API Market paid routing — **off** at soft-launch (free with key; USDG does not move) |

Frontend public env should stay minimal (`VITE_CONVEX_URL`, `VITE_CONVEX_SITE_URL`). Never put Alchemy secrets in `VITE_`.

## Version pin

Always pin `@finchagentic/mcp@4.4.1` in install docs and client configs. Bumping versions is a deliberate changelog event — not silent `@latest`.
