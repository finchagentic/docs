# CLI

The npm package exposes:

| Binary | Role |
|--------|------|
| `finch` | User CLI (doctor, setup, vault, install, …) |
| `finch-mcp` | MCP stdio server entry |

## Common commands

```bash
# Configure clients
finch install

# Health
finch doctor

# Local vault + memory wizard
finch setup

# Inspect vault path / contents
finch vault
```

Via npx without global install:

```bash
npx -y -p @finchagentic/mcp@4.0.0 finch doctor
npx -y -p @finchagentic/mcp@4.0.0 finch setup
```

## Doctor expectations

A healthy doctor output typically shows:

- Backend reachable (if using cloud session)  
- Auth / session state  
- Local vault on/off  
- Tool palette mode (`core` vs `all`)  
- Optional keys present or not (Firecrawl, GitHub, …)  

Zero critical reds is the goal. Warnings for optional keys are normal.

## Version

```bash
finch --version
# should match pinned package, e.g. 4.0.0
```

If clients load a stale binary: `npx clear-npx-cache` and restart the client.
