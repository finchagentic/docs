---
icon: florin-sign
---

# Finch App overview

Browser product for Finch: chat terminal, trading, wallet, API Market, skills.

## Stack

| Layer      | Tech                                          |
| ---------- | --------------------------------------------- |
| Frontend   | React 19, Vite, Tailwind, Zustand             |
| Backend    | Convex (queries/mutations/actions/HTTP/crons) |
| Auth       | Wallet SIWE → session token                   |
| Chains     | Base `8453`, Robinhood Chain `4663`           |
| Settlement | USDG on Robinhood Chain                       |

## Surfaces (routes)

| Route                   | Surface                                          |
| ----------------------- | ------------------------------------------------ |
| `/terminal`             | AI Terminal (chat + tool calling)                |
| `/trading`              | Trading (curated board + Pons Launchpad discovery) |
| `/wallet`               | Wallet                                           |
| `/agents`               | Persistent agents — spawn, recall, and toggle real autonomous background execution |
| `/automation`           | Scheduled/price-trigger automations (swap, send, alert) |
| `/graph`                | Public 3D graph — every user's published research/agents, plus a live layer of graduated Pons Launchpad tokens |
| `/stake`                | FINCH staking                                    |
| `/apimarket/*`          | API Market (catalog, buy, sell, analytics, docs) |
| `/skills`               | Skills marketplace                               |
| `/leaderboard`, `/metrics`, `/activity` | Public stats, platform metrics, live activity feed |
| `/profile`, `/settings` | Account                                          |

## Auth model

1. **Identity wallet** — login via SIWE
2. **Execution wallet** — custodial encrypted key for Base + RH txs + market payout
3. **API keys** — buyer keys for OpenAI-compatible market (`*_sk_*` style; UI may brand as Finch)

## Relation to MCP

|              | App                                 | MCP                         |
| ------------ | ----------------------------------- | --------------------------- |
| Memory/vault | Prompt injection + product features | Full tool palette           |
| Trading UI   | Visual confirm flows                | `base_mcp_*` / `rh_mcp_*`   |
| API Market   | Buy/Sell dashboards                 | Not the primary MCP surface |
| Tool count   | Focused Terminal tools              | 116 registered tools        |

## Operator notes

* Never put Alchemy keys in `VITE_*`
* Dual deploy often needed: Convex + frontend host
* See monorepo `architecture.md` for internal module map
