# Agent tools

| Tool | Purpose |
|------|---------|
| `agent_spawn` | Create named persistent agent / tracker |
| `agent_recall` | Load latest state |
| `agent_update` | Progress / notes |
| `agent_schedule` | Recurring autonomous runs (**confirm first**) |
| `agent_unschedule` | Remove schedule |
| `agent_pause` / `agent_resume` | Control |
| `agent_identity` | Custodial Base identity address |
| `agent_ledger` | Audit ledger |
| `agent_runs` | Run history |
| `list_agents` | List all |
| `hire_agent` | One-shot specialist (no long-lived row) |

## Spawn vs hire vs app agents

| Path | Use when |
|------|----------|
| `agent_spawn` | Multi-session project tracker you will recall later |
| `hire_agent` | Immediate one-shot analysis |
| App “create agent” | Full in-app agent with skills pack (UI hub) |

## Confirmation checklist for schedules

- [ ] Goal clear  
- [ ] Cadence clear  
- [ ] Cost disclosed  
- [ ] Vault write policy clear  
- [ ] User said yes  

## Identity warning

Do not instruct users to send funds to `agent_identity` addresses without explaining custodial control.

See [../agents.md](../agents.md) and [../security.md](../security.md).
