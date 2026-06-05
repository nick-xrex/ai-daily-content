---
id: inbox_035b0a80
date: 2026-06-04
source_ref: "[[00-inbox/.../inbox_035b0a80]]"
title: "Who Evaluates the Evaluator?"
url: https://medium.com/gradient-growth/who-evaluates-the-evaluator-be5d96a74522?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-04T22:36:00+00:00
fetched_at: 2026-06-05T01:18:22.426295+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文對 LLM 在評估系統中的適用性提出深層反思。當團隊以 LLM 代替脆弱的傳統評估時，LLM 評判者本身也存在固有的系統性偏差。作者指出三類關鍵問題：LLM 評判的隨機性（非確定的回應），位置偏差（對序列中的特定位置偏好，如傾向選擇首或尾部），以及冗長偏差（對更長回應的傾向）。這些特性會直接影響評估結果的有效性。文章警示團隊不能盲目假設 LLM 評判者的客觀性，需要對評判過程本身進行監控。"
key_points:
  - "LLM 評判者具備三類系統性偏差：隨機性、位置偏差（對序列位置的選項有傾向）、冗長偏差（傾向於選擇較長的回應）"
  - "這些偏差會影響評估結果，使 LLM 的比較評分產生結構性失真，不能視為客觀標準"
  - "用 LLM 評估 LLM 時，需對評判者本身進行反思與調整，建立對評估過程的監控機制"
tags: [llm-evaluation, judge-bias, prompt-engineering]
topics: []
importance: 3
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Who Evaluates the Evaluator?

本文對 LLM 在評估系統中的適用性提出深層反思。當團隊以 LLM 代替脆弱的傳統評估時，LLM 評判者本身也存在固有的系統性偏差。作者指出三類關鍵問題：LLM 評判的隨機性（非確定的回應），位置偏差（對序列中的特定位置偏好，如傾向選擇首或尾部），以及冗長偏差（對更長回應的傾向）。這些特性會直接影響評估結果的有效性。文章警示團隊不能盲目假設 LLM 評判者的客觀性，需要對評判過程本身進行監控。

### 重點
- LLM 評判者具備三類系統性偏差：隨機性、位置偏差（對序列位置的選項有傾向）、冗長偏差（傾向於選擇較長的回應）
- 這些偏差會影響評估結果，使 LLM 的比較評分產生結構性失真，不能視為客觀標準
- 用 LLM 評估 LLM 時，需對評判者本身進行反思與調整，建立對評估過程的監控機制

**原文：** [medium-tag-llm](https://medium.com/gradient-growth/who-evaluates-the-evaluator-be5d96a74522?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Dr. Lester Leong"
published_at: 2026-06-04T22:36:00+00:00
fetched_at: 2026-06-05T00:41:05.754283+00:00
content_hash: "4ba84f4f5a8cf6a1ee99e1a4e2f537364b15289f7e46a0be5b69991e2bbdbc01"
lang: en
caption_quality: None
raw: true
topics: []
---

# Who Evaluates the Evaluator?

You replaced your flaky eval with an LLM judge. But your judge is a model too: stochastic, position-biased, and verbosity-biased. Here is&#x2026; Continue reading on Gradient Growth »

</details>