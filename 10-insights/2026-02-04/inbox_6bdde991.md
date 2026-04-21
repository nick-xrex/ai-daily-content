---
id: inbox_6bdde991
date: 2026-02-04
source_ref: "[[00-inbox/2026-02-04/0158-openai-blog-unlocking-the-codex-harness-how-we-built-a02f]]"
title: "Unlocking the Codex harness: how we built the App Server"
url: https://openai.com/index/unlocking-the-codex-harness
source: openai-blog
published_at: 2026-02-04T13:00:00+00:00
fetched_at: 2026-04-21T02:22:03.023737+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 揭示了 Codex App Server 的技術基礎，這是一個雙向 JSON-RPC API，支援串流進度更新、工具使用、使用者批准流程和代碼差異展示。該伺服器為嵌入式 Codex Agent 提供了核心基礎設施，使開發者能整合高級 AI 編程能力到自有應用中。這項技術揭示了 OpenAI 在打造可生產環境 AI 代理工具時的架構思路。"
key_points:
  - "Codex App Server 採用雙向 JSON-RPC API 架構"
  - "支援串流進度、工具整合、批准工作流和 diff 顯示"
  - "為嵌入式 AI agent 提供生產級基礎設施"
tags: [codex, json-rpc, app-server, api-architecture]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Unlocking the Codex harness: how we built the App Server

OpenAI 揭示了 Codex App Server 的技術基礎，這是一個雙向 JSON-RPC API，支援串流進度更新、工具使用、使用者批准流程和代碼差異展示。該伺服器為嵌入式 Codex Agent 提供了核心基礎設施，使開發者能整合高級 AI 編程能力到自有應用中。這項技術揭示了 OpenAI 在打造可生產環境 AI 代理工具時的架構思路。

### 重點
- Codex App Server 採用雙向 JSON-RPC API 架構
- 支援串流進度、工具整合、批准工作流和 diff 顯示
- 為嵌入式 AI agent 提供生產級基礎設施

**原文：** [openai-blog](https://openai.com/index/unlocking-the-codex-harness)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Learn how to embed the Codex agent using the Codex App Server, a bidirectional JSON-RPC API powering streaming progress, tool use, approvals, and diffs.

</details>
