# Trading & Wallet

## Wallet

- Shows custodial **execution wallet** balances for Base crypto and Robinhood Chain assets  
- Send / swap flows go through confirm UI  
- Identity wallet (login) is separate from execution wallet  

## Trading

- Quotes and execution on supported chains  
- Base swaps via 0x-style routes  
- RH path for tokenized stocks / RH crypto when selected  
- Automations / TP-SL / DCA panels may appear as product features — treat live vs Soon honestly in UI  

## Safety

| Rule | Detail |
|------|--------|
| Confirm | Every mainnet send/swap |
| Impact caps | Refuse extreme price impact |
| Keys | Never display raw private keys |
| Alchemy | Server-only |

## Related MCP

For agentic trading from Claude/Cursor, use:

- `base_mcp_*` on Base  
- `rh_mcp_*` on Robinhood Chain  

See [../tools/base-defi.md](../tools/base-defi.md) and [../tools/robinhood-chain.md](../tools/robinhood-chain.md).
