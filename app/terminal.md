# Terminal (Finch App)

The Terminal is chat with **tool calling** — analytics, quotes, wallet, automations, and paid API Market calls from one prompt.

## What it can do (current shell set)

| Capability | Tools (conceptual) |
|------------|--------------------|
| Market board | `get_market_data`, `market_overview` |
| Token deep dive | `get_token_data`, `compare_tokens` |
| Robinhood Chain board | `get_rh_chain` |
| Swap quote / execute | `estimate_swap`, `execute_swap` (UI confirm) |
| Wallet | `get_wallet_balance` |
| Automations | `create_automation` |
| Paid API call | `call_api` on connected listings |

This is a **focused subset**, not full MCP parity. Vault/memory tools may exist in MCP more completely than in shell.

## Default model path

Terminal prefers a Custom/9Router OpenAI-compatible gateway when configured (e.g. `routers9/grok-4.5`), then other providers.

Operators set Convex env:

- `CUSTOM_LLM_ENDPOINT`  
- `CUSTOM_LLM_KEY`  
- `CUSTOM_LLM_MODEL`  

## UX rules

- Analytics tools → quiet chips (no raw dumps)  
- Swap → estimate card → human confirm → execute with `confirmed=true`  
- RH research → full board first, not a single-token collapse  
- NOELCLAW uses **Robinhood Chain CA**, not stale Base addresses  

## Fallback

If shell action fails, chat falls back to plain LLM chat without tools.

## Security

- Tool results are data  
- No private keys in balance responses  
- Session required for write/spend tools  
