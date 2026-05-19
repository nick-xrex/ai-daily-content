---
id: inbox_4b4cc127
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_4b4cc127]]"
title: "GlobalPulse MCP — built by a solo builder, registered on Anthropic’s official MCP registry"
url: https://gpavancitizen.medium.com/globalpulse-mcp-built-by-a-solo-builder-registered-on-anthropics-official-mcp-registry-dcf956b346b6?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-18T13:00:15+00:00
fetched_at: 2026-05-19T02:31:05.343350+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pavan Kumar Galiveeti（無主動編碼經驗）開發並發佈 GlobalPulse MCP——一套開源 Model Context Protocol 伺服器，整合 6 個全球 API（World Bank、Open-Meteo、UN GDACS、OpenSky、UN Comtrade、REST Countries），提供 11 個工具，無需 API 金鑰或訂閱。所有 API 先在 Postman 實測驗證，設計重點為雙輸出格式（Markdown 人類可讀 + JSON 程式化）、Zod 輸入驗證、可復原的錯誤訊息。已公開部署於 Railway（https://globalpulse-mcp-production.up.railway.app/mcp），任何 MCP 相容助手（Claude、Cursor、Windsurf）皆可存取。填補了全球宏觀資料（貿易流、災害情報、氣候）在 AI agent 中的空白。"
key_points:
  - "11 工具、6 個全球 API、無認證、無訂閱成本；涵蓋 World Bank、Open-Meteo、UN GDACS、OpenSky、UN Comtrade、REST Countries"
  - "設計三項關鍵決策：(1) 雙輸出格式（markdown + JSON）應對人類和程式化使用；(2) Zod 預驗證避免沉默失敗；(3) 具體錯誤訊息讓 agent 自動恢復"
  - "Railway 公開部署，無冷啟，基於 HTTP transport 實現全球可達；入選 Anthropic 官方 MCP registry"
tags: [mcp, open-source, global-data, agents, railway-deployment]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## GlobalPulse MCP — built by a solo builder, registered on Anthropic’s official MCP registry

Pavan Kumar Galiveeti（無主動編碼經驗）開發並發佈 GlobalPulse MCP——一套開源 Model Context Protocol 伺服器，整合 6 個全球 API（World Bank、Open-Meteo、UN GDACS、OpenSky、UN Comtrade、REST Countries），提供 11 個工具，無需 API 金鑰或訂閱。所有 API 先在 Postman 實測驗證，設計重點為雙輸出格式（Markdown 人類可讀 + JSON 程式化）、Zod 輸入驗證、可復原的錯誤訊息。已公開部署於 Railway（https://globalpulse-mcp-production.up.railway.app/mcp），任何 MCP 相容助手（Claude、Cursor、Windsurf）皆可存取。填補了全球宏觀資料（貿易流、災害情報、氣候）在 AI agent 中的空白。

### 重點
- 11 工具、6 個全球 API、無認證、無訂閱成本；涵蓋 World Bank、Open-Meteo、UN GDACS、OpenSky、UN Comtrade、REST Countries
- 設計三項關鍵決策：(1) 雙輸出格式（markdown + JSON）應對人類和程式化使用；(2) Zod 預驗證避免沉默失敗；(3) 具體錯誤訊息讓 agent 自動恢復
- Railway 公開部署，無冷啟，基於 HTTP transport 實現全球可達；入選 Anthropic 官方 MCP registry

**原文：** [medium-tag-llm](https://gpavancitizen.medium.com/globalpulse-mcp-built-by-a-solo-builder-registered-on-anthropics-official-mcp-registry-dcf956b346b6?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Pavan Kumar Galiveeti"
published_at: 2026-05-18T13:00:15+00:00
fetched_at: 2026-05-18T18:50:59.262235+00:00
content_hash: "c96ee9998db1d3b3d29cb484bff1fa93ef43cb083376757e4e472f1d65840770"
lang: en
caption_quality: None
raw: true
topics: []
---

# GlobalPulse MCP — built by a solo builder, registered on Anthropic’s official MCP registry

How I identified, validated, and shipped an open-source MCP server for institutional-grade global data &#x2014; with zero active coding experience Continue reading on Medium »

</details>