---
icon: instalod
---

# Install

Always pin the package version. Never use `@latest`.

**Current pin:** `@finchagentic/mcp@4.6.2`

***

## One-command installer

Detects common desktop MCP clients and writes config:

```bash
npx -y -p @finchagentic/mcp@4.6.2 finch install
```

### Claude Code

```bash
claude mcp add finch -s user -- npx -y -p @finchagentic/mcp@4.6.2 finch-mcp
```

***

## Client configs

### Claude Desktop / Cursor / Windsurf

```json
{
  "mcpServers": {
    "finch": {
      "command": "npx",
      "args": ["-y", "-p", "@finchagentic/mcp@4.6.2", "finch-mcp"]
    }
  }
}
```

### Hermes

```bash
hermes mcp add finch -- npx -y -p @finchagentic/mcp@4.6.2 finch-mcp
```

### VS Code

`mcp.json` uses `servers` + `"type": "stdio"`:

```json
{
  "servers": {
    "finch": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "-p", "@finchagentic/mcp@4.6.2", "finch-mcp"]
    }
  }
}
```

### Zed

`settings.json` → `context_servers`:

```json
{
  "context_servers": {
    "finch": {
      "source": "custom",
      "command": "npx",
      "args": ["-y", "-p", "@finchagentic/mcp@4.6.2", "finch-mcp"]
    }
  }
}
```

***

## Config file paths

| Client                   | Path                                                              |
| ------------------------ | ----------------------------------------------------------------- |
| Claude Desktop (Mac)     | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Claude Desktop (Windows) | `%APPDATA%\Claude\claude_desktop_config.json`                     |
| Cursor                   | `.cursor/mcp.json`                                                |
| Windsurf                 | `~/.codeium/windsurf/mcp_config.json`                             |
| VS Code                  | `.vscode/mcp.json`                                                |
| Zed                      | `.config/zed/settings.json`                                       |

***

## Optional env in the MCP entry

```json
{
  "mcpServers": {
    "finch": {
      "command": "npx",
      "args": ["-y", "-p", "@finchagentic/mcp@4.6.2", "finch-mcp"],
      "env": {
        "FINCH_SESSION_TOKEN": "…",
        "FINCH_TOOLS": "all",
        "FIRECRAWL_API_KEY": "fc-…"
      }
    }
  }
}
```

| Variable              | Why                                         |
| --------------------- | ------------------------------------------- |
| `FINCH_SESSION_TOKEN` | Cloud vault / agents / account-bound tools  |
| `FINCH_TOOLS`         | `core` (default) or `all` / `defi` palettes |
| `FIRECRAWL_API_KEY`   | Higher-quality web scrape/search            |

No LLM API key is required for tools to run — your MCP client’s model is the brain.

See [configuration.md](configuration.md).

***

## After install

1. Fully restart the MCP client
2. `finch doctor`
3. If an old version sticks: `npx clear-npx-cache` then restart

***

## Global CLI (optional)

```bash
npm install -g @finchagentic/mcp@4.6.2
finch doctor
finch setup
finch vault
```

Binaries: `finch` · `finch-mcp`.
