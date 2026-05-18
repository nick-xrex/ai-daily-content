---
id: inbox_96f06d7e
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_96f06d7e]]"
title: "I built a self-hosted open-source MCP server that gives any local LLM real financial data — SEC filings, 13F, insider &amp; congressional trades, short data, FRED"
url: https://www.reddit.com/r/LocalLLaMA/comments/1te2jko/i_built_a_selfhosted_opensource_mcp_server_that/
source: reddit-localllama
published_at: 2026-05-15T17:08:43+00:00
fetched_at: 2026-05-18T03:59:24.962205+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者發佈 Equibles，一個自託管開源 MCP 伺服器，為本地 LLM 提供即時美國金融資料。該伺服器無需雲端依賴、API key 或遙測，所有資料爬蟲與服務在使用者機器上運行。Equibles 整合多種金融資料來源：SEC 10-K/10-Q/8-K（全文搜尋）、13F 機構持股、內線交易（Form 3/4）、國會交易、FINRA 空頭交易量、FRED 經濟指標、CFTC 期貨部位、CBOE VIX、每日股價與技術指標。任何 MCP capable client（Claude Code、Cursor、自訂代理）都能直接查詢，無轉換成本。此工具特別適合需要隱私優先、實時、可靠金融資料的本地 AI 代理。"
key_points:
  - "完全自託管、無 API key、無遙測：金融資料爬蟲與 MCP server 皆在本地運行，無三方依賴"
  - "支援 SEC 10-K/10-Q/8-K、13F 機構持股、Form 3/4 內線交易、FINRA 空頭、FRED 經濟指標、CFTC 期貨、VIX 選擇權等八類金融資料"
  - "相容任何 MCP client（Claude Code/Desktop、Cursor、自訂代理）直接查詢，無協議轉換開銷"
tags: [mcp, financial-data, self-hosted, open-source, local-agent]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## I built a self-hosted open-source MCP server that gives any local LLM real financial data — SEC filings, 13F, insider & congressional trades, short data, FRED

開發者發佈 Equibles，一個自託管開源 MCP 伺服器，為本地 LLM 提供即時美國金融資料。該伺服器無需雲端依賴、API key 或遙測，所有資料爬蟲與服務在使用者機器上運行。Equibles 整合多種金融資料來源：SEC 10-K/10-Q/8-K（全文搜尋）、13F 機構持股、內線交易（Form 3/4）、國會交易、FINRA 空頭交易量、FRED 經濟指標、CFTC 期貨部位、CBOE VIX、每日股價與技術指標。任何 MCP capable client（Claude Code、Cursor、自訂代理）都能直接查詢，無轉換成本。此工具特別適合需要隱私優先、實時、可靠金融資料的本地 AI 代理。

### 重點
- 完全自託管、無 API key、無遙測：金融資料爬蟲與 MCP server 皆在本地運行，無三方依賴
- 支援 SEC 10-K/10-Q/8-K、13F 機構持股、Form 3/4 內線交易、FINRA 空頭、FRED 經濟指標、CFTC 期貨、VIX 選擇權等八類金融資料
- 相容任何 MCP client（Claude Code/Desktop、Cursor、自訂代理）直接查詢，無協議轉換開銷

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1te2jko/i_built_a_selfhosted_opensource_mcp_server_that/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I built a self-hosted open-source MCP server that gives any local LLM real financial data — SEC filings, 13F, insider & congressional trades, short data, FRED

One thing missing when running local models as agents: real, current data. So I built Equibles — a self-hosted MCP server that scrapes and serves public U.S. financial data and exposes it as MCP tools, so any MCP-capable client (Claude Code/Desktop, Cursor, or your own local-model agent loop) can query it directly. No cloud dependency, no API keys, no telemetry — it all runs on your machine. What it serves: SEC filings (10-K/10-Q/8-K) with full-text search 13F institutional holdings, insider (Form 3/4) and congressional trades FINRA short volume / short interest, SEC fails-to-deliver FRED economic indicators, CFTC futures positioning, CBOE VIX/put-call Daily prices + technical indicators I'm the developer. Feedback and feature suggestions are very welcome. Repo: https://github.com/daniel3303/Equibles (leave a star if you liked it :) ) &#32; submitted by &#32; /u/DanielAPO [link] &#32; [comments]

</details>