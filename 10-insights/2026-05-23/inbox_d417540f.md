---
id: inbox_d417540f
date: 2026-05-23
source_ref: "[[00-inbox/2026-05-23/0348-medium-tag-claude-building-an-mcp-server-in-kotlin-whats-a-6db4]]"
title: "Building an MCP Server in Kotlin: What’s Actually Happening Between Claude and Your Code"
url: https://vivart.medium.com/building-an-mcp-server-in-kotlin-whats-actually-happening-between-claude-and-your-code-5d25463f6b1d?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-23T22:20:27+00:00
fetched_at: 2026-05-24T03:56:15.184486+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Vivart Pandey 教授如何用 Kotlin 構建 MCP（Model Context Protocol）server，MCP 是開放標準讓 Claude 連接外部工具和資料。MCP 工作原理類似 LSP，兩進程通過 JSON-RPC messages 在 stdin/stdout 通訊；Claude Code 啟動時 spawn server 作為子進程，全 session 保活。三個主要 primitives：Tools（函數 Claude 調用）、Resources（唯讀資料）、Prompts（可重用工作流模板）。實現要點：禁用 println()、僅用 stdout for JSON-RPC、logging 用 System.err、tool descriptions 決定 Claude 調用時機、JetBrains 官方 Kotlin SDK 處理序列化。"
key_points:
  - "MCP 是開放標準，通訊協議基於 JSON-RPC 的雙向消息流；Tool descriptions 決定 Claude 何時調用"
  - "不能用 println()，只能 stdout for JSON-RPC、System.err for logging；JetBrains Kotlin SDK 自動處理序列化"
  - "三個 primitives：Tools（functions）、Resources（read-only data）、Prompts（reusable templates as slash commands）"
tags: [mcp, kotlin, json-rpc, claude-integration, language-server]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Building an MCP Server in Kotlin: What’s Actually Happening Between Claude and Your Code

Vivart Pandey 教授如何用 Kotlin 構建 MCP（Model Context Protocol）server，MCP 是開放標準讓 Claude 連接外部工具和資料。MCP 工作原理類似 LSP，兩進程通過 JSON-RPC messages 在 stdin/stdout 通訊；Claude Code 啟動時 spawn server 作為子進程，全 session 保活。三個主要 primitives：Tools（函數 Claude 調用）、Resources（唯讀資料）、Prompts（可重用工作流模板）。實現要點：禁用 println()、僅用 stdout for JSON-RPC、logging 用 System.err、tool descriptions 決定 Claude 調用時機、JetBrains 官方 Kotlin SDK 處理序列化。

### 重點
- MCP 是開放標準，通訊協議基於 JSON-RPC 的雙向消息流；Tool descriptions 決定 Claude 何時調用
- 不能用 println()，只能 stdout for JSON-RPC、System.err for logging；JetBrains Kotlin SDK 自動處理序列化
- 三個 primitives：Tools（functions）、Resources（read-only data）、Prompts（reusable templates as slash commands）

**原文：** [medium-tag-claude](https://vivart.medium.com/building-an-mcp-server-in-kotlin-whats-actually-happening-between-claude-and-your-code-5d25463f6b1d?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

You are working on a project that deals with live data. Exchange rates, database records, internal APIs, file systems &#x2014; something that&#x2026; Continue reading on Medium »

</details>