---
icon: tencent-weibo
---

# Robinhood Chain tools

**Robinhood Chain** = on-chain network `4663` (tokenized stocks + RH crypto pools).

This is **not** Robinhood brokerage / `agent.robinhood.com`.

## Core MCP tools

| Tool                 | Purpose                                |
| -------------------- | -------------------------------------- |
| `rh_mcp_status`      | Chain / readiness                      |
| `rh_mcp_list_stocks` | Tokenized stock list                   |
| `rh_mcp_balance`     | Balances                               |
| `rh_mcp_estimate`    | Quote only                             |
| `rh_mcp_swap`        | Execute swap (`confirm:true` required) |

## Extended RH tools

| Tool                | Purpose                     |
| ------------------- | --------------------------- |
| `rh_token_resolve`  | Resolve symbols / addresses |
| `rh_analyze`        | Analysis                    |
| `rh_safety_check`   | Safety checks               |
| `rh_dca_create`     | DCA order                   |
| `rh_bracket_create` | Bracket order               |
| `rh_orders_list`    | List orders                 |
| `rh_order_cancel`   | Cancel                      |
| `rh_orders_tick`    | Tick/engine step            |
| `rh_stock_bridge`   | Bridge helper               |

## Explorer

`https://robinhoodchain.blockscout.com`

## Settlement (API Market)

API Market buyer/seller settlement uses **USDG** on Robinhood Chain — see [../app/api-market.md](../app/api-market.md).

## $FINCH token note

Official CA (Solana, pump.fun): `4LKS9yUYaBEZyzsaExmFXcWbG9pDBX7AWhseigVYpump`\
Staking in the Finch App still settles in the Robinhood Chain ERC-20 `0x879f29204a5ff842c66f0f65e0f2e422073acce7`.\
Do not use stale Base CAs for $FINCH trading/analysis.

## Rules

* Estimate before swap
* `rh_mcp_swap` needs explicit confirm
* Don’t use Base 0x tools for RH stocks
