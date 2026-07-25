# Clients

Finch MCP works anywhere the Model Context Protocol runs.

## First-class install paths

| Client | Install |
|--------|---------|
| **Claude Code** | `claude mcp add noelclaw -s user -- npx -y -p @noelclaw/mcp@3.44.0 noelclaw-mcp` |
| **Cursor** | `noelclaw install` or `.cursor/mcp.json` |
| **Windsurf** | `noelclaw install` or mcp_config.json |
| **Claude Desktop** | desktop config `mcpServers` |
| **Hermes** | `hermes mcp add noelclaw -- npx -y -p @noelclaw/mcp@3.44.0 noelclaw-mcp` |
| **VS Code** | `.vscode/mcp.json` with `type: stdio` |
| **Zed** | `context_servers` + `source: custom` |
| **Codex / Aeon / others** | stdio MCP entry with same npx args |

Full JSON: [install.md](./install.md).

## Tips

- After config changes, **full restart** the client  
- Pin version in every entry  
- Use `NOELCLAW_TOOLS=core` if context is huge; switch to `all` when needed  
- Local vault works offline for memory/vault; chain tools still need network  

## Finch App vs MCP client

| | MCP client | Finch App |
|--|------------|-----------|
| UX | Inside your coding agent | Browser product |
| Tools | Full MCP palette | Terminal subset + Trading/Wallet/Market UI |
| Auth | Optional session token / local | Wallet SIWE session |
| Best for | Daily agentic coding + research | Trading, API Market, visual wallet |

They complement each other — same brand, different surfaces.
