---
id: inbox_7eed019c
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-medium-tag-llm-gelato-the-frozen-towers-approach-to-mul-3580]]"
title: "GELATO: The Frozen Towers Approach to Multimodal Embeddings"
url: https://medium.com/@ayush.dhanker/gelato-the-frozen-towers-approach-to-multimodal-embeddings-f4cadf13fd6b?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-11T14:09:28+00:00
fetched_at: 2026-06-11T22:12:09.691090+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GELATO 提出多模態嵌入的「凍結塔」(frozen towers) 新架構。業界慣例是針對多模態任務訓練全新模型，但 GELATO 探索一個不同的問題：能否在已有的強大文本嵌入模型基礎上，透過凍結(frozen)參數的方式直接擴展其多模態能力？這個方法避免了從零開始訓練的計算開銷，可顯著降低多模態模型開發成本。此技巧對資源受限的研究團隊與企業具有實務價值，展現了參數共享與遷移學習在多模態領域的新應用。"
key_points:
  - "GELATO 採用凍結塔(frozen towers)架構實現多模態嵌入"
  - "擴展現有文本嵌入模型而非訓練新模型，顯著降低計算成本"
  - "參數凍結與遷移學習的新應用方式"
tags: [multimodal-embeddings, frozen-architecture, gelato, parameter-efficiency, transfer-learning]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## GELATO: The Frozen Towers Approach to Multimodal Embeddings

GELATO 提出多模態嵌入的「凍結塔」(frozen towers) 新架構。業界慣例是針對多模態任務訓練全新模型，但 GELATO 探索一個不同的問題：能否在已有的強大文本嵌入模型基礎上，透過凍結(frozen)參數的方式直接擴展其多模態能力？這個方法避免了從零開始訓練的計算開銷，可顯著降低多模態模型開發成本。此技巧對資源受限的研究團隊與企業具有實務價值，展現了參數共享與遷移學習在多模態領域的新應用。

### 重點
- GELATO 採用凍結塔(frozen towers)架構實現多模態嵌入
- 擴展現有文本嵌入模型而非訓練新模型，顯著降低計算成本
- 參數凍結與遷移學習的新應用方式

**原文：** [medium-tag-llm](https://medium.com/@ayush.dhanker/gelato-the-frozen-towers-approach-to-multimodal-embeddings-f4cadf13fd6b?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Most multimodal embedding papers train a new model. GELATO asks a different question: can we extend an already strong text embedding model&#x2026; Continue reading on Medium »

</details>