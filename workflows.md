---
icon: chart-diagram
---

# Workflows

Anything that **continues after the chat ends**: automations, monitors, packets, scheduled research.

## Automations

Plain-English recurring jobs.

```
create an automation: every Monday 09:00 UTC research Base AI infra and save to vault
list my automations
pause automation <id>
```

| Tool                  | Role             |
| --------------------- | ---------------- |
| `create_automation`   | Create           |
| `list_automations`    | List             |
| `pause_automation`    | Pause            |
| `delete_automation`   | Delete (confirm) |
| `get_automation_runs` | History          |
| `run_automation`      | Manual run       |

## Monitors

Server-side scheduled jobs that outlive the MCP process.

| Tool                | Role                   |
| ------------------- | ---------------------- |
| `list_monitors`     | List                   |
| `cancel_monitor`    | Cancel                 |
| `schedule_research` | Research on a schedule |

**Always confirm** before creating: schedule, actions, cost, storage location.

## Packets

Reusable task packets.

| Tool            | Role    |
| --------------- | ------- |
| `packet_create` | Define  |
| `packet_run`    | Execute |
| `packet_list`   | List    |
| `packet_share`  | Share   |

## Deep research

Multi-stage research that can land in vault.

```
deep research on AI agent infra, save to vault
compare these two research reports
continue that research chain
```

| Tool                        | Role                 |
| --------------------------- | -------------------- |
| `deep_research`             | Multi-stage research |
| `research_compare`          | Compare              |
| `research_chain`            | Chain / continue     |
| `web_search` / `web_scrape` | Raw web              |

Default research modes prefer **sources** without needing a host LLM key. Report modes that write prose server-side may need a provider key.

## Playbooks

| Tool             | Role |
| ---------------- | ---- |
| `list_playbooks` | List |
| `run_playbook`   | Run  |

## Cost honesty

Disclose before schedules:

* Each run may call external LLM / Firecrawl
* Outputs may write to vault or cloud tables
* Jobs continue after you close the client

See [security.md](security.md) boundaries 6–7.
