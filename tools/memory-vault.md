# Memory & vault tools

## Memory

| Tool | Purpose |
|------|---------|
| `memory_add` | Store a preference or fact |
| `memory_search` | Semantic search |
| `memory_context` | Topic-bundled context |
| `memory_profile` | Profile-shaped recall |
| `memory_list` | Enumerate |
| `memory_delete` | Delete (confirm) |
| `memory_insight` | Derived insight |
| `memory_extract` | Pull memories from free text |
| `memory_consolidate` | Merge/clean |
| `memory_publish` | Public publish — irreversible |

### Example

```
User: remember I only trade Base blue chips under 2% impact
→ memory_add
→ later memory_search "risk rules" still finds it
```

## Chronicle

Time-ordered event log companion to memory/vault:

| Tool | Purpose |
|------|---------|
| `chronicle_add` | Append event |
| `chronicle_list` | List |
| `chronicle_search` | Search |
| `chronicle_stats` | Stats |

## Vault

| Tool | Purpose |
|------|---------|
| `vault_save` | Create/update versioned entry |
| `vault_read` | Read |
| `vault_list` | List |
| `vault_search` | Semantic / hybrid search |
| `vault_history` | Versions |
| `vault_diff` | Diff two versions |
| `vault_export` | Export |
| `vault_pin` | Pin for auto-context |
| `vault_tag` | Tag |
| `vault_link` | Explicit edge |
| `vault_related` | Related entries |
| `vault_delete` | Delete (confirm) |
| `vault_unpublish` | Unpublish |
| `vault_store_credential` | Encrypted secret write |
| `vault_get_credential` | Encrypted secret read |

### Example

```
User: save bull/bear ETH thesis to vault
→ vault_save type=research key=research/eth-thesis
→ vault_history shows v1
→ vault_search "ethereum outlook" finds it without keyword overlap
```

## Local vs cloud

- Local vault directory: `~/.finch/vault/`  
- Cloud vault requires session token  
- Credentials always encrypted at rest in local vault mode  

See product docs: [../memory.md](../memory.md), [../vault.md](../vault.md).
