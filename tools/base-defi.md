# Base DeFi tools (`base_mcp_*`)

All Base mainnet execution goes through the **`base_mcp_*`** family — not legacy generic names.

Chain ID: **8453**.

## Tools

| Tool | Purpose |
|------|---------|
| `base_mcp_status` | Connection / readiness |
| `base_mcp_network` | Network info |
| `base_mcp_balance` | Balances |
| `base_mcp_resolve` | Resolve token symbols/addresses |
| `base_mcp_estimate` | Quote only (swap/send) |
| `base_mcp_swap` | Execute swap after confirm |
| `base_mcp_send` | Transfer after confirm |
| `base_mcp_lend` | Lending action after confirm |
| `base_mcp_lending_rates` | Rates |
| `base_mcp_yield_vaults` | Yield vault list |
| `base_mcp_deposit_guide` | Deposit guidance |

## Mandatory flow

```
estimate → show preview → user confirms → swap/send/lend
```

`base_mcp_estimate` never broadcasts.

## Routing

Swaps typically route via 0x / Permit2 style paths. Price impact caps can refuse unsafe trades.

## Not for Robinhood Chain

Tokenized stocks / RH chain assets use `rh_mcp_*` — never `base_mcp_*` for those.

See [robinhood-chain.md](./robinhood-chain.md).
