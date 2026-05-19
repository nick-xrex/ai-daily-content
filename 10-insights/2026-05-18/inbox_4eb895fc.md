---
id: inbox_4eb895fc
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_4eb895fc]]"
title: "Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking"
url: https://www.infoq.com/news/2026/05/swiggy-autocomplete-rt-ranking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-18T14:38:00+00:00
fetched_at: 2026-05-19T02:25:07.940671+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Swiggy 詳解基於 OpenSearch 的實時機器學習排名系統，用於優化搜尋自動完成。系統採用候選生成與排名兩階段分離架構，使用特徵存儲提供實時信號，通過學習排序模型替代傳統啟發式規則。該方案在保持嚴格延遲約束的同時，支持從用戶行為信號持續更新和優化模型，實現了從規則驅動到數據驅動的轉變。"
key_points:
  - "兩階段架構分離：候選生成與實時排名分離，特徵存儲支持實時信號注入"
  - "排序學習模型 (Learning-to-Rank) 替代人工啟發式規則，提升搜尋相關性"
  - "嚴格延遲約束下實現連續模型迭代，從線上用戶行為反饋持續優化"
tags: [ml-ranking, search-autocomplete, feature-store, real-time-ml, two-stage-ranking]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking

Swiggy 詳解基於 OpenSearch 的實時機器學習排名系統，用於優化搜尋自動完成。系統採用候選生成與排名兩階段分離架構，使用特徵存儲提供實時信號，通過學習排序模型替代傳統啟發式規則。該方案在保持嚴格延遲約束的同時，支持從用戶行為信號持續更新和優化模型，實現了從規則驅動到數據驅動的轉變。

### 重點
- 兩階段架構分離：候選生成與實時排名分離，特徵存儲支持實時信號注入
- 排序學習模型 (Learning-to-Rank) 替代人工啟發式規則，提升搜尋相關性
- 嚴格延遲約束下實現連續模型迭代，從線上用戶行為反饋持續優化

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/swiggy-autocomplete-rt-ranking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking

Swiggy detailed real-time machine-learning ranking system for autocomplete built on OpenSearch. The architecture separates candidate generation and ranking, uses feature stores for real time signals, and applies learning to rank models for improved relevance. It replaces heuristic ranking while maintaining strict latency constraints and enabling continuous model updates from user behavior signals. By Leela Kumili

</details>