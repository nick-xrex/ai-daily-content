---
id: inbox_699ec5fb
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-infoq-architecture-webmcp-standard-proposal-for-agentic-web-ec39]]"
title: "WebMCP Standard Proposal for Agentic Web Actuation Now Available in Chrome (Origin Trials)"
url: https://www.infoq.com/news/2026/06/webmcp-web-agent-standard-chrome/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-13T03:32:00+00:00
fetched_at: 2026-06-13T22:06:17.822086+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 宣佈 WebMCP（Web Model Context Protocol）標準提案進入 Chrome 149 Origin Trials 階段。WebMCP 讓網站向瀏覽器內的 AI agent 暴露工具接口（JavaScript 函數、HTML 表單等），使 agent 可以直接呼叫這些函數而非透過 DOM 解析或螢幕讀取，大幅提升可靠性與效能。這標誌著 web 與 AI agent 互動從「猜測」進入「標準化 API」的新時代。"
key_points:
  - "WebMCP 在 Chrome 149 進入 Origin Trials，讓網站向 agent 暴露工具接口（JS 函數、HTML 表單等）"
  - "避免不可靠的 DOM 解析與螢幕讀取，改為直接函數呼叫，大幅提升 agent 可靠性"
  - "標準化的 agent-to-web 互動協議，類似 MCP 在 desktop 的角色，為 web agent 奠定基礎設施"
tags: [webmcp, agents, web-standards, chrome, browser]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## WebMCP Standard Proposal for Agentic Web Actuation Now Available in Chrome (Origin Trials)

Google 宣佈 WebMCP（Web Model Context Protocol）標準提案進入 Chrome 149 Origin Trials 階段。WebMCP 讓網站向瀏覽器內的 AI agent 暴露工具接口（JavaScript 函數、HTML 表單等），使 agent 可以直接呼叫這些函數而非透過 DOM 解析或螢幕讀取，大幅提升可靠性與效能。這標誌著 web 與 AI agent 互動從「猜測」進入「標準化 API」的新時代。

### 重點
- WebMCP 在 Chrome 149 進入 Origin Trials，讓網站向 agent 暴露工具接口（JS 函數、HTML 表單等）
- 避免不可靠的 DOM 解析與螢幕讀取，改為直接函數呼叫，大幅提升 agent 可靠性
- 標準化的 agent-to-web 互動協議，類似 MCP 在 desktop 的角色，為 web agent 奠定基礎設施

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/webmcp-web-agent-standard-chrome/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google recently announced that WebMCP is entering origin trials in Chrome 149. The new WebMCP standard proposal lets sites expose tools (e.g., JavaScript functions and HTML forms) to in-browser AI agents, which can thus reliably simulate user actions instead of resorting to possibly expensive (e.g., on-screen reading) and often unreliable guesswork (e.g., DOM scraping). By Bruno Couriol

</details>