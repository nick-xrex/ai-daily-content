---
id: inbox_d5ac02ab
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2200-lilian-weng-scaling-laws-carefully-6401]]"
title: "Scaling Laws, Carefully"
url: https://lilianweng.github.io/posts/2026-06-24-scaling-laws/
source: lilian-weng
published_at: 2026-06-24T00:00:00+00:00
fetched_at: 2026-06-25T22:10:39.722400+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "縮放律是深度學習最重要的實證發現：訓練損失隨著模型大小、數據量和計算量的增長按冪律遞減，在對數-對數圖上呈直線。Lilian Weng 的文章框架化了這個觀察，強調其核心問題是如何在模型大小(N)和數據量(D)之間最優分配寶貴的計算資源(C)。該理論對指導深度學習系統的訓練策略至關重要，提供了預測性強的關係模型。"
key_points:
  - "縮放律三角：模型大小(N)、數據量(D)、計算量(C) 遵循冪律關係，在 log-log 圖上呈直線"
  - "核心實務問題：計算資源如何在模型大小和數據量之間分配以最小化訓練損失"
  - "框架價值：提供可預測的關係模型，指導訓練策略和資源配置決策"
tags: [scaling-laws, deep-learning, training-optimization, foundation-models, empirical-laws]
topics: []
importance: 3
novelty: 2
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Scaling Laws, Carefully

縮放律是深度學習最重要的實證發現：訓練損失隨著模型大小、數據量和計算量的增長按冪律遞減，在對數-對數圖上呈直線。Lilian Weng 的文章框架化了這個觀察，強調其核心問題是如何在模型大小(N)和數據量(D)之間最優分配寶貴的計算資源(C)。該理論對指導深度學習系統的訓練策略至關重要，提供了預測性強的關係模型。

### 重點
- 縮放律三角：模型大小(N)、數據量(D)、計算量(C) 遵循冪律關係，在 log-log 圖上呈直線
- 核心實務問題：計算資源如何在模型大小和數據量之間分配以最小化訓練損失
- 框架價值：提供可預測的關係模型，指導訓練策略和資源配置決策

**原文：** [lilian-weng](https://lilianweng.github.io/posts/2026-06-24-scaling-laws/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Scaling laws are one of the most critical empirical findings in deep learning. The observation is simple in form: the training loss $L$ decreases predictably as we scale up model size $N$, dataset size $D$, and compute $C$, following a power-law curve, which appears as a straight line on a log-log plot. We can view scaling laws as a framework for describing the relationship between compute, loss, model size and data; at its core, it is about how to allocate precious compute optimally between $N$ and $D$.

</details>