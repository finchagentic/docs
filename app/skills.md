---
icon: chart-sine
---

# Skills

Skills marketplace lets builders publish and install reusable agent skills.

## Routes

| Path              | Purpose          |
| ----------------- | ---------------- |
| `/skills`         | Browse / install |
| `/skills/publish` | Publish a skill  |

## Relationship to MCP

* App skills are productized packs for Terminal / agents
* MCP tools are the low-level runtime primitives
* A skill may orchestrate multiple tools with a prompt + policy

## Publisher expectations

* Clear description and trigger
* No secret leakage in skill text
* Honest capabilities (don’t claim tools that aren’t wired)
