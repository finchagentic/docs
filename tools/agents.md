---
icon: user-hat-tie
---

# Agent tools

| Tool           | Purpose                                                        |
| -------------- | ---------------------------------------------------------------- |
| `agent_spawn`  | Create a named persistent agent / tracker with a goal              |
| `agent_recall` | Load latest state — own updates plus related memory/vault context matching the goal |
| `agent_update` | Log progress / findings (new version each call, full history kept) |
| `agent_ledger` | Audit of what the agent has done                                    |

That's the whole MCP agent surface. `agent_schedule`, `agent_unschedule`, `agent_pause`, `agent_resume`, `agent_identity`, `agent_runs`, `list_agents`, and `hire_agent` no longer exist — none of them ever had a working backend route, and they were removed rather than left dangling.

## MCP agents vs. real autonomous execution

An MCP-spawned agent is a persistent tracker: it only ever updates when something explicitly calls `agent_update`. Real unattended, scheduled execution — an agent that researches on its own and logs findings with no chat session involved — is an **app-only** feature (Finch App → an agent's detail page → "Run autonomously"). There is no MCP tool for it. See [../agents.md](../agents.md) for how it works and its guardrails (no fund-moving authority, 6-hour minimum interval).

## Related

* [../agents.md](../agents.md)
* [../security.md](../security.md)
