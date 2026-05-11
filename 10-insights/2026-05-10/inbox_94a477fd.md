---
id: inbox_94a477fd
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_94a477fd]]"
title: "Stop Treating ATT&amp;CK Mapping as a Single-Label Problem"
url: https://medium.com/@zsjstart/stop-treating-att-ck-mapping-as-a-single-label-problem-bcfa2a381fe6?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-10T15:46:34+00:00
fetched_at: 2026-05-11T02:16:35.061223+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ATT&CK mapping 不應視為單標籤分類問題。傳統方法（準確度60-70%）的許多「誤差」實際上是合理的替代解釋，源自granularity、parent vs sub-technique、analyst perspective 的差異。LLM方案不依賴fine-tuning或RAG，而是通過prompt engineering leverage隱含的cybersecurity知識，將mapping分解為邏輯步驟：identify behavior → analyze implementation → reason about ATT&CK options → select techniques。gpt-oss-120b 達成80%直接準確度，額外10%為defensible alternative，合計約90%有效準確度。關鍵是reasoning transparency（說明why）與multi-label支持。"
key_points:
  - "單標籤模型低估實際準確度：60-70% 「誤差」中許多是同等有效的替代mapping"
  - "LLM方案避免fine-tuning/supervised/RAG，僅用prompt engineering + reasoning transparency"
  - "gpt-oss-120b 達 80% direct + 10% defensible = 90% 有效準確度；multi-label flexibility 比accuracy score更重要"
tags: [attack-mapping, prompt-engineering, cybersecurity, multi-label-classification, reasoning-transparency]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Treating ATT&CK Mapping as a Single-Label Problem

ATT&CK mapping 不應視為單標籤分類問題。傳統方法（準確度60-70%）的許多「誤差」實際上是合理的替代解釋，源自granularity、parent vs sub-technique、analyst perspective 的差異。LLM方案不依賴fine-tuning或RAG，而是通過prompt engineering leverage隱含的cybersecurity知識，將mapping分解為邏輯步驟：identify behavior → analyze implementation → reason about ATT&CK options → select techniques。gpt-oss-120b 達成80%直接準確度，額外10%為defensible alternative，合計約90%有效準確度。關鍵是reasoning transparency（說明why）與multi-label支持。

### 重點
- 單標籤模型低估實際準確度：60-70% 「誤差」中許多是同等有效的替代mapping
- LLM方案避免fine-tuning/supervised/RAG，僅用prompt engineering + reasoning transparency
- gpt-oss-120b 達 80% direct + 10% defensible = 90% 有效準確度；multi-label flexibility 比accuracy score更重要

**原文：** [medium-tag-llm](https://medium.com/@zsjstart/stop-treating-att-ck-mapping-as-a-single-label-problem-bcfa2a381fe6?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Dr. Shujie Zhao"
published_at: 2026-05-10T15:46:34+00:00
fetched_at: 2026-05-10T22:37:10.204996+00:00
content_hash: "32e625d4f380a76761842511ccd635af771f784541f76fdfdffcb6ed44a0f979"
lang: en
caption_quality: None
raw: true
topics: []
---

# Stop Treating ATT&CK Mapping as a Single-Label Problem

LLM-powered ATT&amp;CK mapping without fine-tuning or RAG Continue reading on Medium »

</details>