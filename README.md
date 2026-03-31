# amazon-trends-mcp

[![Amazon Trends](https://img.shields.io/badge/Amazon%20Trends-FF9900?style=flat-square)](https://trendsmcp.ai/amazon-search-trends)
[![MCP](https://img.shields.io/badge/MCP-compatible-blue?style=flat-square)](https://modelcontextprotocol.io)
[![Works with Claude](https://img.shields.io/badge/Claude-supported-orange?style=flat-square)](https://trendsmcp.ai/mcp-server-for-claude)
[![Works with Cursor](https://img.shields.io/badge/Cursor-supported-purple?style=flat-square)](https://trendsmcp.ai/mcp-server-for-cursor)

> **Amazon search trend data for AI assistants**
> Measure real consumer purchase intent. Amazon search volume reveals what people are actively looking to buy - not just research. Historical demand curves and growth signals, queryable by your AI.

**Full docs and live demo:** [https://trendsmcp.ai/amazon-search-trends](https://trendsmcp.ai/amazon-search-trends)

Part of **[Trends MCP](https://trendsmcp.ai)** -- the MCP server for live trend data across 12+ sources.
See the main repo: [https://github.com/trendsmcp/trends-mcp](https://github.com/trendsmcp/trends-mcp)

---

## Get started in 2 steps

**Step 1:** Get your free API key at **[trendsmcp.ai](https://trendsmcp.ai)**
100 requests/day, no credit card required.

**Step 2:** Add to your AI client (replace `YOUR_API_KEY`):

[**+ Add to Cursor (one click)**](cursor://anysphere.cursor-deeplink/mcp/install?name=trends-mcp&config=eyJ1cmwiOiAiaHR0cHM6Ly9hcGkudHJlbmRzbWNwLmFpL21jcCIsICJ0cmFuc3BvcnQiOiAiaHR0cCJ9)

**Cursor / Windsurf / Cline** &nbsp; (`~/.cursor/mcp.json` or equivalent)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**VS Code / GitHub Copilot** &nbsp; (`.vscode/mcp.json`)
```json
{
  "servers": {
    "trends-mcp": {
      "type": "http",
      "url": "https://api.trendsmcp.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude Desktop** &nbsp; (`claude_desktop_config.json`)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude.ai** (browser) &nbsp; Settings -> Connectors -> Add custom connector:
```
https://api.trendsmcp.ai/mcp
```

---

## Example query

After connecting, ask your AI:
```
get_trends(keyword='air fryer', source='amazon', data_mode='weekly')
```

---

## Available tools

| Tool | What it does |
|------|-------------|
| `get_trends` | Time-series for a keyword on this source |
| `get_growth` | Growth % over 1W, 1M, 3M, 6M, 1Y periods |
| `get_top_trends` | What is trending right now on this source |
| `get_ranked_trends` | Top topics ranked by volume |

---

## FAQ

### What Amazon data does Trends MCP provide?

Amazon product search volume trends - normalized interest over time reflecting consumer purchase intent. This is distinct from Google Search data because Amazon queries represent active buying intent rather than general information seeking.

### Is Amazon search data useful for e-commerce product research?

Yes. Compare product keyword demand on Amazon vs. Google to understand whether consumer intent is primarily informational or transactional. Rising Amazon search is a strong buying signal.

### Can I track a whole product category?

Yes. Use a category keyword like 'bluetooth headphones' or 'protein powder' and the signal aggregates demand across that category on Amazon.

### How is Amazon trend data normalized?

All values are normalized to a 0-100 scale for consistent comparison. An absolute volume estimate is also returned alongside the normalized signal.

---

## All data sources

Trends MCP covers 12+ sources in one connection:
Google Search, YouTube, TikTok, Reddit, Amazon, Wikipedia,
News Sentiment, Web Traffic, App Downloads, Steam, npm, and more.

Browse all: [https://trendsmcp.ai/data-sources](https://trendsmcp.ai/data-sources)


---

## Also works as a Python client

Same API key works directly in Python — no MCP host needed.

```bash
pip install amazon-trends-mcp
```

```python
import os
from amazon_trends_mcp import TrendsMcpClient, SOURCE

client = TrendsMcpClient(api_key=os.environ["TRENDSMCP_API_KEY"])

series  = client.get_trends(source=SOURCE, keyword="your keyword")
growth  = client.get_growth(source=SOURCE, keyword="your keyword", percent_growth=["1M", "3M", "12M"])
top     = client.get_top_trends(type="Amazon", limit=10)
```

Full Python docs: [trendsmcp.ai/docs](https://trendsmcp.ai/docs)
---

## License

MIT &copy; [Trends MCP](https://trendsmcp.ai)