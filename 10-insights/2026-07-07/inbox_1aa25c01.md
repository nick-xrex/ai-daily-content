---
id: inbox_1aa25c01
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_1aa25c01]]"
title: "How HubSpot Scaled Semantic Search to 20 Billion Vectors"
url: https://www.infoq.com/news/2026/07/hubspot-semantic-vector-search/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-07T08:00:00+00:00
fetched_at: 2026-07-08T01:06:17.435188+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "HubSpot 將其語義搜尋平台從概念驗證擴展至生產規模，現管理超過 20 億個向量，服務 38 個以上的內部團隊。該系統支持代理、RAG 和聯繫人去重等多元使用場景。隨著代理使用量的增長，系統優先級發生關鍵轉變：檢索質量和延遲成為比總吞吐量更重要的指標。此轉變反映出代理工作負載對向量檢索系統的不同要求——代理需要低延遲、高召回率的精准檢索，而非批量查詢。"
key_points:
  - "20 億向量規模跨越 38+ 團隊，展示向量數據庫的企業級可擴展性"
  - "代理使用增長改變了檢索優先順序：從吞吐量導向轉變為質量+延遲導向"
  - "RAG + 代理組合成為語義搜尋的主要消費者，改變了系統設計的優化權衡"
tags: [vector-scale, rag-infrastructure, semantic-search, agent-retrieval]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How HubSpot Scaled Semantic Search to 20 Billion Vectors

HubSpot 將其語義搜尋平台從概念驗證擴展至生產規模，現管理超過 20 億個向量，服務 38 個以上的內部團隊。該系統支持代理、RAG 和聯繫人去重等多元使用場景。隨著代理使用量的增長，系統優先級發生關鍵轉變：檢索質量和延遲成為比總吞吐量更重要的指標。此轉變反映出代理工作負載對向量檢索系統的不同要求——代理需要低延遲、高召回率的精准檢索，而非批量查詢。

### 重點
- 20 億向量規模跨越 38+ 團隊，展示向量數據庫的企業級可擴展性
- 代理使用增長改變了檢索優先順序：從吞吐量導向轉變為質量+延遲導向
- RAG + 代理組合成為語義搜尋的主要消費者，改變了系統設計的優化權衡

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/hubspot-semantic-vector-search/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# How HubSpot Scaled Semantic Search to 20 Billion Vectors

SaaS software vendor HubSpot has described how its semantic search platform grew from a proof of concept into an internal service that now manages more than 20 billion vectors across 38-plus teams. The company says the system now supports agents, RAG, and contact deduplication, and that the increase in agent usage has made retrieval quality and latency more important than before. By Matt Saunders

</details>