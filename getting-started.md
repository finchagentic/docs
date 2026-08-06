---
icon: play
---

# Getting started

## 60 seconds

```bash
# 1. Install / configure your MCP client
npx -y -p @finchagentic/mcp@4.4.1 finch install

# 2. Health check
npx -y -p @finchagentic/mcp@4.4.1 finch doctor

# 3. (Optional) fully local vault + memory
npx -y -p @finchagentic/mcp@4.4.1 finch setup
```

Then open Claude Code / Cursor / Hermes and say:

```
remember: I prefer conservative DeFi, max size caps on swaps
```

Expected: a `memory_add` (or vault profile) write that **auto-loads next session**.

***

## First workflows worth trying

### 1. Memory that survives the session

```
remember my coding style — TypeScript strict, no any, prefer composition
what do you know about my coding style?
```

### 2. Vault research note

```
deep research on Base AI infra protocols, save to vault
what did I save about Base AI infra?
```

### 3. Persistent agent

```
spawn an agent called base-tracker
goal: track Base DeFi weekly and save findings
```

### 4. Quote before swap (Base)

```
estimate swap 50 USDC to ETH on Base
```

Never executes until you explicitly confirm.

***

## Two ways to use Finch

| Mode           | When                                              | Needs                                    |
| -------------- | ------------------------------------------------- | ---------------------------------------- |
| **MCP client** | You already live in Claude Code / Cursor / Hermes | Install package · optional session token |
| **Finch App**  | Browser Terminal, Trading, Wallet, API Market     | Login (wallet SIWE) · session            |

MCP and App share the same product idea: **state that persists**. Tool surfaces are not 1:1 — Terminal has a focused analytics/swap subset; MCP has the full 116-tool runtime.

***

## Next

* [Install](install.md) for every client config
* [Local mode](local-mode.md) if you want zero account
* [Memory](memory.md) + [Vault](vault.md) for the core product story
* [Security](security.md) before any mainnet or schedule
