---
id: inbox_ae692f07
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-infoq-main-google-s-genkit-ships-agents-api-with-de-c643]]"
title: "Google&#39;s Genkit Ships Agents API with Detached Turns and Human-in-the-Loop for TypeScript and Go"
url: https://www.infoq.com/news/2026/07/genkit-agents-api-preview/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-14T10:17:00+00:00
fetched_at: 2026-07-14T22:13:15.258849+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google Genkit 發布 Agents API 預覽版（TypeScript / Go），內建訊息歷史、工具迴圈、流式處理與狀態持久化。核心創新為 detached turns（代理在客戶端斷開後繼續工作）與 human-in-the-loop 模式，搭配反鍽造驗證保障恢復時安全性。此設計打破傳統 request-response 同步侷限，為交互式 AI agent 提供非同步與人工干預能力。"
key_points:
  - "Detached turns 允許 agent 在客戶端斷開後非同步執行，解除同步請求-回應限制"
  - "Human-in-the-loop 控制搭配反鍽造驗證，確保代理恢復時的安全性與可審計性"
  - "統一 chat() 介面包裝訊息歷史、工具、流式、狀態，降低代理實現複雜度"
tags: [agents, google-genkit, human-in-the-loop, async-patterns, typescript-go]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Google's Genkit Ships Agents API with Detached Turns and Human-in-the-Loop for TypeScript and Go

Google Genkit 發布 Agents API 預覽版（TypeScript / Go），內建訊息歷史、工具迴圈、流式處理與狀態持久化。核心創新為 detached turns（代理在客戶端斷開後繼續工作）與 human-in-the-loop 模式，搭配反鍽造驗證保障恢復時安全性。此設計打破傳統 request-response 同步侷限，為交互式 AI agent 提供非同步與人工干預能力。

### 重點
- Detached turns 允許 agent 在客戶端斷開後非同步執行，解除同步請求-回應限制
- Human-in-the-loop 控制搭配反鍽造驗證，確保代理恢復時的安全性與可審計性
- 統一 chat() 介面包裝訊息歷史、工具、流式、狀態，降低代理實現複雜度

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/genkit-agents-api-preview/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google released the Genkit Agents API in preview for TypeScript and Go. The open-source framework packages message history, tool loops, streaming, and state persistence behind a single chat() interface. Detached turns let agents work after clients disconnect. Interruptible tools provide human-in-the-loop control with anti-forgery validation on resume. By Steef-Jan Wiggers

</details>