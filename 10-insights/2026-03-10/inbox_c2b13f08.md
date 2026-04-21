---
id: inbox_c2b13f08
date: 2026-03-10
source_ref: "[[00-inbox/2026-03-10/0158-openai-blog-improving-instruction-hierarchy-in-front-880c]]"
title: "Improving instruction hierarchy in frontier LLMs"
url: https://openai.com/index/instruction-hierarchy-challenge
source: openai-blog
published_at: 2026-03-10T11:00:00+00:00
fetched_at: 2026-04-21T02:11:51.348562+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 推出 IH-Challenge 訓練方法，教導前沿 LLMs 優先執行來自可信來源的指令，改進模型的指令層級結構和安全可控性。此方案直接強化模型對 prompt injection 攻擊的抵抗力，為安全部署大型語言模型提供新途徑。IH-Challenge 針對指令衝突的根本問題進行訓練，而非事後防禦。"
key_points:
  - "IH-Challenge 訓練方法強化指令優先級學習"
  - "改進指令層級結構以提升 prompt injection 抵抗力"
  - "提升前沿 LLMs 的安全可控性"
tags: [instruction-hierarchy, prompt-injection, safety, training, frontier-models]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## Improving instruction hierarchy in frontier LLMs

OpenAI 推出 IH-Challenge 訓練方法，教導前沿 LLMs 優先執行來自可信來源的指令，改進模型的指令層級結構和安全可控性。此方案直接強化模型對 prompt injection 攻擊的抵抗力，為安全部署大型語言模型提供新途徑。IH-Challenge 針對指令衝突的根本問題進行訓練，而非事後防禦。

### 重點
- IH-Challenge 訓練方法強化指令優先級學習
- 改進指令層級結構以提升 prompt injection 抵抗力
- 提升前沿 LLMs 的安全可控性

**原文：** [openai-blog](https://openai.com/index/instruction-hierarchy-challenge)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

IH-Challenge trains models to prioritize trusted instructions, improving instruction hierarchy, safety steerability, and resistance to prompt injection attacks.

</details>
