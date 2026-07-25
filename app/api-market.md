# API Market

Two-sided **model inference** market (not arbitrary HTTPS endpoints).

## Buyer

Surplus-style sections:

| Tab | Purpose |
|-----|---------|
| Overview | Spend, savings, health |
| API Keys | Create / revoke keys |
| Budgets | Hard + alert caps, max price |
| Activity | Request ledger |
| Connect | OpenAI-compatible snippets |

### Call shape

```http
POST /v1/chat/completions
Authorization: Bearer <api_key>
```

OpenAI SDKs work with the Finch base URL (product may show `api.finch.market` in UI copy while infrastructure hostnames catch up).

### Routing

1. Auth key (or x402 wallet path where enabled)  
2. Rank healthy offers by price + budget + filters  
3. Proxy to seller upstream  
4. Meter real tokens  
5. Settle buyer → seller (USDG · Robinhood Chain)

## Seller

| Tab | Purpose |
|-----|---------|
| Overview | Earnings / health |
| Offers | Live listings |
| Create | Discover models from provider key, set multiplier |
| Sales | Recent fills |

Supported provider allowlists include Bankr, Venice, OpenAI, Anthropic, OpenRouter (paste your own key — platform chat key ≠ seller key).

## Pricing honesty

- Catalog list prices are **reference only**  
- Offer price = seller choice (often list × multiplier)  
- Discount = real `1 − buyerCost/listCost` — never invent savings  
- UI numbers come from settlement ledger rows  

## Settlement

- Asset: USDG on Robinhood Chain (`4663`)  
- Payout to seller custodial execution wallet  

## Docs inside app

`/apimarket/docs` — endpoint reference for buyers.

## Non-goals

- Fake “Soon” catalog rows presented as live  
- Arbitrary URL marketplace as primary UI  
- Media / meme markets as core path  
