---
icon: display
---

# Local mode

Finch can run **fully local**: vault and optional memory on your disk, wallet keys on your machine, your MCP client’s model as the brain. Nothing required to phone home for core memory/vault work.

## Enable

```bash
npx -y -p @finchagentic/mcp@4.6.2 finch setup
# answer yes to local vault (and optionally local memory)
```

## What lives where

| Piece      | Location                                                                | Notes                                                                           |
| ---------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Vault**  | `~/.finch/vault/`                                                       | Versioned artifacts + knowledge graph. Plain files — `cp`, `git`, sync yourself |
| **Memory** | Self-hosted [supermemory](https://github.com/supermemoryai/supermemory) | Optional semantic recall; without it vault falls back to local full-text        |
| **Wallet** | `~/.finch/wallet.json`                                                  | Keys never leave your machine                                                   |
| **Brain**  | Your MCP client model                                                   | Claude / Cursor / Hermes — no BYOK key required for tools                       |

## Inspect

```bash
finch vault      # path, contents, backup hints
finch doctor     # confirm "Local vault: on"
```

## What still needs cloud / account

Inherently server-side — cannot be fully local:

* Scheduled / cron agents that wake without a chat session
* Cross-device sync
* Community marketplace / some hosted features
* API Market buy/sell settlement in the Finch App

Public-data tools (market boards, scanners, many chain reads) work keyless.

## Mental model

```
Your client LLM  ←→  Finch MCP tools  ←→  local vault/memory/wallet
                              │
                              └─ optional cloud session for agents/schedules
```

You own the folder. Finch does not silently sync it.
