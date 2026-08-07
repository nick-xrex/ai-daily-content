---
id: inbox_79af5460
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_79af5460]]"
title: "Pretraining, Fine-Tuning, and Instruct-Tuning an LLM with Unsloth: A Hands-On Guide to Building a..."
url: https://medium.com/@saadnaeem.dev/pretraining-fine-tuning-and-instruct-tuning-an-llm-with-unsloth-a-hands-on-guide-to-building-a-3397c0c5e40e?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-08-06T19:42:17+00:00
fetched_at: 2026-08-07T01:31:03.356295+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Unsloth 是一個微調框架，支援在本地機器訓練 Llama 3.1 8B 模型。文章展示了連續預訓練的完整工作流，以法律判例為例進行領域預訓練。隨後在 24K 法律問答對上進行指令微調。Unsloth 降低了進階微調的硬體需求與程式複雜度。這使開發者可在標準機器本地完成垂直化模型開發。該示例展示如何在專業資料集上構建領域特化 LLM。"
key_points:
  - "Unsloth + Llama 3.1 8B：本地支援連續預訓練（raw case law）+ 指令微調（24K legal QA 對）完整工作流"
  - "法律領域垂直微調實例：原始判例作預訓練語料，領域特定 QA 對進行指令對齐"
  - "開源工具民主化：降低進階微調門檻，標準硬體可執行完整流程，對中小團隊與獨立開發者可達成度高"
tags: [unsloth, llama-3.1, fine-tuning, domain-adaptation, legal-ai]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Pretraining, Fine-Tuning, and Instruct-Tuning an LLM with Unsloth: A Hands-On Guide to Building a...

Unsloth 是一個微調框架，支援在本地機器訓練 Llama 3.1 8B 模型。文章展示了連續預訓練的完整工作流，以法律判例為例進行領域預訓練。隨後在 24K 法律問答對上進行指令微調。Unsloth 降低了進階微調的硬體需求與程式複雜度。這使開發者可在標準機器本地完成垂直化模型開發。該示例展示如何在專業資料集上構建領域特化 LLM。

### 重點
- Unsloth + Llama 3.1 8B：本地支援連續預訓練（raw case law）+ 指令微調（24K legal QA 對）完整工作流
- 法律領域垂直微調實例：原始判例作預訓練語料，領域特定 QA 對進行指令對齐
- 開源工具民主化：降低進階微調門檻，標準硬體可執行完整流程，對中小團隊與獨立開發者可達成度高

**原文：** [medium-tag-llm](https://medium.com/@saadnaeem.dev/pretraining-fine-tuning-and-instruct-tuning-an-llm-with-unsloth-a-hands-on-guide-to-building-a-3397c0c5e40e?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Saad Naeem"
published_at: 2026-08-06T19:42:17+00:00
fetched_at: 2026-08-06T22:53:46.220005+00:00
content_hash: "e77e7a0148de8f33301fb98c0bf8442617472d80a69e7f90e727ceecd39c6296"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pretraining, Fine-Tuning, and Instruct-Tuning an LLM with Unsloth: A Hands-On Guide to Building a...

Train and fine-tune your own Llama 3.1 8B locally &#x2014; continued pretraining on raw case law, instruction tuning on 24K real legal Q&amp;A pairs&#x2026; Continue reading on Medium »

</details>