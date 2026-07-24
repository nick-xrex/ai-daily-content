---
id: inbox_c05bcbc0
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0149-medium-towards-data-science-why-adding-more-ai-agents-made-our-syste-f8c2]]"
title: "Why Adding More AI Agents Made Our System Slower"
url: https://towardsdatascience.com/why-adding-more-ai-agents-made-our-system-slower/
source: medium-towards-data-science
published_at: 2026-07-23T12:00:00+00:00
fetched_at: 2026-07-24T02:08:51.840921+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文揭示大規模 LLM agent 系統的反直覺性能問題：增加 agent 數量反而導致整體吞吐量下降。作者在實際部署百級 agent 規模時發現，隱藏的瓶頸並非 LLM 推理延遲，而是非同步系統的 CPU 開銷——上下文切換、任務調度、鎖競爭等微小操作在高並發下累積成主要性能殺手。這些微觀成本在調度層逐級放大，最終掩蓋 LLM 延遲。該發現打破常見擴展迷思：性能最佳化的關鍵不在盲目增加 worker，而在識別並消除 synchronization 層開銷。對 agent 架構設計者而言，應優先檢查調度層而非模型層的瓶頸。"
key_points:
  - "微小 CPU 操作（上下文管理、調度、鎖競爭）在 100+ agent 規模下累積成最大瓶頸，超過 LLM 推理延遲"
  - "非同步系統隱藏成本隨並發數指數級放大；這是常被忽視的性能殺手"
  - "性能最佳化應先檢查調度層而非模型層；盲目加 worker 會加劇隱藏開銷"
tags: [agent-scaling, async-bottleneck, performance-tuning, llm-systems]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Adding More AI Agents Made Our System Slower

本文揭示大規模 LLM agent 系統的反直覺性能問題：增加 agent 數量反而導致整體吞吐量下降。作者在實際部署百級 agent 規模時發現，隱藏的瓶頸並非 LLM 推理延遲，而是非同步系統的 CPU 開銷——上下文切換、任務調度、鎖競爭等微小操作在高並發下累積成主要性能殺手。這些微觀成本在調度層逐級放大，最終掩蓋 LLM 延遲。該發現打破常見擴展迷思：性能最佳化的關鍵不在盲目增加 worker，而在識別並消除 synchronization 層開銷。對 agent 架構設計者而言，應優先檢查調度層而非模型層的瓶頸。

### 重點
- 微小 CPU 操作（上下文管理、調度、鎖競爭）在 100+ agent 規模下累積成最大瓶頸，超過 LLM 推理延遲
- 非同步系統隱藏成本隨並發數指數級放大；這是常被忽視的性能殺手
- 性能最佳化應先檢查調度層而非模型層；盲目加 worker 會加劇隱藏開銷

**原文：** [medium-towards-data-science](https://towardsdatascience.com/why-adding-more-ai-agents-made-our-system-slower/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The hidden cost of asynchronous systems, how tiny CPU tasks quietly became our biggest bottleneck while scaling hundreds of LLM agents. 
 The post Why Adding More AI Agents Made Our System Slower appeared first on Towards Data Science .

</details>