---
icon: chart-column
---

# Trading & Wallet

## Wallet

* Shows custodial **execution wallet** balances for Base crypto and Robinhood Chain assets
* Send / swap flows go through confirm UI
* Identity wallet (login) is separate from execution wallet

## Trading

* Quotes and execution on supported chains
* Base swaps via 0x-style routes
* RH path for tokenized stocks / RH crypto when selected
* Automations / TP-SL / DCA panels may appear as product features — treat live vs Soon honestly in UI

## Pons Launchpad (Robinhood Chain)

The Trading page has a dedicated Pons Launchpad view alongside the curated token board — every token launched on [Pons](https://ponsfamily.com), indexed live directly on-chain (there's no Pons API; Finch reads `TokenLaunched` events off their factory contracts itself). Trending, New, and Graduated tabs, real launch icons/descriptions decoded from the launch transaction, and full pagination through the catalog.

"Graduated" reflects the factory's own `graduationStatus()` — it confirms a pool crossed Pons's liquidity threshold, not a quality or safety signal. It's a permissionless launchpad: anything can be deployed, including many tokens sharing the same ticker. Terminal's `pons_search` tool (see [terminal.md](./terminal.md)) ranks matches by real liquidity specifically so a zero-liquidity same-named clone never gets picked over the real token.

## Safety

| Rule        | Detail                         |
| ----------- | ------------------------------ |
| Confirm     | Every mainnet send/swap        |
| Impact caps | Refuse extreme price impact    |
| Keys        | Never display raw private keys |
| Alchemy     | Server-only                    |

## Related MCP

For agentic trading from Claude/Cursor, use:

* `base_mcp_*` on Base
* `rh_mcp_*` on Robinhood Chain

See [../tools/base-defi.md](../tools/base-defi.md) and [../tools/robinhood-chain.md](../tools/robinhood-chain.md).
