# commodities.sh

[![banner](assets/banner.png)](https://commodities.sh/mcp)

[![MCP](https://img.shields.io/badge/MCP-streamable%20HTTP-0f6e56)](https://api.commodities.sh/api/mcp)
[![30 tools](https://img.shields.io/badge/30%20tools-7%20free-0f6e56)](https://commodities.sh/mcp)
[![Free key](https://img.shields.io/badge/free%20key-no%20card-0f6e56)](https://commodities.sh/signup)
[![v0.2.0](https://img.shields.io/badge/v0.2.0-MCP%20Registry-0f6e56)](https://registry.modelcontextprotocol.io/?search=commodities-sh)

MCP server for primary-source commodities. Claude, Cursor, and any MCP host connect over streamable HTTP. The data is EIA, USDA, CFTC, IMF, Federal Reserve, USGS, FAOSTAT, and UN Comtrade. This is not real-time exchange futures. 30 tools, 7 of them free.

**[Get a free key](https://commodities.sh/signup)** — email signup, no card. 100 requests a day, 10 a minute, and 30 days of history. The 30 days is how far back the key can read. The key does not expire.

## Connect

<img src="assets/icon-connect.png" width="24" height="24" alt="" /> No account is required to connect.

```
https://api.commodities.sh/api/mcp
```

Streamable HTTP. After the server is added, call `catalog.search` and resolve a commodity name to an instrument code.

### Claude Code

One command. Add the header when you want the free key or a Pro key on the connection.

```bash
claude mcp add --transport http commodities https://api.commodities.sh/api/mcp \
  --header "Authorization: Bearer cs_free_…"
```

### Cursor and Claude Code

`type`, `url`, and `headers` go in `.cursor/mcp.json` or `.mcp.json`. The key is a transport header, not a tool argument.

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

Claude Desktop custom connectors authenticate with OAuth and have no field for this header. The bridge is on [commodities.sh/mcp](https://commodities.sh/mcp).

### What a call looks like

Every observation is labeled. Cite the fields. Do not invent a timestamp the payload does not carry.

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

<img src="assets/icon-connect.png" width="24" height="24" alt="" /> These seven reference tools are free. Six of them answer with no credential. `account.quota` reads the key already on the connection.

`catalog.list` · `catalog.search` · `calendar.get` · `trade.codes` · `minerals.list` · `cash.reports` · `account.quota`

## Free key

<img src="assets/icon-key.png" width="24" height="24" alt="" /> **[Get a free key](https://commodities.sh/signup).** The prefix is `cs_free_`. Put it in the `Authorization` header as `Bearer cs_free_…`.

A free key covers the latest print for every instrument, FX, stats, crack, crush, basis, and 30 days of history per instrument. Upgrading to Pro keeps the same key string.

A free key does not cover inventories, COT, USDA and USGS fundamentals, trade, minerals, cash bids, or decision packs. Those are Pro or x402.

## Pay per call

x402 USDC on Base, from $0.01, no account. That path is the REST API. A normal MCP host will not settle the payment for you. [How x402 works](https://commodities.sh/x402).

## Pro

<img src="assets/icon-pro.png" width="24" height="24" alt="" /> $19 a month or $180 a year. 3,000 credits each month, the same list price as x402, plus release webhooks. One credit is $0.01. The header is `Authorization: Bearer cs_live_…`. [Get a Pro key](https://commodities.sh/get-started).

The other 23 tools need that header or they return 402.

## Next

- [MCP setup, tool list, and the Desktop bridge](https://commodities.sh/mcp)
- [Pricing](https://commodities.sh/pricing)
- [llms.txt](https://commodities.sh/llms.txt) and [SKILL.md](https://commodities.sh/SKILL.md) for agents
- [Observation contract](https://commodities.sh/docs)
- Registry: [`io.github.sawftware-apps/commodities-sh`](https://registry.modelcontextprotocol.io/?search=commodities-sh)

**[Get a free key](https://commodities.sh/signup)**
