---
id: inbox_fa3e9a9e
date: 2026-04-13
source_ref: "[[00-inbox/2026-04-13/0427-substack-bytebytego-how-linkedin-feed-uses-llms-to-serve-1-3-2337]]"
title: "How LinkedIn Feed Uses LLMs to Serve 1.3 Billion Users"
url: https://blog.bytebytego.com/p/how-linkedin-feed-uses-llms-to-serve
source: substack-bytebytego
published_at: 2026-04-13T15:31:28+00:00
fetched_at: 2026-04-21T04:33:44.751086+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 工程團隊分享其如何利用大語言模型（LLMs）重構服務 13 億用戶的信息流系統。文章深入探討在超大規模應用中部署 LLMs 所面臨的多維工程挑戰：延遲控制在毫秒級、成本優化、排序準確度、召回率平衡。通過多層快取、模型蒸餾、批處理、特徵工程等技術方案，LinkedIn 展示了如何在嚴苛的 SLA 約束下充分發揮 LLM 的推薦能力。"
key_points:
  - "13 億用戶規模要求延遲控制在毫秒級，驅動快取、批處理、模型優化等架構設計"
  - "排序準確度、成本、延遲三角形：需多維權衡，無法同時最優化"
  - "從特徵工程、模型蒸餾到推理優化，大規模 LLM 應用需系統化工程投入"
tags: [llm-applications, large-scale, feed-ranking]
topics: []
importance: 5
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## How LinkedIn Feed Uses LLMs to Serve 1.3 Billion Users

LinkedIn 工程團隊分享其如何利用大語言模型（LLMs）重構服務 13 億用戶的信息流系統。文章深入探討在超大規模應用中部署 LLMs 所面臨的多維工程挑戰：延遲控制在毫秒級、成本優化、排序準確度、召回率平衡。通過多層快取、模型蒸餾、批處理、特徵工程等技術方案，LinkedIn 展示了如何在嚴苛的 SLA 約束下充分發揮 LLM 的推薦能力。

### 重點
- 13 億用戶規模要求延遲控制在毫秒級，驅動快取、批處理、模型優化等架構設計
- 排序準確度、成本、延遲三角形：需多維權衡，無法同時最優化
- 從特徵工程、模型蒸餾到推理優化，大規模 LLM 應用需系統化工程投入

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/how-linkedin-feed-uses-llms-to-serve)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In this article, we will look at how the LinkedIn engineering team rebuilt the Feed and the challenges they faced.

</details>