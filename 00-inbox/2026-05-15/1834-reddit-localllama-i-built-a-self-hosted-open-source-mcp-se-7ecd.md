---
id: inbox_96f06d7e
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1te2jko/i_built_a_selfhosted_opensource_mcp_server_that/"
author: "/u/DanielAPO"
published_at: 2026-05-15T17:08:43+00:00
fetched_at: 2026-05-15T18:34:22.472917+00:00
content_hash: "7ecd4296c4e1cf5c4b293a8d46a017663161c8f02e152835caa0d02e3c6dec70"
lang: en
caption_quality: None
raw: true
topics: []
---

# I built a self-hosted open-source MCP server that gives any local LLM real financial data — SEC filings, 13F, insider & congressional trades, short data, FRED

One thing missing when running local models as agents: real, current data. So I built Equibles — a self-hosted MCP server that scrapes and serves public U.S. financial data and exposes it as MCP tools, so any MCP-capable client (Claude Code/Desktop, Cursor, or your own local-model agent loop) can query it directly. No cloud dependency, no API keys, no telemetry — it all runs on your machine. What it serves: SEC filings (10-K/10-Q/8-K) with full-text search 13F institutional holdings, insider (Form 3/4) and congressional trades FINRA short volume / short interest, SEC fails-to-deliver FRED economic indicators, CFTC futures positioning, CBOE VIX/put-call Daily prices + technical indicators I'm the developer. Feedback and feature suggestions are very welcome. Repo: https://github.com/daniel3303/Equibles (leave a star if you liked it :) ) &#32; submitted by &#32; /u/DanielAPO [link] &#32; [comments]