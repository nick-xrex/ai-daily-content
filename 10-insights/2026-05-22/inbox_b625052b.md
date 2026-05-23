---
id: inbox_b625052b
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-infoq-ai-ml-uber-improves-restaurant-recommendations-d7ac]]"
title: "Uber Improves Restaurant Recommendations Using Real-Time Signals and Listwise Ranking"
url: https://www.infoq.com/news/2026/05/uber-eats-ranking-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-22T14:32:00+00:00
fetched_at: 2026-05-22T18:14:14.894159+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 改進 Uber Eats 推薦系統，從手工特徵設計轉向基於 transformer 的序列模型和 Listwise GenRec（生成式推薦）。關鍵優化：特徵新鮮度從 24 小時降至秒級，評分方式從 pointwise 轉為 listwise 排序。此轉變提升個性化程度和即時反應能力，代表推薦系統從靜態到動態、手工到學習的演進範式。"
key_points:
  - "Transformer 序列模型 + Listwise GenRec — 特徵從手工到自動學習"
  - "特徵新鮮度：24 小時 → 秒級，支援實時用戶訊號"
  - "模式：推薦系統從 pointwise 單項評分轉向 listwise 上下文排序"
tags: [recommendation-system, transformer, listwise-ranking, uber-eats]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Improves Restaurant Recommendations Using Real-Time Signals and Listwise Ranking

Uber 改進 Uber Eats 推薦系統，從手工特徵設計轉向基於 transformer 的序列模型和 Listwise GenRec（生成式推薦）。關鍵優化：特徵新鮮度從 24 小時降至秒級，評分方式從 pointwise 轉為 listwise 排序。此轉變提升個性化程度和即時反應能力，代表推薦系統從靜態到動態、手工到學習的演進範式。

### 重點
- Transformer 序列模型 + Listwise GenRec — 特徵從手工到自動學習
- 特徵新鮮度：24 小時 → 秒級，支援實時用戶訊號
- 模式：推薦系統從 pointwise 單項評分轉向 listwise 上下文排序

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/uber-eats-ranking-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber updates its Uber Eats Home Feed recommendation system using near real-time user sequence features and a Generative Recommender model. The system evolves from hand-crafted features to transformer-based sequence modeling, reduces feature freshness from 24 hours to seconds, and shifts from pointwise scoring to listwise GenRec for improved contextual ranking and real-time personalization. By Leela Kumili

</details>