---
icon: square-terminal
---

# Terminal (Finch App)

The Terminal is chat with **tool calling** — analytics, quotes, wallet, agents, automations, and Pons Launchpad discovery, all from one prompt.

## What it can do (current shell set — 22 tools)

| Capability | Tools |
|------------|-------|
| Market board | `get_market_data`, `market_overview` |
| Token deep dive | `get_token_data`, `compare_tokens` |
| Robinhood Chain board | `get_rh_chain` |
| Pons Launchpad lookup | `pons_search` — resolves a launchpad token by ticker/name, ranked by real liquidity so a same-named zero-liquidity clone never wins over the real token |
| Swap quote / execute | `estimate_swap`, `execute_swap` (UI confirm card) |
| Send | `send_token` (UI confirm card) |
| Staking | `stake_finch`, `unstake_finch`, `stake_finch_status` |
| Automations | `create_automation`, `list_automations`, `pause_automation`, `delete_automation` (swap/send actions require UI confirm; alerts create immediately) |
| Agents | `agent_spawn`, `agent_update`, `agent_recall` (persistent memory namespace shared with the MCP server's own `agent_*` tools) |
| Memory search | `memory_recall` — read-only semantic search over the user's existing memories from any source (chat, MCP, agents) |
| Live web | `web_search` — real Firecrawl results, not training-data recall |
| Paid API call | Market calls surface via the API Market dashboard / OpenAI-compatible `/v1/chat/completions` (see [api-market.md](./api-market.md)) |

This is a **focused subset**, not full MCP parity — the MCP server has the complete 116-tool runtime (`vault_*`, staking, GitHub, research, etc.). The app shell mirrors the parts most useful for chat-driven trading and research.

## Chat mode toggles

The composer has three opt-in toggles, off by default, persisted per browser:

* **Memory** — relevant saved memories are auto-recalled and injected as context before the model replies, instead of only searching when explicitly asked.
* **Web Search** — the model treats `web_search` as expected for any question touching current events or prices, not just when told to search.
* **Auto-Agent** — the model may proactively `agent_spawn` for a clearly multi-step/ongoing request without waiting to be asked first. It still always tells you it did so.

## Default model path

Terminal prefers a Custom/9Router OpenAI-compatible gateway when configured (e.g. `routers9/grok-4.5`), then other providers.

Operators set Convex env:

* `CUSTOM_LLM_ENDPOINT`
* `CUSTOM_LLM_KEY`
* `CUSTOM_LLM_MODEL`

## UX rules

* Analytics tools → quiet chips (no raw dumps)
* Swap/send/stake → estimate or preview card → human confirm → execute with `confirmed=true`. The model never treats its own `confirmed=true` output as sufficient on its own — the UI only renders a real confirm card after a first call comes back blocked, and only a genuine click re-sends with authorization.
* RH research → full board first (`get_rh_chain`), not a single-token collapse
* A Robinhood-chain token that isn't ETH/WETH/USDG/FINCH and isn't on the curated board is almost certainly a Pons launchpad token — resolve it with `pons_search` first, never guess an address
* $FINCH / product token uses **Robinhood Chain CA**, not stale Base addresses

## Fallback

If a shell action fails, chat falls back to plain LLM chat without tools.

## Security

* Tool results are data, never treated as instructions
* No private keys in balance responses
* Session required for write/spend tools
* Autonomous agent runs (see [../agents.md](../agents.md)) get no fund-moving authority at all, regardless of what the model outputs
