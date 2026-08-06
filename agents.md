---
icon: user-hat-tie
---

# Agents

Persistent agents are named workstreams that **keep state** — not one-shot function calls.

## Mental model

| Concept | Meaning                                              |
| ------- | ----------------------------------------------------- |
| Spawn   | Create a named agent with a goal                       |
| Recall  | Load latest state, weeks later — pulls in related vault/memory context matching the goal too, not just its own logged updates |
| Update  | Log progress / findings (new version each call, full history kept) |
| Ledger  | Audit of what the agent has done                        |

## Typical prompts

```
spawn an agent called market-researcher
goal: track Base protocols weekly

what is agent market-researcher working on?
update agent market-researcher progress: "covered Aerodrome and Morpho"
```

## Tool surface (MCP)

| Tool            | Role                                          |
| --------------- | ---------------------------------------------- |
| `agent_spawn`   | Create a named tracker with a goal              |
| `agent_recall`  | Resume state — own updates + related memory/vault context |
| `agent_update`  | Log progress (a new version each call)          |
| `agent_ledger`  | Audit of what the agent has done                |

That's the full MCP agent surface — 4 tools. Earlier docs referenced `agent_schedule`/`agent_unschedule`/`agent_pause`/`agent_resume`/`agent_identity`/`agent_runs`, `list_agents`, and `hire_agent`; none of those ever had a working backend route and they were removed rather than left dangling. An MCP-spawned agent only ever updates when something (you, in chat) explicitly calls `agent_update` — it does not run itself.

## Real autonomous execution (Finch App, not MCP)

The **Finch App** (webapp) closes that gap for agents spawned there: from an agent's detail page (`/agents`), toggle **"Run autonomously"** and pick an interval (6h / 12h / 24h). Once on, that agent runs on a schedule with no chat session required — a real research turn (web search, market data, etc., the same tool guardrails as an interactive chat) that ends by logging its own findings, same as a manual `agent_update` would.

Guardrails:

* **No fund-moving authority at all.** An autonomous run cannot swap, send, stake, or touch automations — those tools are blocked outright for this execution path, not just gated behind a confirmation.
* **6-hour floor.** The fastest interval offered is every 6 hours, to keep unattended LLM/API spend bounded.
* Off by default, per agent — this is an explicit opt-in, not a background default.

This is app-only for now; there's no MCP tool to toggle it remotely.

## Related

* [Workflows](workflows.md) for automations/monitors without a full agent persona
* [Tools: agents](tools/agents.md)
* [App overview](app/overview.md)
