---
id: inbox_e35c9b95
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-infoq-main-openai-introduces-websocket-based-execut-b344]]"
title: "OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows"
url: https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-07T14:48:00+00:00
fetched_at: 2026-05-08T07:43:22.072172+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 為 Responses API 推出基於 WebSocket 的執行模式，替代傳統 HTTP 請求-回應循環，用於改善編碼代理和實時 AI 系統的性能。該更新將延遲降低高達 40%，並改進流式傳輸、工具執行和多步驟編排在生產規模系統中的能力。這是在 agentic workflows 中實現低延遲的關鍵技術突破。"
key_points:
  - "OpenAI Responses API 新增 WebSocket 執行模式，透過持久連接替代 HTTP 循環，降低延遲 40%"
  - "改進三項關鍵能力：流式傳輸、工具執行、多步驟編排在生產規模系統中的性能"
  - "特別針對編碼代理和實時 AI 系統設計，解決 agentic workflows 中的延遲瓶頸"
tags: [openai, websocket, agentic-workflows, latency-optimization, real-time-ai]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows

OpenAI 為 Responses API 推出基於 WebSocket 的執行模式，替代傳統 HTTP 請求-回應循環，用於改善編碼代理和實時 AI 系統的性能。該更新將延遲降低高達 40%，並改進流式傳輸、工具執行和多步驟編排在生產規模系統中的能力。這是在 agentic workflows 中實現低延遲的關鍵技術突破。

### 重點
- OpenAI Responses API 新增 WebSocket 執行模式，透過持久連接替代 HTTP 循環，降低延遲 40%
- 改進三項關鍵能力：流式傳輸、工具執行、多步驟編排在生產規模系統中的性能
- 特別針對編碼代理和實時 AI 系統設計，解決 agentic workflows 中的延遲瓶頸

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

OpenAI introduces a WebSocket-based execution mode for its Responses API to improve agentic workflow performance in coding agents and real-time AI systems. The update reduces latency by up to 40 percent by replacing HTTP request-response cycles with persistent connections, improving streaming, tool execution, and multi-step orchestration in production-scale AI systems. By Leela Kumili

</details>