---
id: inbox_a372ec04
date: 2026-06-06
source_ref: "[[00-inbox/2026-06-06/0052-medium-towards-data-science-my-scipy-ode-solver-was-killing-my-bayes-988e]]"
title: "My SciPy ODE Solver Was Killing My Bayesian Inference: A Cosmologist’s Honest Account of Discovering Diffrax"
url: https://towardsdatascience.com/my-scipy-ode-solver-was-killing-my-bayesian-inference-a-cosmologists-honest-account-of-discovering-diffrax/
source: medium-towards-data-science
published_at: 2026-06-06T13:00:00+00:00
fetched_at: 2026-06-07T00:56:24.449674+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "宇宙學家在進行貝葉斯推論計算時發現 SciPy 的 ODE solver 成為效能瓶頸。經深入調查後發現 Diffrax 庫提供更高效的替代方案。文章詳述遷移的成本考量、效能收益以及實務中犯下的三個重要錯誤。此案例說明選擇合適的數值計算工具對科學計算效率的關鍵影響，具有跨領域借鑒價值。"
key_points:
  - "SciPy ODE solver 在密集貝葉斯推論中成為瓶頸，Diffrax 提供顯著性能改進"
  - "遷移涉及成本與效能收益的量化權衡，需謹慎評估"
  - "記錄實務中的三個常見錯誤，提供學習與避坑指南"
tags: [ode-solver, bayesian-inference, diffrax, numerical-methods, performance-optimization]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## My SciPy ODE Solver Was Killing My Bayesian Inference: A Cosmologist’s Honest Account of Discovering Diffrax

宇宙學家在進行貝葉斯推論計算時發現 SciPy 的 ODE solver 成為效能瓶頸。經深入調查後發現 Diffrax 庫提供更高效的替代方案。文章詳述遷移的成本考量、效能收益以及實務中犯下的三個重要錯誤。此案例說明選擇合適的數值計算工具對科學計算效率的關鍵影響，具有跨領域借鑒價值。

### 重點
- SciPy ODE solver 在密集貝葉斯推論中成為瓶頸，Diffrax 提供顯著性能改進
- 遷移涉及成本與效能收益的量化權衡，需謹慎評估
- 記錄實務中的三個常見錯誤，提供學習與避坑指南

**原文：** [medium-towards-data-science](https://towardsdatascience.com/my-scipy-ode-solver-was-killing-my-bayesian-inference-a-cosmologists-honest-account-of-discovering-diffrax/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

what it costs, what it gains and the three mistakes that I make 
 The post My SciPy ODE Solver Was Killing My Bayesian Inference: A Cosmologist’s Honest Account of Discovering Diffrax appeared first on Towards Data Science .

</details>