# Clients

**Finch MCP** (`@finchagentic/mcp`) — install once into Claude Code, Cursor, Hermes, Windsurf, Codex, and any MCP client.

## First-class install paths

| Client | Install |
|--------|---------|
| **Claude Code** | `claude mcp add finch -s user -- npx -y -p @finchagentic/mcp@4.0.0 finch-mcp` |
| **Cursor** | `finch install` or `.cursor/mcp.json` |
| **Windsurf** | `finch install` or mcp_config.json |
| **Claude Desktop** | desktop config `mcpServers` |
| **Hermes** | `hermes mcp add finch -- npx -y -p @finchagentic/mcp@4.0.0 finch-mcp` |
| **VS Code** | `.vscode/mcp.json` with `type: stdio` |
| **Zed** | `context_servers` + `source: custom` |
| **Codex / others** | stdio MCP entry with same npx args |

Full JSON: [install.md](./install.md).

## Tips

- After config changes, **full restart** the client  
- Pin version in every entry (`@finchagentic/mcp@4.0.0`)  
- Use `FINCH_TOOLS=core` if context is huge; switch to `all` when needed  
- Local vault works offline for memory/vault; chain tools still need network  

## Finch App vs MCP client

| | MCP client | Finch App |
|--|------------|-----------|
| UX | Inside your coding agent | Browser product |
| Tools | Full MCP palette | Terminal subset + Trading/Wallet/Market UI |
| Auth | Optional session token / local | Wallet SIWE session |
| Best for | Daily agentic coding + research | Trading, API Market, visual wallet |

They complement each other — same brand, different surfaces.
