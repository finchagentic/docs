# Solana tools (`sol_*`)

Seven tools for Solana, in the `defi` and `all` presets (`FINCH_PRESET=defi`). They use a **local** Solana wallet that never leaves your machine. Fund-moving tools only execute with `confirmed=true`.

| Tool | What it does |
| ---- | ------------ |
| `sol_wallet` | Public address of your local wallet (created on first use) |
| `sol_balance` | SOL and SPL balances (Token and Token-2022) |
| `sol_token_info` | Price, liquidity, market cap, holders for any mint |
| `sol_quote` | Jupiter quote with min received and price impact |
| `sol_swap` | Jupiter swap. Rejects price impact above 5% |
| `sol_send` | Send SOL or an SPL token |
| `sol_launch_token` | Launch a token on pump.fun |

Official `$FINCH` mint: `4LKS9yUYaBEZyzsaExmFXcWbG9pDBX7AWhseigVYpump`.

Set `FINCH_SOLANA_RPC_URL` to use your own RPC. Source: [`@finchagentic/mcp`](https://www.npmjs.com/package/@finchagentic/mcp) 4.8.0+.
