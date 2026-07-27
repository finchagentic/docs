# Market & scanner tools

> **Note:** this page is the **crypto / stock market scanner + analytics** tool
> palette (MCP). It is **not** the API Market (model inference marketplace).
> For buying/selling LLM inference with an API key, see
> [API Market](../app/api-market.md).



## Market / analytics

| Tool | Purpose |
|------|---------|
| `get_market_data` | Live board / market snapshot |
| `get_token_data` | Single token deep dive |
| `get_base_token_data` | Base-specific token data |
| `compare_tokens` | Side-by-side |
| `market_overview` | Global overview |
| `token_history` | Historical series |
| `market_thesis` | Thesis generation helper |
| `trade_plan` | Trade plan helper |
| `score_token` | Scoring |
| `check_token` | Health / checks |
| `scan_market` | Scan |
| `ask_finch` | Natural-language market helper |

## Scanner / sim

| Tool | Purpose |
|------|---------|
| `miroshark_simulate` | Simulation |
| `miroshark_status` | Status |
| `miroshark_stop` | Stop |
| `audit_contract` | Contract audit helper |

## Stocks / SEC-style

| Tool | Purpose |
|------|---------|
| `stock_fundamentals` | Fundamentals |
| `stock_insider` | Insider |
| `stock_events` | Events |

## Playbooks / yields

| Tool | Purpose |
|------|---------|
| `list_playbooks` | List |
| `run_playbook` | Run |
| `get_defi_yields` | Yields snapshot |

## App Terminal overlap

Finch App Terminal implements a **subset** (analytics + swap + wallet + automations + paid API call). Full market/scanner palette is MCP.
