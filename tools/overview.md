# Tools overview

Finch MCP registers **121 tools** (measured from `@noelclaw/mcp@3.44.0` `ALL_TOOLS.length`).

Default exposure is the **`core`** palette. Set `NOELCLAW_TOOLS=all` for the full set.

## Pillars

| Pillar | Approx. count | Families |
|--------|---------------|----------|
| Memory | 10 + chronicle | `memory_*`, `chronicle_*` |
| Vault | 15 | `vault_*` |
| Agents | 12 | `agent_*`, `hire_agent`, `list_agents` |
| Workflows | 13 | automations, monitors, packets, schedule_research |
| Base DeFi | 11 | `base_mcp_*` |
| Robinhood Chain | 14 | `rh_mcp_*`, `rh_*` |
| Research | 5 | web + deep_research + compare/chain |
| Market | 12 | boards, thesis, trade_plan, scores |
| GitHub | 8 | `github_*` |
| Stocks / SEC | 3 | `stock_*` |
| Scanner / audit | 4 | miroshark, audit_contract |
| OS / wallet | 7 | balances, diagnostics, shell bridge |
| Other | playbooks, yields | `list_playbooks`, `run_playbook`, `get_defi_yields` |

## Full name list by family

### Memory (10)
`memory_add`, `memory_search`, `memory_context`, `memory_profile`, `memory_list`, `memory_delete`, `memory_insight`, `memory_extract`, `memory_publish`, `memory_consolidate`

### Chronicle (4)
`chronicle_add`, `chronicle_list`, `chronicle_search`, `chronicle_stats`

### Vault (15)
`vault_save`, `vault_read`, `vault_list`, `vault_search`, `vault_history`, `vault_diff`, `vault_export`, `vault_store_credential`, `vault_get_credential`, `vault_pin`, `vault_unpublish`, `vault_delete`, `vault_tag`, `vault_link`, `vault_related`

### Agents (12)
`list_agents`, `hire_agent`, `agent_spawn`, `agent_recall`, `agent_update`, `agent_identity`, `agent_ledger`, `agent_schedule`, `agent_unschedule`, `agent_pause`, `agent_resume`, `agent_runs`

### Workflows (13)
`create_automation`, `list_automations`, `pause_automation`, `delete_automation`, `get_automation_runs`, `run_automation`, `schedule_research`, `list_monitors`, `cancel_monitor`, `packet_create`, `packet_run`, `packet_list`, `packet_share`

### Base DeFi (11)
`base_mcp_yield_vaults`, `base_mcp_lending_rates`, `base_mcp_deposit_guide`, `base_mcp_network`, `base_mcp_status`, `base_mcp_balance`, `base_mcp_send`, `base_mcp_swap`, `base_mcp_estimate`, `base_mcp_lend`, `base_mcp_resolve`

### Robinhood Chain (14)
`rh_mcp_status`, `rh_mcp_list_stocks`, `rh_mcp_balance`, `rh_mcp_estimate`, `rh_mcp_swap`, `rh_token_resolve`, `rh_analyze`, `rh_safety_check`, `rh_dca_create`, `rh_bracket_create`, `rh_orders_list`, `rh_order_cancel`, `rh_orders_tick`, `rh_stock_bridge`

### Research (5)
`web_scrape`, `web_search`, `deep_research`, `research_compare`, `research_chain`

### Market (12)
`get_market_data`, `get_token_data`, `compare_tokens`, `market_overview`, `token_history`, `get_base_token_data`, `ask_noel`, `market_thesis`, `trade_plan`, `score_token`, `check_token`, `scan_market`

### GitHub (8)
`github_list_repos`, `github_list_prs`, `github_get_pr`, `github_list_issues`, `github_get_issue`, `github_get_file`, `github_get_commits`, `github_search_code`

### Stocks (3)
`stock_fundamentals`, `stock_insider`, `stock_events`

### Scanner (4)
`miroshark_simulate`, `miroshark_status`, `miroshark_stop`, `audit_contract`

### OS / wallet (7)
`get_noel_ledger`, `get_wallet_address`, `get_wallet_balance`, `wallet_sign_message`, `noel_status`, `noel_diagnostics`, `noel_shell_chat`

### Other (3)
`get_defi_yields`, `list_playbooks`, `run_playbook`

**Total = 121**

## Mutating tools (high care)

Always confirm with the user before:

- `base_mcp_send`, `base_mcp_swap`, `base_mcp_lend`  
- `rh_mcp_swap`, order create/cancel paths  
- `agent_schedule`, automation create/delete  
- `memory_delete`, `vault_delete`, `memory_publish`  
- Credential store/get  

## Detail pages

- [memory-vault.md](./memory-vault.md)  
- [agents.md](./agents.md)  
- [base-defi.md](./base-defi.md)  
- [robinhood-chain.md](./robinhood-chain.md)  
- [research.md](./research.md)  
- [market.md](./market.md)  
- [github-os.md](./github-os.md)  
