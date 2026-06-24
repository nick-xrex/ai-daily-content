---
id: inbox_a2f598fb
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2201-medium-towards-data-science-a-three-phase-factual-recall-circuit-in-c7bd]]"
title: "A Three-Phase Factual Recall Circuit in Gemma-2B and Gemma-12B-IT"
url: https://towardsdatascience.com/a-three-phase-factual-recall-circuit-in-gemma-2b-and-gemma-12b-it/
source: medium-towards-data-science
published_at: 2026-06-24T15:00:00+00:00
fetched_at: 2026-06-24T22:10:29.818122+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "透過啟動修補（activation patching）技術揭示 Gemma-2B 與 Gemma-12B-IT 模型內部的事實記憶電路，發現可分為三個階段：事實儲存、路由傳遞、讀出執行。研究表明殘差流（residual stream）在事實回憶中承擔主要責任，而非傳統認知中的注意力層。該發現對理解 LLM 內部機制、設計更有效提示與微調策略具有重要參考價值。"
key_points:
  - "Gemma 模型的事實記憶分為三階段電路：儲存→路由→讀出"
  - "殘差流而非注意力層承擔事實回憶的核心職責"
  - "啟動修補（activation patching）是解析模型內部運作的強大工具"
tags: [gemma, transformer-internals, activation-patching, mechanistic-interpretability, factual-recall]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## A Three-Phase Factual Recall Circuit in Gemma-2B and Gemma-12B-IT

透過啟動修補（activation patching）技術揭示 Gemma-2B 與 Gemma-12B-IT 模型內部的事實記憶電路，發現可分為三個階段：事實儲存、路由傳遞、讀出執行。研究表明殘差流（residual stream）在事實回憶中承擔主要責任，而非傳統認知中的注意力層。該發現對理解 LLM 內部機制、設計更有效提示與微調策略具有重要參考價值。

### 重點
- Gemma 模型的事實記憶分為三階段電路：儲存→路由→讀出
- 殘差流而非注意力層承擔事實回憶的核心職責
- 啟動修補（activation patching）是解析模型內部運作的強大工具

**原文：** [medium-towards-data-science](https://towardsdatascience.com/a-three-phase-factual-recall-circuit-in-gemma-2b-and-gemma-12b-it/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Activation patching reveals how facts are stored, routed, and read out across transformer layers, and why the residual stream does most of the work 
 The post A Three-Phase Factual Recall Circuit in Gemma-2B and Gemma-12B-IT appeared first on Towards Data Science .

</details>