---
id: inbox_29edd28a
date: 2026-05-20
source_ref: "[[00-inbox/2026-05-20/0917-substack-bytebytego-how-netflix-is-using-multimodal-ai-to-po-93fe]]"
title: "How Netflix is Using Multimodal AI to Power Video Search"
url: https://blog.bytebytego.com/p/how-netflix-is-using-multimodal-ai
source: substack-bytebytego
published_at: 2026-05-20T15:31:07+00:00
fetched_at: 2026-05-21T09:31:47.667348+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Netflix 用三層架構解決超大規模視頻搜尋問題。單季原始影片 2000+ 小時（2.16 億幀），編輯傳統搜尋需數天。Netflix 方案：Stage 1 原始模型輸出直入 Apache Cassandra（零轉換優先完整性）→ Stage 2 離線融合成 1 秒時間桶規範化 → Stage 3 Elasticsearch 嵌套文檔混合搜尋。關鍵決策：特化模型（如臉部識別專用模型）精度優於通用模型；混合搜尋結合精確關鍵字和語義相似度（例「Joey 在廚房」同時需要名字精度+空間語義）。三層分工核心：入口層優先原始性、中層優先融合、出口層優先查詢速度。"
key_points:
  - "三層流水線設計：Cassandra（原始）→ 離線融合（規範化）→ Elasticsearch（混合搜尋）——入口保真、中層融合、出口快速的漸進優化"
  - "特化模型 > 通用模型：臉部識別專用模型識別字符精度明顯優於通用視覺 AI，多模型協作需策略式整合"
  - "混合搜尋：結合精確關鍵字匹配（人名）+ 語義向量相似度（環境概念），用戶可調精度-速度權衡"
tags: [multi-model-architecture, specialized-models, hybrid-search, elasticsearch-patterns, netflix-scale]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How Netflix is Using Multimodal AI to Power Video Search

Netflix 用三層架構解決超大規模視頻搜尋問題。單季原始影片 2000+ 小時（2.16 億幀），編輯傳統搜尋需數天。Netflix 方案：Stage 1 原始模型輸出直入 Apache Cassandra（零轉換優先完整性）→ Stage 2 離線融合成 1 秒時間桶規範化 → Stage 3 Elasticsearch 嵌套文檔混合搜尋。關鍵決策：特化模型（如臉部識別專用模型）精度優於通用模型；混合搜尋結合精確關鍵字和語義相似度（例「Joey 在廚房」同時需要名字精度+空間語義）。三層分工核心：入口層優先原始性、中層優先融合、出口層優先查詢速度。

### 重點
- 三層流水線設計：Cassandra（原始）→ 離線融合（規範化）→ Elasticsearch（混合搜尋）——入口保真、中層融合、出口快速的漸進優化
- 特化模型 > 通用模型：臉部識別專用模型識別字符精度明顯優於通用視覺 AI，多模型協作需策略式整合
- 混合搜尋：結合精確關鍵字匹配（人名）+ 語義向量相似度（環境概念），用戶可調精度-速度權衡

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/how-netflix-is-using-multimodal-ai)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In this article, we will understand how Netflix built this system and the challenges it faced.

</details>