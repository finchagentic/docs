# CLI

The npm package exposes:

| Binary | Role |
|--------|------|
| `noelclaw` | User CLI (doctor, setup, vault, install, …) |
| `noelclaw-mcp` | MCP stdio server entry |

Product brand is **Finch**; binary names remain technical.

## Common commands

```bash
# Configure clients
noelclaw install

# Health
noelclaw doctor

# Local vault + memory wizard
noelclaw setup

# Inspect vault path / contents
noelclaw vault

# List tools (after global install or via npx)
noelclaw tools   # if available in your version
```

Via npx without global install:

```bash
npx -y -p @noelclaw/mcp@3.44.0 noelclaw doctor
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
noelclaw --version
# should match pinned package, e.g. 3.44.0
```

If clients load a stale binary: `npx clear-npx-cache` and restart the client.
