---
id: inbox_4a5e784c
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-infoq-ai-ml-openai-introduces-websocket-based-execut-048d]]"
title: "OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows"
url: https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-07T14:48:00+00:00
fetched_at: 2026-05-08T07:45:18.278810+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 為 Responses API 推出 WebSocket 執行模式，透過持久連接取代傳統 HTTP 請求-回應循環，在編碼代理和實時 AI 系統中減少延遲最多 40%。新的執行模式改進了串流、工具執行和多步驟協調的性能。WebSocket 連接特別適合需要頻繁交互的代理工作流程，例如編碼助手和實時決策系統。這項優化針對生產規模的 AI 系統進行設計。該更新對建構低延遲代理應用的開發者具有直接的實務價值。"
key_points:
  - "OpenAI Responses API WebSocket 執行模式相比 HTTP 減少延遲最多 40%，透過持久連接優化性能"
  - "改進編碼代理的工具執行、串流和多步驟協調，支援實時 AI 系統"
  - "針對生產規模代理工作流程優化，特別適合頻繁交互的應用場景"
tags: [openai, websocket, latency, responses-api, agentic-workflows]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows

OpenAI 為 Responses API 推出 WebSocket 執行模式，透過持久連接取代傳統 HTTP 請求-回應循環，在編碼代理和實時 AI 系統中減少延遲最多 40%。新的執行模式改進了串流、工具執行和多步驟協調的性能。WebSocket 連接特別適合需要頻繁交互的代理工作流程，例如編碼助手和實時決策系統。這項優化針對生產規模的 AI 系統進行設計。該更新對建構低延遲代理應用的開發者具有直接的實務價值。

### 重點
- OpenAI Responses API WebSocket 執行模式相比 HTTP 減少延遲最多 40%，透過持久連接優化性能
- 改進編碼代理的工具執行、串流和多步驟協調，支援實時 AI 系統
- 針對生產規模代理工作流程優化，特別適合頻繁交互的應用場景

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

OpenAI introduces a WebSocket-based execution mode for its Responses API to improve agentic workflow performance in coding agents and real-time AI systems. The update reduces latency by up to 40 percent by replacing HTTP request-response cycles with persistent connections, improving streaming, tool execution, and multi-step orchestration in production-scale AI systems. By Leela Kumili

</details>