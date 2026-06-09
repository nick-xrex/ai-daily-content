---
id: inbox_4de33c4c
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-simon-willison-setting-a-custom-price-for-a-model-in-ag-2a40]]"
title: "Setting a custom price for a model in AgentsView"
url: https://simonwillison.net/2026/Jun/9/agentsview-custom-model-price/#atom-everything
source: simon-willison
published_at: 2026-06-09T21:35:31+00:00
fetched_at: 2026-06-09T22:07:11.744599+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發現 Claude Fable 5 才剛推出，AgentsView（一款追蹤本地編碼代理的 token 用量工具）的定價數據庫尚未包含此新模型。他用 Fable 反向工程 AgentsView 的代碼，摸索出設定自訂價格的方法，並分享了可套用的配置方案。這個技巧讓開發者在新模型未被納入官方定價前，能夠手動追蹤自己的使用費用。"
key_points:
  - "Claude Fable 5 發布當天被用來反向工程 AgentsView，展示 Fable 編碼能力可勝任代碼審查類任務"
  - "AgentsView 用 treemap 視覺化單日跨專案的 token 用量分佈，幫助開發者監控代理成本"
  - "自訂定價設定可在新模型推出但定價數據庫滯後的過渡期應急"
tags: [agentsview, claude-fable-5, llm-pricing, token-usage, developer-tools]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Setting a custom price for a model in AgentsView

Simon Willison 發現 Claude Fable 5 才剛推出，AgentsView（一款追蹤本地編碼代理的 token 用量工具）的定價數據庫尚未包含此新模型。他用 Fable 反向工程 AgentsView 的代碼，摸索出設定自訂價格的方法，並分享了可套用的配置方案。這個技巧讓開發者在新模型未被納入官方定價前，能夠手動追蹤自己的使用費用。

### 重點
- Claude Fable 5 發布當天被用來反向工程 AgentsView，展示 Fable 編碼能力可勝任代碼審查類任務
- AgentsView 用 treemap 視覺化單日跨專案的 token 用量分佈，幫助開發者監控代理成本
- 自訂定價設定可在新模型推出但定價數據庫滯後的過渡期應急

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/9/agentsview-custom-model-price/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TIL: Setting a custom price for a model in AgentsView 
 I've been really enjoying AgentsView by Wes McKinney as a tool for exploring my token usage across different coding agents running on my laptop. 
 Claude Fable 5 came out today and wasn't yet included in the pricing database AgentsView uses. I used Fable to reverse-engineer AgentsView and figured out this recipe for setting custom prices. 
 Here's my Claude Fable 5 usage for today so far, plotted by AgentsView as a treemap across my different local projects: 
 
 
 
 Tags: ai , generative-ai , llms , llm-pricing

</details>