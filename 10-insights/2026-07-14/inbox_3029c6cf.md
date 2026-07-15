---
id: inbox_3029c6cf
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-medium-towards-data-science-how-much-does-it-actually-cost-to-run-a-76b0]]"
title: "How Much Does It Actually Cost to Run a Local LLM? (Euros per Million Tokens, Measured)"
url: https://towardsdatascience.com/how-much-does-it-actually-cost-to-run-a-local-llm-e-per-million-tokens-measured/
source: medium-towards-data-science
published_at: 2026-07-14T13:30:00+00:00
fetched_at: 2026-07-14T22:14:59.869660+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "實測八個本地 LLM 模型在單張 RTX 3090 GPU 上實際運行的成本，並以歐元每百萬 token 計算。測試發現成本與模型大小非線性相關：成本最低的並非參數量最小的模型，最昂貴的也不是最大模型。這個結果推翻了簡單的線性成本假設。該實測數據為本地 LLM 部署的成本預算和 ROI 分析提供了具體參考依據。"
key_points:
  - "測試環境：單張 RTX 3090，涵蓋 8 個不同本地 LLM 模型"
  - "成本與模型大小非線性關係：最便宜的不是最小模型，最貴的也不是最大模型"
  - "提供可量化的 GPU 電力成本數據（歐元/百萬 token），支援部署決策"
tags: [local-llm, cost-analysis, gpu-efficiency, rtx-3090, inference-cost]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## How Much Does It Actually Cost to Run a Local LLM? (Euros per Million Tokens, Measured)

實測八個本地 LLM 模型在單張 RTX 3090 GPU 上實際運行的成本，並以歐元每百萬 token 計算。測試發現成本與模型大小非線性相關：成本最低的並非參數量最小的模型，最昂貴的也不是最大模型。這個結果推翻了簡單的線性成本假設。該實測數據為本地 LLM 部署的成本預算和 ROI 分析提供了具體參考依據。

### 重點
- 測試環境：單張 RTX 3090，涵蓋 8 個不同本地 LLM 模型
- 成本與模型大小非線性關係：最便宜的不是最小模型，最貴的也不是最大模型
- 提供可量化的 GPU 電力成本數據（歐元/百萬 token），支援部署決策

**原文：** [medium-towards-data-science](https://towardsdatascience.com/how-much-does-it-actually-cost-to-run-a-local-llm-e-per-million-tokens-measured/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I measured the actual GPU electricity for eight local models on one RTX 3090 — and the cheapest wasn't the smallest, nor the priciest the biggest. 
 The post How Much Does It Actually Cost to Run a Local LLM? (Euros per Million Tokens, Measured) appeared first on Towards Data Science .

</details>