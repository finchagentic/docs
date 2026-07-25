# Finch Docs

**Finch** is the runtime layer for Agentic AI — persistent memory, vault, agents, workflows, and execution tools that survive every session.

This documentation covers:

1. **Finch MCP** (`@noelclaw/mcp`) — install once into Claude Code, Cursor, Hermes, Windsurf, Codex, and any MCP client  
2. **Finch App** — Terminal, Trading, Wallet, API Market, Skills in the browser  

> Package name on npm is still `@noelclaw/mcp` (technical identifier). The product brand is **Finch**.

---

## Start here

| Path | What |
|------|------|
| [Getting started](./getting-started.md) | 60-second path from zero to first memory save |
| [Install](./install.md) | Every MCP client + pin rules |
| [Local mode](./local-mode.md) | Vault + memory on your machine, no account |
| [Configuration](./configuration.md) | Env vars, tool palettes, providers |
| [CLI](./cli.md) | `noelclaw` / doctor / setup / vault |

## Product pillars

| Pillar | Docs |
|--------|------|
| **Memory** | [memory.md](./memory.md) — semantic recall that auto-loads |
| **Vault** | [vault.md](./vault.md) — versioned notes, graph, credentials |
| **Agents** | [agents.md](./agents.md) — spawn, schedule, audit ledger |
| **Workflows** | [workflows.md](./workflows.md) — automations, monitors, packets, research |

## Tools reference

| Doc | Scope |
|-----|--------|
| [Tools overview](./tools/overview.md) | 121 tools · categories · palettes |
| [Memory & vault tools](./tools/memory-vault.md) | `memory_*` · `vault_*` · chronicle |
| [Agent tools](./tools/agents.md) | lifecycle · identity · ledger |
| [Base DeFi](./tools/base-defi.md) | `base_mcp_*` swaps, send, lend |
| [Robinhood Chain](./tools/robinhood-chain.md) | `rh_mcp_*` stocks + crypto |
| [Research](./tools/research.md) | web · deep_research · compare |
| [Market & scanner](./tools/market.md) | boards · scores · playbooks |
| [GitHub & OS](./tools/github-os.md) | github_* · diagnostics · shell |

## Finch App

| Doc | Scope |
|-----|--------|
| [App overview](./app/overview.md) | Surfaces, auth, stack |
| [Terminal](./app/terminal.md) | Chat tool-calling (analytics, swap, automations) |
| [Trading & wallet](./app/trading-wallet.md) | Base + RH Chain execution wallet |
| [API Market](./app/api-market.md) | Buy / Sell inference · OpenAI-compatible |
| [Skills](./app/skills.md) | Skill marketplace |

## Safety & ops

| Doc | Scope |
|-----|--------|
| [Security](./security.md) | 8 mandatory boundaries |
| [Troubleshooting](./troubleshooting.md) | doctor, common failures |
| [Clients](./clients.md) | Claude Code, Cursor, Hermes, VS Code, Zed |

---

## Quick facts

| Fact | Value |
|------|--------|
| MCP package | `@noelclaw/mcp@3.44.0` (pin — never `@latest`) |
| Registered tools | **121** |
| Default tool palette | `core` (set `NOELCLAW_TOOLS=all` for full set) |
| Primary chains | Base `8453` · Robinhood Chain `4663` |
| Settlement asset (API Market) | USDG on Robinhood Chain |
| npm | https://www.npmjs.com/package/@noelclaw/mcp |

---

## What Finch is *not*

- Not a generic “121 tools dump” pitch without persistence — the product is **memory + agents that stick**
- Not Robinhood brokerage / `agent.robinhood.com` — RH tools are **Robinhood Chain** (on-chain tokenized stocks + crypto)
- Not unauthenticated mainnet spend — swaps/sends need estimate → preview → confirm
