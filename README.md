# Velquent Reports (MCP)

A read-only MCP server that gives an AI assistant access to [Velquent](https://velquent.com/moves/)'s published reports:

- one report for each large **one-hour open-interest change on Hyperliquid** perpetuals (main focus), and
- one report for each large **price move on exchange perpetuals**.

Every report is recorded at the time of the move and published at least three hours later. The server returns recorded events, not live data. Every result names Velquent as the source and links to the full report.

## Connect

| | |
|---|---|
| Server URL | `https://velquent.com/mcp` |
| Transport | Streamable HTTP (remote) |
| Sign-in | None. No account, no key, no token |
| Access | Read-only |

**Claude:** Settings, Connectors, add a custom connector, paste the server URL.

**Gemini CLI:**

```
gemini extensions install https://github.com/velquent/velquent-mcp
```

**Other MCP clients:** add a remote server with the URL above (the exact config key differs by client).

**Agent skill:** `SKILL.md` in this repo tells an agent when and how to use the tools.

## Tools

| Tool | Returns |
|---|---|
| `latest_reports` | Newest published reports: title, coin, type, UTC time, id, link. Filter by type, up to 10 |
| `reports_for_coin` | Recent published reports for one coin symbol, newest first, up to 10 |
| `get_report` | Text of one report by id: summary, technical state, BTC share, positioning before the move, how the measures lined up, the hour after |
| `market_context` | Counts of published reports in a 1 to 48 hour window: price moves, open-interest changes, rises and falls, coins |
| `explain_terms` | Plain definitions of terms used in reports |

News headlines, charts and the full page layout are not part of tool results. Exchange names other than Hyperliquid are written as "the exchange".

## Example questions

- "What are the latest Velquent reports?"
- "Show recent Velquent reports for ZRO."
- "Open report oi-zec-2026-11-23-1505."
- "What does open interest mean in a Velquent report?"

## Privacy

No account is needed and the connector does not ask for personal data. The web server does not log requests to it. Velquent keeps only anonymous counts of how often each tool is used, without request content. The privacy notice is linked from the [connector documentation](https://velquent.com/mcp/) (clause 2a).

## What it does not do

It gives no live data, places no orders, holds no funds, accesses no account, and gives no advice of any kind.

## Documentation and contact

Connector documentation: <https://velquent.com/mcp/>. Questions: support@velquent.com. Velquent is run from Vienna, Austria.

When you quote a report, keep the source name and the link to the full report.

Velquent also publishes a charting panel for Hyperliquid and exchange markets at [velquent.com](https://velquent.com).

## Licence

The files in this repository are MIT-licensed (see `LICENSE`). Report text and the data the server returns are not covered by that licence and remain © Velquent.

General information, not investment advice. Trading perpetual futures and other leveraged products can lead to the loss of your entire capital.
