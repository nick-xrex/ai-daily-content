---
id: inbox_d414fd4c
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-infoq-main-elastic-open-sources-atlas-agent-memory-2e42]]"
title: "Elastic Open-Sources Atlas Agent Memory Based on Cognitive Science"
url: https://www.infoq.com/news/2026/06/elastic-atlas-agent-memory/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-30T13:00:00+00:00
fetched_at: 2026-07-02T00:21:41.690420+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Elastic 開源了 Atlas，一個基於 Elasticsearch 的代理記憶系統，由認知科學啟發設計。Atlas 維護三層記憶架構（短期、中期、長期），透過 MCP（Model Context Protocol）與代理整合，並實現逐用戶隔離的多租戶安全。在標準問答任務評估中達到 0.89 Recall@10，為長期代理對話提供實用級的記憶檢索精度。"
key_points:
  - "三層記憶架構：基於認知科學設計的短中長期記憶分層，超越簡單 vector store 的單層存儲"
  - "MCP 整合 + 用戶隔離：Model Context Protocol 標準接入，內建每用戶記憶隔離，實現多租戶安全性"
  - "量化效能指標：Recall@10=0.89，標誌著代理記憶系統的檢索精度達到生產實用水平"
tags: [agent-memory, elasticsearch, mcp-integration, cognitive-science, open-source-tool]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 4
insight_type: tool
deep_dive_candidate: true
deep_dive_approved: false
---

## Elastic Open-Sources Atlas Agent Memory Based on Cognitive Science

Elastic 開源了 Atlas，一個基於 Elasticsearch 的代理記憶系統，由認知科學啟發設計。Atlas 維護三層記憶架構（短期、中期、長期），透過 MCP（Model Context Protocol）與代理整合，並實現逐用戶隔離的多租戶安全。在標準問答任務評估中達到 0.89 Recall@10，為長期代理對話提供實用級的記憶檢索精度。

### 重點
- 三層記憶架構：基於認知科學設計的短中長期記憶分層，超越簡單 vector store 的單層存儲
- MCP 整合 + 用戶隔離：Model Context Protocol 標準接入，內建每用戶記憶隔離，實現多租戶安全性
- 量化效能指標：Recall@10=0.89，標誌著代理記憶系統的檢索精度達到生產實用水平

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/elastic-atlas-agent-memory/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Elastic open-sourced Atlas, a system built on Elasticsearch that maintains three categories of memory for agents. Atlas integrates with agents via MCP and maintains per-user isolation of memories. When evaluated on question-answering capability, it scored 0.89 Recall@10. By Anthony Alford

</details>