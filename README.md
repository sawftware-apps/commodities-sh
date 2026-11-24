# commodities.sh

[![banner](assets/banner.png)](https://commodities.sh/mcp)

[![MCP](https://img.shields.io/badge/MCP-streamable%20HTTP-0f6e56)](https://api.commodities.sh/api/mcp)
[![30 tools](https://img.shields.io/badge/30%20tools-7%20free-0f6e56)](https://commodities.sh/mcp)
[![Free key](https://img.shields.io/badge/free%20key-no%20card-0f6e56)](https://commodities.sh/signup)
[![v0.2.0](https://img.shields.io/badge/v0.2.0-MCP%20Registry-0f6e56)](https://registry.modelcontextprotocol.io/?search=commodities-sh)

Ask Claude or Cursor for WTI, corn basis, or a crack spread and get the official print, with the source on the observation. EIA, USDA, CFTC, IMF, the Fed, USGS, FAOSTAT, and UN Comtrade. Not exchange futures.

**[Get a free key](https://commodities.sh/signup)** — email signup, no card. 50 requests a day, 10 a minute, and 30 days of history. The 30 days is how far back the key can read. The key does not expire.

## Connect

<img src="assets/icon-connect.png" width="24" height="24" alt="" />

```
https://api.commodities.sh/api/mcp
```

Put the key in the `Authorization` header. Then call `catalog.search` and turn a commodity name into an instrument code.

### Claude Code

```bash
claude mcp add --transport http commodities https://api.commodities.sh/api/mcp \
  --header "Authorization: Bearer cs_free_…"
```

### Cursor and Claude Code

```json
{
  "mcpServers": {
    "commodities": {
      "type": "http",
      "url": "https://api.commodities.sh/api/mcp",
      "headers": {
        "Authorization": "Bearer cs_free_…"
      }
    }
  }
}
```

Claude Desktop custom connectors have no field for this header. The bridge is on [commodities.sh/mcp](https://commodities.sh/mcp).

### What a call looks like

Cite the fields the payload carries.

```json
{
  "id": "obs_6363a358d0f6971751334765",
  "instrument": "CL",
  "name": "WTI Cushing",
  "value": 78.42,
  "unit": "USD/bbl",
  "as_of": "2026-07-09",
  "freshness_class": "eod",
  "quality": "official",
  "source": { "name": "EIA", "series_id": "PET.RWTC.D" },
  "cite": "EIA PET.RWTC.D as of 2026-07-09 (eod, official)"
}
```

## Free tools

`catalog.list` · `catalog.search` · `calendar.get` · `trade.codes` · `minerals.list` · `cash.reports` · `account.quota`

Six answer with no credential. `account.quota` reads the key already on the connection.

## Free key

<img src="assets/icon-key.png" width="24" height="24" alt="" /> **[Get a free key](https://commodities.sh/signup).** Prefix `cs_free_`.

A free key covers the latest print for every instrument, FX, stats, crack, crush, basis, and 30 days of history. Inventories, COT, USDA and USGS fundamentals, trade, minerals, cash bids, and decision packs are Pro or x402. Upgrading to Pro with the same email keeps the same key string.

x402 is USDC on Base from $0.01, on the REST API. A normal MCP host will not settle it. [How x402 works](https://commodities.sh/x402).

## Pro

<img src="assets/icon-pro.png" width="24" height="24" alt="" /> $19 a month or $180 a year. 3,000 credits each month, plus release webhooks. One credit is $0.01. [Get a Pro key](https://commodities.sh/get-started).

## Next

- [MCP setup, tool list, and the Desktop bridge](https://commodities.sh/mcp)
- [Pricing](https://commodities.sh/pricing)
- [llms.txt](https://commodities.sh/llms.txt) and [SKILL.md](https://commodities.sh/SKILL.md) for agents
- [Observation contract](https://commodities.sh/docs)
- Registry: [`io.github.sawftware-apps/commodities-sh`](https://registry.modelcontextprotocol.io/?search=commodities-sh)
