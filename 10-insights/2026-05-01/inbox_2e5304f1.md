---
id: inbox_2e5304f1
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0131-infoq-architecture-jobrunr-introduces-clawrunr-an-open-sour-e12c]]"
title: "JobRunr Introduces ClawRunr, an Open-Source Java AI Agent"
url: https://www.infoq.com/news/2026/05/clawrunr/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-01T15:00:00+00:00
fetched_at: 2026-05-03T01:36:45.740827+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "JobRunr 推出 ClawRunr（原名 JavaClaw），開源 Java AI agent 框架用於排程化、週期性和一次性後台任務。ClawRunr 執行在用戶硬體上，整合會話交互、持久化任務執行、MCP 工具與瀏覽器自動化能力，支援 Web、Telegram 與 Discord 多通道觸發。底層使用 JobRunr 管理排程、重試邏輯和監控，實現生產級 agent 可靠性。"
key_points:
  - "基於 JobRunr 的 Java AI agent，支持 MCP tools 標準，便於工具拓展"
  - "多通道整合（Web、Telegram、Discord）與會話驅動，適用多場景應用"
  - "內建重試、排程、監控機制，提升後台任務穩定性與可觀察性"
tags: [java, ai-agent, mcp-tools]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## JobRunr Introduces ClawRunr, an Open-Source Java AI Agent

JobRunr 推出 ClawRunr（原名 JavaClaw），開源 Java AI agent 框架用於排程化、週期性和一次性後台任務。ClawRunr 執行在用戶硬體上，整合會話交互、持久化任務執行、MCP 工具與瀏覽器自動化能力，支援 Web、Telegram 與 Discord 多通道觸發。底層使用 JobRunr 管理排程、重試邏輯和監控，實現生產級 agent 可靠性。

### 重點
- 基於 JobRunr 的 Java AI agent，支持 MCP tools 標準，便於工具拓展
- 多通道整合（Web、Telegram、Discord）與會話驅動，適用多場景應用
- 內建重試、排程、監控機制，提升後台任務穩定性與可觀察性

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/clawrunr/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/05/clawrunr/en/headerimage/generatedHeaderImage-1777644148544.jpg" /><p>JobRunr has introduced ClawRunr, an open-source Java AI agent for scheduled, recurring, and one-off background tasks. Formerly JavaClaw, it runs on users' hardware and combines conversational interaction with persistent task execution, MCP tools, browser automation, and web, Telegram, and Discord channels, while using JobRunr for scheduling, retries, and monitoring.</p> <i>By Diogo Carleto</i>

</details>