# API Market

Two-sided **model inference** marketplace (not arbitrary HTTPS endpoints). Buyers call
OpenAI-compatible endpoints with a Finch API key; sellers list capacity from their
own provider keys. Every request is routed, metered, and (when settlement is on)
settled in USDG on Robinhood Chain.

> **Status: soft-launch (free).** Money movement is **disabled** — `MARKET_SETTLEMENT_LIVE`
> is off. Authenticated keys get free routed inference; only the ledger + activity
> rows write. Flip settlement only after the live checklist.

## Base URL

```
https://app.finchagentic.com/v1
```

This is a same-origin Vercel rewrite that proxies to the Convex backend. Buyers
**never** see a Convex hostname. (`api.finch.market` is not DNS-live — do not
document it as the user-facing base.)

## Buyer

### Tabs

| Tab | Purpose |
|-----|---------|
| Overview | Spend, savings, health |
| API Keys | Create / revoke keys (`finch_sk_*`) |
| Budgets | Hard + alert caps, max price |
| Activity | Request ledger |
| Connect | OpenAI-compatible snippets |
| Docs | This reference, in-app |

### Quick start

```bash
# 1. Create a key in the app: API Market → API Keys → Create
#    It looks like: finch_sk_xxxx

# 2. Call the endpoint
export FINCH_API_KEY="finch_sk_xxxx"

curl https://app.finchagentic.com/v1/chat/completions \
  -H "Authorization: Bearer $FINCH_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "claude-fable-5",
    "messages": [{"role": "user", "content": "Hello"}],
    "max_tokens": 256
  }'
```

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://app.finchagentic.com/v1",
    api_key="finch_sk_xxxx",
)

resp = client.chat.completions.create(
    model="claude-fable-5",
    messages=[{"role": "user", "content": "Hello"}],
    max_tokens=256,
)
print(resp.choices[0].message.content)
```

```javascript
import OpenAI from "openai";

const client = new OpenAI({
  baseURL: "https://app.finchagentic.com/v1",
  apiKey: "finch_sk_xxxx",
});

const resp = await client.chat.completions.create({
  model: "claude-fable-5",
  messages: [{ role: "user", content: "Hello" }],
  max_tokens: 256,
});
console.log(resp.choices[0].message.content);
```

### Endpoints

| Method | Path | Purpose |
|--------|------|---------|
| GET | `/v1/models` | List live models + best offer |
| POST | `/v1/chat/completions` | OpenAI-compatible chat |

The request shape is the standard OpenAI `chat.completions` body. Pick any `model`
id from `/v1/models`.

### Routing

1. Authenticate API key (or `x402` wallet path where enabled)
2. Rank healthy offers by price + budget + filters
3. Proxy to the seller's upstream provider
4. Meter real tokens in / out
5. Settle buyer → seller (USDG · Robinhood Chain) — **off during soft-launch**

### Soft-launch limits (enforced)

| Limit | Value |
|-------|-------|
| Requests per key / day | 80 |
| Ledger cost per key / day | $5 |
| `max_tokens` soft cap | 2048 |
| Max keys per user | 8 |
| Settlement | **disabled** (USDG does not move) |

These are hard caps, not suggestions — a request over budget returns an honest
`402`-style error, not a silent fail.

## Seller

### Tabs

| Tab | Purpose |
|-----|---------|
| Overview | Earnings / health |
| Offers | Live listings |
| Create | Discover models from a provider key, set multiplier |
| Sales | Recent fills |

### Bring-your-own provider

A seller pastes their **own** provider key (the platform chat key is separate from
the seller key). Supported allowlist includes **Bankr**, **Venice**, **OpenAI**,
**Anthropic**, **OpenRouter**.

> **Platform liquidity:** at soft-launch the catalog is seeded from **Bankr** live
> models (`seedPlatformLiquidity`) so the board is not empty. Those are real,
> callable routes — not dummy rows. Seller-published offers layer on top.

## Pricing honesty

- Catalog list prices are **reference only**
- Offer price = seller choice (often `list × multiplier`)
- Discount = real `1 − buyerCost / listCost` — never invent savings
- UI numbers come from settlement ledger rows

## Settlement (when enabled)

- Asset: **USDG** on **Robinhood Chain** (`4663`)
- Payout to seller custodial execution wallet
- Only after `MARKET_SETTLEMENT_LIVE=1` on prod, post dry-run

## Docs inside app

`/apimarket/docs` — same content as this file, rendered in the app.

## Non-goals

- Fake "Soon" catalog rows presented as live
- Arbitrary URL marketplace as primary UI
- Media / meme markets as core path
