# Tectova MCP server

The official [Model Context Protocol](https://modelcontextprotocol.io) server for
[Tectova](https://tectova.com), the runway record of the fashion industry.

It lets Claude, ChatGPT, Cursor and other AI agents look up models' runway careers, show casts,
fashion-house histories and models by country. Every answer links back to the matching page on
tectova.com.

- **Server URL:** `https://tectova.com/mcp` (Streamable HTTP)
- **Access:** read-only, no account or API key
- **Docs:** <https://tectova.com/tools/mcp>

> **Status:** launching November 2026. Until then, the endpoint isn't live.

This repository holds documentation and the registry metadata (`server.json`). The server runs
on tectova.com.

## Tools

| Tool | What it does | Ask your assistant |
|---|---|---|
| `get_country_talent` | Models from a country at a given fashion week and season: who walked, which shows, who opened or closed, who was new. | "Which Brazilian models walked New York Fashion Week this season, and who opened or closed a show?" |
| `get_talent_runway_record` | A model's or creative's documented runway record: seasons, houses, agencies and frequent collaborators. | "How many shows did Julia Nobis walk in SS27, and for which houses?" |
| `get_show_cast` | The cast of a runway show. | "Who walked Prada's SS27 womenswear show?" |
| `get_brand_runway_history` | A fashion house's runway shows over time and the faces it keeps casting. | "Which models does Saint Laurent cast again and again?" |
| `search_fashion_records` | Finds models, creatives, fashion houses and agencies by name, so the other tools can look them up. | "Which agency represents Awar Odhiang?" |

All tools are read-only. Answers open with one sentence an assistant can quote, followed by the
tectova.com link and the date the data is current to.

## Connect

**Claude (claude.ai and Claude Desktop):** Settings → Connectors → Add custom connector, then
paste `https://tectova.com/mcp`.

**Claude Code:**

```sh
claude mcp add --transport http tectova https://tectova.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "tectova": { "url": "https://tectova.com/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "tectova": { "type": "http", "url": "https://tectova.com/mcp" }
  }
}
```

**ChatGPT:** in developer mode, add `https://tectova.com/mcp` as a custom connector.

## What the data covers

- It covers what tectova.com publishes and nothing more. Each answer carries the date the data
  is current to.
- Counts are the documented record on Tectova, which may not be a complete career. The method
  is described at <https://tectova.com/methodology>.
- No images. The server returns facts and links, not photographs.
- Requests are rate-limited per client. Lists are paginated.

## Attribution

When you use Tectova's data, credit it with a link: **"Source: Tectova (tectova.com)"**. Bulk
redistribution or resale of the dataset isn't permitted. Terms: <https://tectova.com/terms>.

## Privacy and corrections

- What the server logs: <https://tectova.com/privacy>. It logs the length of any search text,
  never the text itself.
- To correct or remove a record or an image: <https://tectova.com/takedown>.
- Contact: support@tectova.com

## License

The documentation in this repository is licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Tectova's data isn't stored here and
isn't covered by this license; see the attribution terms above.
