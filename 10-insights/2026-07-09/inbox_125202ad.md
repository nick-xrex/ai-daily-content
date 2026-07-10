---
id: inbox_125202ad
date: 2026-07-09
source_ref: "[[00-inbox/.../inbox_125202ad]]"
title: "AlloyDB Ships Proxy Models That Replace LLM Calls with Local Inference inside the Database"
url: https://www.infoq.com/news/2026/07/alloydb-ai-proxy-models/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-09T08:00:00+00:00
fetched_at: 2026-07-10T01:20:58.311396+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google AlloyDB AI 函數正式版推出代理模型架構，在資料庫內運行輕量級本地模型以替代外部 LLM 呼叫，通過智能批處理實現 2,400 倍吞吐量提升。該系統在預覽版達到每秒 100,000 列的性能，將推理邊界移至資料庫層以優化延遲和成本，但基準測試數據來自內部測試。"
key_points:
  - "代理模型架構：在資料庫內訓練輕量級本地模型取代外部 LLM 呼叫，實現資料庫速度查詢"
  - "性能提升：智能批處理達到 2,400 倍吞吐量提升，預覽版達 100,000 列/秒"
  - "成本優化：避免外部 LLM 呼叫，將 AI 推理邊界移至資料庫層"
tags: [alloydb, llm-optimization, local-inference, database, proxy-model]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## AlloyDB Ships Proxy Models That Replace LLM Calls with Local Inference inside the Database

Google AlloyDB AI 函數正式版推出代理模型架構，在資料庫內運行輕量級本地模型以替代外部 LLM 呼叫，通過智能批處理實現 2,400 倍吞吐量提升。該系統在預覽版達到每秒 100,000 列的性能，將推理邊界移至資料庫層以優化延遲和成本，但基準測試數據來自內部測試。

### 重點
- 代理模型架構：在資料庫內訓練輕量級本地模型取代外部 LLM 呼叫，實現資料庫速度查詢
- 性能提升：智能批處理達到 2,400 倍吞吐量提升，預覽版達 100,000 列/秒
- 成本優化：避免外部 LLM 呼叫，將 AI 推理邊界移至資料庫層

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/alloydb-ai-proxy-models/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AlloyDB Ships Proxy Models That Replace LLM Calls with Local Inference inside the Database

Google shipped AlloyDB AI functions GA with a proxy model architecture that trains a lightweight local model from LLM outputs, then runs queries at database speed without external calls. Smart batching delivers 2,400x throughput improvement. The proxy model reaches 100,000 rows per second in preview, but benchmark numbers apply only to ai.if in internal testing. By Steef-Jan Wiggers

</details>