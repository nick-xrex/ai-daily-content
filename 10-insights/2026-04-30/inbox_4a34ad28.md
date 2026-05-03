---
id: inbox_4a34ad28
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/0133-hackernews-granite-4-1-ibm-s-8b-model-matching-32b-e110]]"
title: "Granite 4.1: IBM&#39;s 8B Model Matching 32B MoE"
url: https://firethering.com/granite-4-1-ibm-open-source-model-family/
source: hackernews
published_at: 2026-04-30T10:31:17+00:00
fetched_at: 2026-05-03T02:11:40.000788+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "IBM 發布 Granite 4.1 基礎模型家族，核心突破為 8B 密集模型在指令遵循與工具調用上匹配或超越 32B 混合專家（MoE）模型的性能。模型家族覆蓋 3B/8B/30B 參數級別的密集解碼模型，配套 Granite Vision（文檔理解）、Speech（語音）、Embeddings、Guardian（有害檢測）。訓練採用 15 兆 token 多階段方案，先廣泛預訓練再逐步轉向高質量技術科學數據，最後多階段強化學習分別優化指令遵循、對話、事實性與數學推理。該架構簡化易調優，針對企業應用成本敏感與低延遲要求的場景提供推理鏈長度短的替代方案，性能可與 Gemma、Qwen 等開源模型競爭。"
key_points:
  - "性能突破：Granite 4.1 8B (密集) == Granite 4.0 32B (MoE) 在指令遵循與工具調用上，架構更簡潔易微調"
  - "訓練哲學：重數據質量與分階段提煉勝於原始量；15 兆 token、多階段 RL、512K context 長度"
  - "企業價值：無長思維鏈、token 成本低、延遲穩定——推理模型在成本/速度重要的生產工作負載上更優"
tags: [foundation-models, ibm-granite, instruction-following, tool-calling, efficiency]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Granite 4.1: IBM's 8B Model Matching 32B MoE

IBM 發布 Granite 4.1 基礎模型家族，核心突破為 8B 密集模型在指令遵循與工具調用上匹配或超越 32B 混合專家（MoE）模型的性能。模型家族覆蓋 3B/8B/30B 參數級別的密集解碼模型，配套 Granite Vision（文檔理解）、Speech（語音）、Embeddings、Guardian（有害檢測）。訓練採用 15 兆 token 多階段方案，先廣泛預訓練再逐步轉向高質量技術科學數據，最後多階段強化學習分別優化指令遵循、對話、事實性與數學推理。該架構簡化易調優，針對企業應用成本敏感與低延遲要求的場景提供推理鏈長度短的替代方案，性能可與 Gemma、Qwen 等開源模型競爭。

### 重點
- 性能突破：Granite 4.1 8B (密集) == Granite 4.0 32B (MoE) 在指令遵循與工具調用上，架構更簡潔易微調
- 訓練哲學：重數據質量與分階段提煉勝於原始量；15 兆 token、多階段 RL、512K context 長度
- 企業價值：無長思維鏈、token 成本低、延遲穩定——推理模型在成本/速度重要的生產工作負載上更優

**原文：** [hackernews](https://firethering.com/granite-4-1-ibm-open-source-model-family/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<a href="https:&#x2F;&#x2F;research.ibm.com&#x2F;blog&#x2F;granite-4-1-ai-foundation-models" rel="nofollow">https:&#x2F;&#x2F;research.ibm.com&#x2F;blog&#x2F;granite-4-1-ai-foundation-mode...</a>

</details>