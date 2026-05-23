---
id: inbox_79ae351d
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-infoq-main-uber-improves-restaurant-recommendations-3634]]"
title: "Uber Improves Restaurant Recommendations Using Real-Time Signals and Listwise Ranking"
url: https://www.infoq.com/news/2026/05/uber-eats-ranking-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-22T14:32:00+00:00
fetched_at: 2026-05-22T18:13:42.140135+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 升級 Eats Home Feed 推薦系統，核心變更三層面：特徵演進（hand-crafted features → transformer-based sequence modeling）、特徵新鮮度（24 小時 → 秒級 near real-time user sequence features）、排名模式（pointwise scoring → listwise GenRec Generative Recommender）。新架構採 transformer-based sequence modeling 配 real-time signals，支援上下文感知排名與實時個性化。此舉顯著降低特徵延遲、改善推薦多樣性與業務指標。實現的關鍵是用實時用戶序列信號取代靜態手工特徵，並以生成式排名模型進行 listwise 評分。該變更代表推薦系統從離線批處理向實時在線計算的演進。"
key_points:
  - "Feature freshness：24 hours → seconds via near real-time user sequence features（sequence modeling 取代 hand-crafted）"
  - "排名方式：pointwise scoring → listwise GenRec for contextual ranking，結合 transformer-based sequence modeling"
  - "技術棧轉向：離線批處理 → 實時在線計算、靜態特徵 → 動態實時信號、單點評分 → 列表級生成式評分"
tags: [recommender-systems, listwise-ranking, real-time-features, sequence-modeling, genrec]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Improves Restaurant Recommendations Using Real-Time Signals and Listwise Ranking

Uber 升級 Eats Home Feed 推薦系統，核心變更三層面：特徵演進（hand-crafted features → transformer-based sequence modeling）、特徵新鮮度（24 小時 → 秒級 near real-time user sequence features）、排名模式（pointwise scoring → listwise GenRec Generative Recommender）。新架構採 transformer-based sequence modeling 配 real-time signals，支援上下文感知排名與實時個性化。此舉顯著降低特徵延遲、改善推薦多樣性與業務指標。實現的關鍵是用實時用戶序列信號取代靜態手工特徵，並以生成式排名模型進行 listwise 評分。該變更代表推薦系統從離線批處理向實時在線計算的演進。

### 重點
- Feature freshness：24 hours → seconds via near real-time user sequence features（sequence modeling 取代 hand-crafted）
- 排名方式：pointwise scoring → listwise GenRec for contextual ranking，結合 transformer-based sequence modeling
- 技術棧轉向：離線批處理 → 實時在線計算、靜態特徵 → 動態實時信號、單點評分 → 列表級生成式評分

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/uber-eats-ranking-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber updates its Uber Eats Home Feed recommendation system using near real-time user sequence features and a Generative Recommender model. The system evolves from hand-crafted features to transformer-based sequence modeling, reduces feature freshness from 24 hours to seconds, and shifts from pointwise scoring to listwise GenRec for improved contextual ranking and real-time personalization. By Leela Kumili

</details>