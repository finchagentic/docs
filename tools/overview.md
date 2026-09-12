---
icon: toolbox
---

# Tools overview

Finch MCP registers **116 tools** (measured from `@finchagentic/mcp@4.6.2` `ALL_TOOLS.length`).

Default exposure is the **`core`** palette. Set `FINCH_TOOLS=all` for the full set.

## Pillars

| Pillar          | Count | Families                                           |
| --------------- | ----- | --------------------------------------------------- |
| Memory          | 9 + chronicle (4) | `memory_*`, `chronicle_*`                    |
| Vault           | 17    | `vault_*` (incl. `code_session_save`, `list_projects`) |
| Agents          | 4     | `agent_spawn`, `agent_recall`, `agent_update`, `agent_ledger` |
| Staking         | 5     | `stake_*`, `claim_vested_rewards`                    |
| Workflows       | 13    | automations, monitors, packets, `schedule_research`  |
| Base DeFi       | 12    | `base_mcp_*`, `get_defi_yields`                      |
| Robinhood Chain | 14    | `rh_mcp_*`, `rh_*`                                   |
| Research        | 5     | web + `deep_research` + compare/chain                |
| Market          | 9     | boards, thesis, `trade_plan`                         |
| Scanner / audit | 4     | `score_token`, `check_token`, `scan_market`, `audit_contract` |
| GitHub          | 8     | `github_*`                                           |
| Stocks / SEC    | 3     | `stock_*`                                            |
| Miroshark       | 3     | simulate, status, stop                               |
| OS / wallet     | 6     | balances, sign, shell bridge, diagnostics             |

Notable removals since earlier releases: `list_agents`/`hire_agent` and every autonomous-schedule agent tool (`agent_identity`, `agent_schedule`, `agent_unschedule`, `agent_pause`, `agent_resume`, `agent_runs`) were removed — their backend routes never existed. `list_playbooks`/`run_playbook`/`get_finch_ledger` (Noel Framework) were removed the same way. `memory_publish` was removed for promising a "Memory Marketplace" that doesn't exist at any layer.

## Full name list by family

### Memory (9)

`memory_add`, `memory_search`, `memory_context`, `memory_profile`, `memory_list`, `memory_delete`, `memory_insight`, `memory_extract`, `memory_consolidate`

### Chronicle (4)

`chronicle_add`, `chronicle_list`, `chronicle_search`, `chronicle_stats`

### Vault (17)

`vault_save`, `code_session_save`, `vault_read`, `vault_list`, `vault_search`, `vault_history`, `vault_diff`, `vault_export`, `vault_pin`, `vault_unpublish`, `vault_tag`, `vault_delete`, `vault_link`, `vault_related`, `vault_store_credential`, `vault_get_credential`, `list_projects`

### Agents (4)

`agent_spawn`, `agent_recall`, `agent_update`, `agent_ledger`

### Staking (5)

`stake_finch_status`, `stake_finch`, `unstake_finch`, `claim_vested_rewards`, `stake_auto_restake`

### Workflows (13)

`create_automation`, `list_automations`, `pause_automation`, `delete_automation`, `get_automation_runs`, `run_automation`, `schedule_research`, `list_monitors`, `cancel_monitor`, `packet_create`, `packet_run`, `packet_list`, `packet_share`

### Base DeFi (12)

`get_defi_yields`, `base_mcp_yield_vaults`, `base_mcp_lending_rates`, `base_mcp_deposit_guide`, `base_mcp_network`, `base_mcp_status`, `base_mcp_balance`, `base_mcp_send`, `base_mcp_swap`, `base_mcp_estimate`, `base_mcp_lend`, `base_mcp_resolve`

### Robinhood Chain (14)

`rh_mcp_status`, `rh_mcp_list_stocks`, `rh_mcp_balance`, `rh_mcp_estimate`, `rh_mcp_swap`, `rh_token_resolve`, `rh_analyze`, `rh_safety_check`, `rh_dca_create`, `rh_bracket_create`, `rh_orders_list`, `rh_order_cancel`, `rh_orders_tick`, `rh_stock_bridge`

### Research (5)

`web_scrape`, `web_search`, `deep_research`, `research_compare`, `research_chain`

### Market (9)

`get_market_data`, `get_token_data`, `compare_tokens`, `market_overview`, `token_history`, `get_base_token_data`, `ask_finch`, `market_thesis`, `trade_plan`

### Scanner (4)

`score_token`, `check_token`, `scan_market`, `audit_contract`

### GitHub (8)

`github_list_repos`, `github_list_prs`, `github_get_pr`, `github_list_issues`, `github_get_issue`, `github_get_file`, `github_get_commits`, `github_search_code`

### Stocks (3)

`stock_fundamentals`, `stock_insider`, `stock_events`

### Miroshark (3)

`miroshark_simulate`, `miroshark_status`, `miroshark_stop`

### OS / wallet (6)

`get_wallet_address`, `get_wallet_balance`, `wallet_sign_message`, `finch_status`, `finch_diagnostics`, `finch_shell_chat`

**Total = 116**

## Mutating tools (high care)

Always confirm with the user before:

* `base_mcp_send`, `base_mcp_swap`, `base_mcp_lend`
* `rh_mcp_swap`, order create/cancel paths, `stake_finch`, `unstake_finch`
* `create_automation` (two-step: preview first, then `confirm: true`), `delete_automation`
* `memory_delete`, `vault_delete`
* Credential store/get

## Detail pages

* [memory-vault.md](memory-vault.md)
* [agents.md](agents.md)
* [base-defi.md](base-defi.md)
* [robinhood-chain.md](robinhood-chain.md)
* [research.md](research.md)
* [market.md](market.md)
* [github-os.md](github-os.md)
