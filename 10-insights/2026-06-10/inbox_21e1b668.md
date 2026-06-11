---
id: inbox_21e1b668
date: 2026-06-10
source_ref: "[[00-inbox/2026-06-10/2359-infoq-main-presentation-beyond-prompting-context-en-e348]]"
title: "Presentation: Beyond Prompting: Context Engineering and Memory Management for AI Systems at Scale"
url: https://www.infoq.com/presentations/context-engineering-data/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-10T12:03:00+00:00
fetched_at: 2026-06-11T00:02:51.212101+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Adi Polak 在 InfoQ 演講中分享了從無狀態提示過渡到有狀態 AI 代理的工程架構設計。她建議利用 Apache Kafka 和 Flink 進行實時流處理、實施動態內存分層策略、通過 MCP 進行工具編排，以克服代幣限制、成本激增和延遲瓶頸。此建議基於 15 年分佈式系統工程經驗。"
key_points:
  - "架構轉變：從無狀態提示到有狀態、內容豐富的 AI 代理（Context-rich Agents）"
  - "技術棧：Apache Kafka + Apache Flink（實時流處理）+ 動態內存分層 + MCP 工具編排"
  - "問題解決：代幣限制突破、成本激增控制、延遲瓶頸優化"
tags: [ai-agents, mcp, kafka, flink, context-engineering]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Beyond Prompting: Context Engineering and Memory Management for AI Systems at Scale

Adi Polak 在 InfoQ 演講中分享了從無狀態提示過渡到有狀態 AI 代理的工程架構設計。她建議利用 Apache Kafka 和 Flink 進行實時流處理、實施動態內存分層策略、通過 MCP 進行工具編排，以克服代幣限制、成本激增和延遲瓶頸。此建議基於 15 年分佈式系統工程經驗。

### 重點
- 架構轉變：從無狀態提示到有狀態、內容豐富的 AI 代理（Context-rich Agents）
- 技術棧：Apache Kafka + Apache Flink（實時流處理）+ 動態內存分層 + MCP 工具編排
- 問題解決：代幣限制突破、成本激增控制、延遲瓶頸優化

**原文：** [infoq-main](https://www.infoq.com/presentations/context-engineering-data/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Adi Polak discusses the architecture required to transition from stateless prompts to state-aware, context-rich AI agents. Drawing on 15 years in distributed systems, she shares how engineering leaders can leverage Apache Kafka and Flink for real-time stream processing, dynamic memory tiering, and tool orchestration via MCP to solve token limits, cost spikes, and latency bottlenecks. By Adi Polak

</details>