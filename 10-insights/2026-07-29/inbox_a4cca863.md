---
id: inbox_a4cca863
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_a4cca863]]"
title: "Why Your Best Predictive Model Gives the Wrong Treatment Effect"
url: https://towardsdatascience.com/why-your-best-predictive-model-gives-the-wrong-treatment-effect/
source: medium-towards-data-science
published_at: 2026-07-29T15:00:00+00:00
fetched_at: 2026-07-31T01:37:28.775253+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章揭示機器學習領域的一個根本矛盾：最優預測模型的變數選擇（追求最小 MSE），對因果推論（causal inference）失效。當 ML 工程師用預測精度來挑選變數時，往往會系統性遺漏混淆因子（confounders），導致治療效應估計（treatment effect estimation）嚴重偏差。作者介紹貝葉斯混淆調整法（Bayesian Adjustment for Confounding, BAC）作為解決方案，結合先驗知識和貝葉斯框架來補正變數選擇的盲點。核心洞見在於：建模的目標函式若不同（預測 vs. 因果），選擇最優變數集的標準也應根本不同——預測最優 ≠ 因果最優。這對醫療、政策評估、A/B 測試等需要準確估計因果效應的應用尤為關鍵。"
key_points:
  - "預測優化陷阱：變數選擇若只看預測精度（MSE），會系統性遺漏混淆因子，破壞因果估計"
  - "因果推論的獨特需求：治療效應估計需要完整調整集（sufficient adjustment set），邏輯與預測最小化根本不同"
  - "貝葉斯混淆調整法（BAC）：用先驗知識和貝葉斯框架，補正預測驅動變數選擇的盲點"
tags: [causal-inference, ml-methodology, treatment-effect, confounder-bias]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Your Best Predictive Model Gives the Wrong Treatment Effect

文章揭示機器學習領域的一個根本矛盾：最優預測模型的變數選擇（追求最小 MSE），對因果推論（causal inference）失效。當 ML 工程師用預測精度來挑選變數時，往往會系統性遺漏混淆因子（confounders），導致治療效應估計（treatment effect estimation）嚴重偏差。作者介紹貝葉斯混淆調整法（Bayesian Adjustment for Confounding, BAC）作為解決方案，結合先驗知識和貝葉斯框架來補正變數選擇的盲點。核心洞見在於：建模的目標函式若不同（預測 vs. 因果），選擇最優變數集的標準也應根本不同——預測最優 ≠ 因果最優。這對醫療、政策評估、A/B 測試等需要準確估計因果效應的應用尤為關鍵。

### 重點
- 預測優化陷阱：變數選擇若只看預測精度（MSE），會系統性遺漏混淆因子，破壞因果估計
- 因果推論的獨特需求：治療效應估計需要完整調整集（sufficient adjustment set），邏輯與預測最小化根本不同
- 貝葉斯混淆調整法（BAC）：用先驗知識和貝葉斯框架，補正預測驅動變數選擇的盲點

**原文：** [medium-towards-data-science](https://towardsdatascience.com/why-your-best-predictive-model-gives-the-wrong-treatment-effect/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Why Your Best Predictive Model Gives the Wrong Treatment Effect

Why prediction-driven variable selection misses confounders and how Bayesian Adjustment for Confounding attempts to fix it. 
 The post Why Your Best Predictive Model Gives the Wrong Treatment Effect appeared first on Towards Data Science .

</details>