# Install

Always pin the package version. Never use `@latest`.

**Current pin:** `@noelclaw/mcp@3.44.0`

---

## One-command installer

Detects common desktop MCP clients and writes config:

```bash
npx -y -p @noelclaw/mcp@3.44.0 noelclaw install
```

Claude Code uses a dedicated command (config path differs):

```bash
claude mcp add noelclaw -s user -- npx -y -p @noelclaw/mcp@3.44.0 noelclaw-mcp
```

---

## Client configs

### Claude Desktop / Cursor / Windsurf

```json
{
  "mcpServers": {
    "noelclaw": {
      "command": "npx",
      "args": ["-y", "-p", "@noelclaw/mcp@3.44.0", "noelclaw-mcp"]
    }
  }
}
```

### Hermes

```bash
hermes mcp add noelclaw -- npx -y -p @noelclaw/mcp@3.44.0 noelclaw-mcp
```

### VS Code

`mcp.json` uses `servers` + `"type": "stdio"`:

```json
{
  "servers": {
    "noelclaw": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "-p", "@noelclaw/mcp@3.44.0", "noelclaw-mcp"]
    }
  }
}
```

### Zed

`settings.json` → `context_servers`:

```json
{
  "context_servers": {
    "noelclaw": {
      "source": "custom",
      "command": "npx",
      "args": ["-y", "-p", "@noelclaw/mcp@3.44.0", "noelclaw-mcp"]
    }
  }
}
```

---

## Config file paths

| Client | Path |
|--------|------|
| Claude Desktop (Mac) | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Claude Desktop (Windows) | `%APPDATA%\Claude\claude_desktop_config.json` |
| Cursor | `.cursor/mcp.json` |
| Windsurf | `~/.codeium/windsurf/mcp_config.json` |
| VS Code | `.vscode/mcp.json` |
| Zed | `.config/zed/settings.json` |

---

## Optional env in the MCP entry

```json
{
  "mcpServers": {
    "noelclaw": {
      "command": "npx",
      "args": ["-y", "-p", "@noelclaw/mcp@3.44.0", "noelclaw-mcp"],
      "env": {
        "NOELCLAW_SESSION_TOKEN": "noel_…",
        "NOELCLAW_TOOLS": "all",
        "FIRECRAWL_API_KEY": "fc-…"
      }
    }
  }
}
```

| Variable | Why |
|----------|-----|
| `NOELCLAW_SESSION_TOKEN` | Cloud vault / agents / account-bound tools |
| `NOELCLAW_TOOLS` | `core` (default) or `all` / `defi` palettes |
| `FIRECRAWL_API_KEY` | Higher-quality web scrape/search |

No LLM API key is required for tools to run — your MCP client’s model is the brain.

See [configuration.md](./configuration.md).

---

## After install

1. Fully restart the MCP client  
2. `noelclaw doctor`  
3. If an old version sticks: `npx clear-npx-cache` then restart  

---

## Global CLI (optional)

```bash
npm install -g @noelclaw/mcp@3.44.0
noelclaw doctor
noelclaw setup
noelclaw vault
```

Binary names: `noelclaw`, `noelclaw-mcp` (technical). Product brand remains **Finch**.
