# Agents

Persistent agents are named workstreams that **keep state** — not one-shot function calls.

## Mental model

| Concept | Meaning |
|---------|---------|
| Spawn | Create a named agent with a goal |
| Recall | Load latest state weeks later |
| Update | Progress / notes |
| Schedule | Recurring autonomous runs (needs confirmation) |
| Ledger / runs | Audit of what ran, cost, status |
| Identity | Optional Base address (custodial — see security) |

## Typical prompts

```
spawn an agent called market-researcher
goal: track Base protocols weekly

what is agent market-researcher working on?
update agent market-researcher progress: "covered Aerodrome and Morpho"
```

## Tool surface (MCP)

| Tool | Role |
|------|------|
| `agent_spawn` | Create tracker / agent note |
| `agent_recall` | Resume state |
| `agent_update` | Progress |
| `agent_schedule` / `agent_unschedule` | Recurring runs |
| `agent_pause` / `agent_resume` | Control |
| `agent_identity` | Base identity address |
| `agent_ledger` / `agent_runs` | Audit |
| `list_agents` | List |
| `hire_agent` | One-shot specialist run |

> Product also has richer “create agent” paths in the app (Identity + Prompt + Skills). MCP `agent_spawn` is the multi-session tracker path; don’t confuse with one-shot `hire_agent`.

## Confirmation required

Before `agent_schedule`:

1. Name + goal  
2. Cadence (daily / weekly / cron)  
3. Expected LLM cost per run  
4. Whether vault writes are allowed  
5. Explicit user yes  

## Identity custody (critical)

`agent_identity` returns a **backend-controlled** Base address. The private key is not the user’s browser wallet.

- Do **not** casually tell users to fund that address  
- User login wallet ≠ agent execution identity  
- See [security.md](./security.md) boundary 8  

## Related

- [Workflows](./workflows.md) for automations/monitors without a full agent persona  
- [Tools: agents](./tools/agents.md)  
