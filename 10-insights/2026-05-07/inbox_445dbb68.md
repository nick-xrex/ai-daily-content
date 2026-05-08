---
id: inbox_445dbb68
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-infoq-architecture-openai-introduces-websocket-based-execut-6eef]]"
title: "OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows"
url: https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-07T14:48:00+00:00
fetched_at: 2026-05-08T07:47:07.198848+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 為 Responses API 推出 WebSocket 執行模式，利用持久連接替代 HTTP request-response 循環，在生產環境中實現最高 40% 的延遲降低。該更新特別優化了 Coding Agents 和實時 AI 系統的 streaming、tool execution 和多步驟編排能力，為 Agent 工作流提供顯著的性能改進，對成本敏感的大規模應用具有實務價值。"
key_points:
  - "WebSocket 持久連接替代 HTTP 循環，延遲降低最高 40%"
  - "優化 streaming、tool execution、multi-step orchestration 的吞吐量"
  - "針對 Coding Agents 和實時 AI 系統的關鍵性能改進"
tags: [websocket, responses-api, openai, agent-workflow, latency-optimization]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenAI Introduces Websocket-Based Execution Mode to Reduce Latency in Agentic Workflows

OpenAI 為 Responses API 推出 WebSocket 執行模式，利用持久連接替代 HTTP request-response 循環，在生產環境中實現最高 40% 的延遲降低。該更新特別優化了 Coding Agents 和實時 AI 系統的 streaming、tool execution 和多步驟編排能力，為 Agent 工作流提供顯著的性能改進，對成本敏感的大規模應用具有實務價值。

### 重點
- WebSocket 持久連接替代 HTTP 循環，延遲降低最高 40%
- 優化 streaming、tool execution、multi-step orchestration 的吞吐量
- 針對 Coding Agents 和實時 AI 系統的關鍵性能改進

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/openai-websocket-responses-api/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

OpenAI introduces a WebSocket-based execution mode for its Responses API to improve agentic workflow performance in coding agents and real-time AI systems. The update reduces latency by up to 40 percent by replacing HTTP request-response cycles with persistent connections, improving streaming, tool execution, and multi-step orchestration in production-scale AI systems. By Leela Kumili

</details>