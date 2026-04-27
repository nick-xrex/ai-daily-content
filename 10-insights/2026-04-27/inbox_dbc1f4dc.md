---
id: inbox_dbc1f4dc
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0956-medium-tag-llm-why-large-language-models-forget-early-c-f9e9]]"
title: "Why Large Language Models “Forget” Early Context (and the Math Behind It)"
url: https://medium.com/@majid.golshadi/why-large-language-models-forget-early-context-and-the-math-behind-it-397156bac9b3?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-04-27T07:31:01+00:00
fetched_at: 2026-04-27T10:10:00.041850+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM「遺忘」早期context的根本原因在於self-attention的數學特性。Attention權重必須sum to 1（固定預算），context增長時每個token獲得的基礎attention反比下降（1萬token時~0.01%，100 token時~1%）。Softmax exponential weighting將微小分數差異（如2點）放大為7倍attention差異，導致最近、語義相關的token輕易壓過早期指令。Positional encoding對鄰近token有幾何優勢。在多步驟workflow中，若每步保留90%的constraint，5步後僅剩59%（指數衰減）。模型傾向信任自己的摘要勝於原始輸入，因為壓縮文本獲得更高attention分數。解決方案不在larger models或longer context，而在workflow engineering：重複「釘住」critical constraints於context末尾維持競爭attention分數。"
key_points:
  - "Attention預算固定（sum to 1），context擴張導致每token baseline attention反比衰減；Softmax amplification將score差2點擴大為7倍attention優勢"
  - "多步驟workflow指數衰減：每步損失10%，5步後僅剩59%；模型傾向信任自己的摘要而非原始messy input，形成正反饋迴圈"
  - "Long context window無法解決召回品質問題，工程方案是workflow-level的重複pinning：在context末尾反覆重述critical constraints以維持attention競爭力"
tags: [context-window, attention-mechanism, llm-limitations, softmax, workflow-engineering]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Large Language Models “Forget” Early Context (and the Math Behind It)

LLM「遺忘」早期context的根本原因在於self-attention的數學特性。Attention權重必須sum to 1（固定預算），context增長時每個token獲得的基礎attention反比下降（1萬token時~0.01%，100 token時~1%）。Softmax exponential weighting將微小分數差異（如2點）放大為7倍attention差異，導致最近、語義相關的token輕易壓過早期指令。Positional encoding對鄰近token有幾何優勢。在多步驟workflow中，若每步保留90%的constraint，5步後僅剩59%（指數衰減）。模型傾向信任自己的摘要勝於原始輸入，因為壓縮文本獲得更高attention分數。解決方案不在larger models或longer context，而在workflow engineering：重複「釘住」critical constraints於context末尾維持競爭attention分數。

### 重點
- Attention預算固定（sum to 1），context擴張導致每token baseline attention反比衰減；Softmax amplification將score差2點擴大為7倍attention優勢
- 多步驟workflow指數衰減：每步損失10%，5步後僅剩59%；模型傾向信任自己的摘要而非原始messy input，形成正反饋迴圈
- Long context window無法解決召回品質問題，工程方案是workflow-level的重複pinning：在context末尾反覆重述critical constraints以維持attention競爭力

**原文：** [medium-tag-llm](https://medium.com/@majid.golshadi/why-large-language-models-forget-early-context-and-the-math-behind-it-397156bac9b3?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@majid.golshadi/why-large-language-models-forget-early-context-and-the-math-behind-it-397156bac9b3?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/1536/1*RVp6aT2nuiFzjJgYYcNKfQ.png" width="1536" /></a></p><p class="medium-feed-snippet">If you have worked with Large Language Models (LLMs) long enough &#x2014; whether in chat-based products, translation pipelines, research&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@majid.golshadi/why-large-language-models-forget-early-context-and-the-math-behind-it-397156bac9b3?source=rss------large_language_models-5">Continue reading on Medium »</a></p></div>

</details>