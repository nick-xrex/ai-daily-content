---
id: inbox_ebf6cbaa
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0131-medium-towards-data-science-ghost-a-database-for-ourtimes-bb4a]]"
title: "Ghost: A Database for Our Times?"
url: https://towardsdatascience.com/ghost-a-database-for-our-times/
source: medium-towards-data-science
published_at: 2026-05-01T13:30:00+00:00
fetched_at: 2026-05-03T01:40:16.690800+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ghost（ghost.build）推出「為 AI 代理設計的第一個資料庫」—— 基於 Postgres 的 agent-first 平台。不同於傳統長期生產資料庫設計，Ghost 將資料庫視為可拋棄資源，支援即時創建、fork、檢查、查詢、操縱和刪除整個資料庫，工作流更接近現代 agentic 開發。支援的代理包括 Claude Code、Codex、Cursor、Gemini CLI 等。Ghost 的內建 MCP server 讓代理（如 Claude Code）直接進行資料庫管理、遷移、schema 檢查和 SQL 執行，無須手動 dashboard 操作或複製連接字符串。特別適合測試、原型開發、代理工作流、branch 資料庫、遷移實驗等臨時環境。提供慷慨的免費使用額度。"
key_points:
  - "Agent-first 設計：資料庫如同代碼沙箱般可拋棄和可程式化，契合 Claude Code / Codex 的推理能力和 MCP 工具整合"
  - "內建 MCP server 賦能代理直接管理數據庫：無需中間步驟，支援 write migrations、debug queries、generate seed data、inspect logs"
  - "支援的代理平台包括 Claude Code、Codex、Cursor、Gemini CLI、VS Code、Windsurf 等主流 AI 開發工具"
tags: [database, ai-agents, mcp-tools, postgres, developer-tools]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Ghost: A Database for Our Times?

Ghost（ghost.build）推出「為 AI 代理設計的第一個資料庫」—— 基於 Postgres 的 agent-first 平台。不同於傳統長期生產資料庫設計，Ghost 將資料庫視為可拋棄資源，支援即時創建、fork、檢查、查詢、操縱和刪除整個資料庫，工作流更接近現代 agentic 開發。支援的代理包括 Claude Code、Codex、Cursor、Gemini CLI 等。Ghost 的內建 MCP server 讓代理（如 Claude Code）直接進行資料庫管理、遷移、schema 檢查和 SQL 執行，無須手動 dashboard 操作或複製連接字符串。特別適合測試、原型開發、代理工作流、branch 資料庫、遷移實驗等臨時環境。提供慷慨的免費使用額度。

### 重點
- Agent-first 設計：資料庫如同代碼沙箱般可拋棄和可程式化，契合 Claude Code / Codex 的推理能力和 MCP 工具整合
- 內建 MCP server 賦能代理直接管理數據庫：無需中間步驟，支援 write migrations、debug queries、generate seed data、inspect logs
- 支援的代理平台包括 Claude Code、Codex、Cursor、Gemini CLI、VS Code、Windsurf 等主流 AI 開發工具

**原文：** [medium-towards-data-science](https://towardsdatascience.com/ghost-a-database-for-our-times/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p>The first database built for AI Agents</p>
<p>The post <a href="https://towardsdatascience.com/ghost-a-database-for-our-times/">Ghost: A Database for Our Times?</a> appeared first on <a href="https://towardsdatascience.com">Towards Data Science</a>.</p>

</details>