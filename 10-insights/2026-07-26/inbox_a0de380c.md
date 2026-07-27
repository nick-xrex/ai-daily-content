---
id: inbox_a0de380c
date: 2026-07-26
source_ref: "[[00-inbox/2026-07-26/0123-simon-willison-an-inside-look-at-the-relay-market-power-f120]]"
title: "An Inside Look at the Relay Market Powering Token Resellers and Fraud"
url: https://simonwillison.net/2026/Jul/26/relay-market/#atom-everything
source: simon-willison
published_at: 2026-07-26T19:30:54+00:00
fetched_at: 2026-07-27T01:35:26.379768+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "安全研究者 Matt Lenhard 調查揭露了圍繞 LLM API token 轉售的地下市場生態，主要集中在中國。轉售商透過濫用免費試用、代理未受保護的支持機器人、利用被盜信用卡或發起退款詐騙，以低於官方定價的折扣出售 API 訪問。該市場採用開源代理軟體（one-api 與更活躍的 new-api fork）進行負載均衡與憑證池管理。買家涵蓋三類：追求低成本 token、規避地理限制、以及採集數據用於模型蒸餾。Simon Willison 指出此生態系統的存在意味著 LLM 服務商急需實施嚴格的美元支出上限機制，以保護未受保護的端點免受大規模濫用。"
key_points:
  - "市場主要位於中國，採用 one-api/new-api 開源代理軟體，通過免費試用、支持機器人代理、被盜信用卡、退款詐騙等方式實現折扣"
  - "買家分為三類：成本優化、地理限制規避（跨地區訪問）、以及模型蒸餾訓練數據收集"
  - "關鍵安全建議：LLM 供應商需實施每日/月度美元支出上限，使未授權使用觸發自動停止，防止單一洩露端點導致大規模損失"
tags: [llm-security, token-resale, api-abuse, marketplace-fraud, china-market]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## An Inside Look at the Relay Market Powering Token Resellers and Fraud

安全研究者 Matt Lenhard 調查揭露了圍繞 LLM API token 轉售的地下市場生態，主要集中在中國。轉售商透過濫用免費試用、代理未受保護的支持機器人、利用被盜信用卡或發起退款詐騙，以低於官方定價的折扣出售 API 訪問。該市場採用開源代理軟體（one-api 與更活躍的 new-api fork）進行負載均衡與憑證池管理。買家涵蓋三類：追求低成本 token、規避地理限制、以及採集數據用於模型蒸餾。Simon Willison 指出此生態系統的存在意味著 LLM 服務商急需實施嚴格的美元支出上限機制，以保護未受保護的端點免受大規模濫用。

### 重點
- 市場主要位於中國，採用 one-api/new-api 開源代理軟體，通過免費試用、支持機器人代理、被盜信用卡、退款詐騙等方式實現折扣
- 買家分為三類：成本優化、地理限制規避（跨地區訪問）、以及模型蒸餾訓練數據收集
- 關鍵安全建議：LLM 供應商需實施每日/月度美元支出上限，使未授權使用觸發自動停止，防止單一洩露端點導致大規模損失

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/26/relay-market/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

An Inside Look at the Relay Market Powering Token Resellers and Fraud 
Fascinating investigation by Matt Lenhard into the market that has grown up around reselling LLM tokens at a discount by pooling API keys from various sources. 
 This looks to be mostly a thing in China. Resellers sell access to an LLM proxy that offers significant discounts on regular API pricing, which they achieve by abusing free trials, proxying through unprotected support bots, or sometimes through stolen credit cards or chargeback attacks. 
 The software they are using for these proxies is open source - mostly one-api and its more actively developed fork new-api , both legitimate API proxy products which can be used to load. balance requests across a pool of API credentials. 
 The buyers are seeking cheap tokens, avoiding geo-restrictions, and in some cases collecting data for model distillation. 
 I've been cautious about exposing my own LLM-driven applications publicly out of fear of abuse leading to big token bills. The existence of this marketplace makes me even more cautious: there's now an entire ecosystem that can profit from finding a new unprotected endpoint to exploit. 
 LLM vendors really need to get better at offering strict caps for their API keys. I want my LLM apps to stop working the moment they hit a dollar threshold I've set for a period of time. 
 Here's the (Chinese language) forum thread that served as the principal source for Matt's article.

 Via Hacker News 

 Tags: ai , generative-ai , llms , llm-pricing , ai-ethics , ai-in-china

</details>