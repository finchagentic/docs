---
icon: bug
---

# Troubleshooting

## Tools not appearing

1. Restart the MCP client fully (not just reload window)
2. Confirm config path for your client ([install.md](install.md))
3. `npx clear-npx-cache` then restart
4. Run `finch doctor`

## Old version stuck

```bash
npx clear-npx-cache
npx -y -p @finchagentic/mcp@4.6.1 finch --version
```

Ensure every client entry pins `@4.4.1`.

## Auth / session errors

* Cloud vault/agents need `FINCH_SESSION_TOKEN`
* Local vault mode works without account for core vault tools
* Re-login from Finch App if token expired

## `web_search` / scrape weak or failing

Set `FIRECRAWL_API_KEY` in MCP env. Without it, quality falls back or fails depending on path.

## Swap refused

* Price impact over cap
* Missing estimate/preview/confirm
* Wrong family: Base → `base_mcp_*`, Robinhood Chain stocks → `rh_mcp_*` (not 0x Base tools)

## GitHub tools

Need `GITHUB_TOKEN` for search/private ops.

## Rate limits (429)

Many paths auto-retry with backoff. Wait; don’t hammer.

## Diagnose anything

```bash
finch doctor
```

## App Terminal has no tools

* Convex `finchShell` must be deployed (`npx convex dev`)
* Frontend falls back to plain chat if shell action fails
* Terminal tool set ≠ full MCP 116 tools

## API Market buyer errors

- Invalid / revoked API key  
- Budget hard-cap hit (402-style)  
- No healthy offers for model  
- Settlement disabled at soft-launch (off in **all** environments, including prod)  

## Still stuck

1. `doctor` output
2. MCP client logs
3. Package version
4. Whether local vault is on
5. Exact tool name that failed
