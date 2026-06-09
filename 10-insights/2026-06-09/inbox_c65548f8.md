---
id: inbox_c65548f8
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-medium-tag-llm-what-really-happens-when-you-talk-to-an-59ac]]"
title: "What Really Happens When You Talk to an LLM"
url: https://medium.com/@harshdaga18/what-really-happens-when-you-talk-to-an-llm-0811448b2c0f?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-09T20:09:17+00:00
fetched_at: 2026-06-09T22:11:06.252047+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "該系列文章開篇「AI 基礎設施工程」系列，第一週聚焦 LLM 核心概念。文章分解講解訓練（training）與推理（inference）兩個不同階段的計算特性與資源成本。深入解釋 Token 的定義、Prefill 階段（模型處理提示詞）與 Decode 階段（逐個生成回應 token）的機制。文章旨在系統化介紹 LLM 運作的底層原理，幫助開發者與基礎設施工程師瞭解對話系統的實際處理流程與瓶頸。適合想深入理解 LLM 效能特徵、延遲特性與成本考量的技術人員。

```mermaid
graph LR
    T[\"用戶提示 (Tokens)\"]
    P[\"Prefill 階段\"]
    D[\"Decode 階段\"]
    O[\"輸出\"]
    T -->|處理提示詞| P
    P -->|轉換為初始狀態| D
    D -->|逐 token 遞迴生成| D
    D -->|完成| O
    style P fill:#ffcccc
    style D fill:#ccccff
```"
key_points:
  - "訓練 vs 推理階段：兩個截然不同的計算流程，成本與延遲特性迥異"
  - "Prefill 與 Decode 拆解：prefill 一次性處理整個提示詞，decode 逐 token 遞迴生成"
  - "基礎設施視角優化：理解 token 流動與階段特性，找出系統瓶頸與優化空間"
tags: [llm-infrastructure, tokens, prefill-decode, inference]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## What Really Happens When You Talk to an LLM

該系列文章開篇「AI 基礎設施工程」系列，第一週聚焦 LLM 核心概念。文章分解講解訓練（training）與推理（inference）兩個不同階段的計算特性與資源成本。深入解釋 Token 的定義、Prefill 階段（模型處理提示詞）與 Decode 階段（逐個生成回應 token）的機制。文章旨在系統化介紹 LLM 運作的底層原理，幫助開發者與基礎設施工程師瞭解對話系統的實際處理流程與瓶頸。適合想深入理解 LLM 效能特徵、延遲特性與成本考量的技術人員。

```mermaid
graph LR
    T["用戶提示 (Tokens)"]
    P["Prefill 階段"]
    D["Decode 階段"]
    O["輸出"]
    T -->|處理提示詞| P
    P -->|轉換為初始狀態| D
    D -->|逐 token 遞迴生成| D
    D -->|完成| O
    style P fill:#ffcccc
    style D fill:#ccccff
```

### 重點
- 訓練 vs 推理階段：兩個截然不同的計算流程，成本與延遲特性迥異
- Prefill 與 Decode 拆解：prefill 一次性處理整個提示詞，decode 逐 token 遞迴生成
- 基礎設施視角優化：理解 token 流動與階段特性，找出系統瓶頸與優化空間

**原文：** [medium-tag-llm](https://medium.com/@harshdaga18/what-really-happens-when-you-talk-to-an-llm-0811448b2c0f?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AI Infrastructure Engineering &#x2014; Week 1: LLMs, training vs. inference, tokens, prefill, and decode. Continue reading on Medium »

</details>