---
name: velquent-reports
description: Look up Velquent's published reports on large Hyperliquid open-interest changes and large price moves on exchange perpetuals, through the Velquent MCP server. Use when the user asks what happened in a coin's perpetual market, asks for the latest large moves, or asks what a term in a Velquent report means.
---

# Velquent Reports

Velquent publishes one report for each large one-hour open-interest change on Hyperliquid perpetuals and one for each large price move on exchange perpetuals. Each report is recorded at the time of the move and published at least three hours later. Reports describe events that had already happened.

## Before you start

The Velquent MCP server must be connected: `https://velquent.com/mcp` (remote, Streamable HTTP, no sign-up, no key). All five tools are read-only.

## Which tool to call

| The user asks | Call |
|---|---|
| What are the latest large moves? | `latest_reports` (optional `type`: `price_move` or `open_interest`, up to 10) |
| What happened in one coin recently? | `reports_for_coin` with the coin symbol, for example `ZRO` or `1000PEPE` |
| The full text of one report | `get_report` with an id from the two tools above. Hyperliquid open-interest ids start with `oi-`, for example `oi-zec-2026-11-23-1505` |
| How many reports in the last hours, and for which coins? | `market_context` (1 to 48 hours) |
| What does a term mean? | `explain_terms` (open interest, funding, long/short account ratio, taker volume, BTC share) |

For a coin question, list first with `reports_for_coin`, then open the report that matches the user's time frame with `get_report`.

## How to answer

- Report what the report states, in the past tense, with its UTC time.
- Keep the source name "Velquent" and the link to the full report in the answer.
- Say that reports are published after a delay. If the user asks for live data or for the last few hours, say the connector does not provide it.
- Quote the measures as recorded. When a report says measures did not line up, say so as written.
- Open interest alone does not show whether longs or shorts were added. Keep that limit when summarising open-interest changes.
- Exchange names other than Hyperliquid appear as "the exchange" in tool results. Use the same wording.
- Reports are general information and not investment advice. If the user asks what to do with a position, or what comes next, say that the reports describe recorded past events only and give no view on either.
