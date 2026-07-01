---
id: inbox_7da921fe
date: 2026-06-29
source_ref: "[[00-inbox/.../inbox_7da921fe]]"
title: "Claude Code Plugins: The Complete Guide to Extending Your AI Dev Environment"
url: https://medium.com/@mudassir00seven/claude-code-plugins-the-complete-guide-to-extending-your-ai-dev-environment-2de2158ee475?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-29T20:49:16+00:00
fetched_at: 2026-07-01T01:00:58.194284+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 外掛是可安裝的 `.plugin` ZIP 檔案，整合三大核心元件：MCP servers（與外部系統的連接器）、skills（Markdown 指令文件）和 hooks（自動化 shell 腳本）。一次安裝後在所有會話中自動持續。MCP servers 使 Claude 能以原生工具形式與資料庫、API 和檔案系統互動。Skills 提供永久結構化指令而無需專案配置改動。Hooks 在工具呼叫前後或通知觸發時執行自動化。最小化外掛需要 SKILL.md、MCP server 及 config.json；高價值用例包括資料庫連接器、檔案導航、CI/CD 整合。"
key_points:
  - "Claude Code 外掛 = MCP servers + skills (SKILL.md) + hooks (shell scripts)，一次安裝永久生效"
  - "MCP servers 作為原生工具連接資料庫、API、檔案系統；skills 提供不需專案配置的永久指令"
  - "最小門檻：Markdown SKILL.md、FastMCP Python server、config.json；高價值場景：DB/CI-CD 整合"
tags: [claude-code-plugins, mcp-servers, workflow-automation]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Claude Code Plugins: The Complete Guide to Extending Your AI Dev Environment

Claude Code 外掛是可安裝的 `.plugin` ZIP 檔案，整合三大核心元件：MCP servers（與外部系統的連接器）、skills（Markdown 指令文件）和 hooks（自動化 shell 腳本）。一次安裝後在所有會話中自動持續。MCP servers 使 Claude 能以原生工具形式與資料庫、API 和檔案系統互動。Skills 提供永久結構化指令而無需專案配置改動。Hooks 在工具呼叫前後或通知觸發時執行自動化。最小化外掛需要 SKILL.md、MCP server 及 config.json；高價值用例包括資料庫連接器、檔案導航、CI/CD 整合。

### 重點
- Claude Code 外掛 = MCP servers + skills (SKILL.md) + hooks (shell scripts)，一次安裝永久生效
- MCP servers 作為原生工具連接資料庫、API、檔案系統；skills 提供不需專案配置的永久指令
- 最小門檻：Markdown SKILL.md、FastMCP Python server、config.json；高價值場景：DB/CI-CD 整合

**原文：** [medium-tag-claude](https://medium.com/@mudassir00seven/claude-code-plugins-the-complete-guide-to-extending-your-ai-dev-environment-2de2158ee475?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Mudassir Khan"
published_at: 2026-06-29T20:49:16+00:00
fetched_at: 2026-06-29T22:51:52.032598+00:00
content_hash: "9b8bfda1466b216ccc6a67994115d0cbc410ab4a22851ddb5e60d4de8de9786b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code Plugins: The Complete Guide to Extending Your AI Dev Environment

A few months ago I was running the same three commands before every Claude Code session. Export an env var, confirm a config path, remind&#x2026; Continue reading on Medium »

</details>