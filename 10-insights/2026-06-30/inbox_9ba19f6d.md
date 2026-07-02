---
id: inbox_9ba19f6d
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2332-medium-towards-data-science-context-engineering-for-rag-the-four-typ-c4be]]"
title: "Context Engineering for RAG : The Four Typed Inputs Behind Every RAG Answer"
url: https://towardsdatascience.com/context-engineering-for-rag-the-four-typed-inputs-behind-every-rag-answer/
source: medium-towards-data-science
published_at: 2026-06-30T16:30:00+00:00
fetched_at: 2026-07-02T00:26:30.667122+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Context Engineering 是 RAG 系統的新興框架，於 2025 年由 Tobi Lütke 和 Andrej Karpathy 正式命名。該框架將 RAG 輸入組織為四種類型的上下文，每個文檔的各類型輸入獨立生成，最終聚合到單一 LLM 呼叫以提升效率與精確度。此框架提供系統化思考方式，後續工作涵蓋語料庫層級、對話延續與工具整合。"
key_points:
  - "四類型上下文輸入模型（Four Typed Inputs）提供 RAG 設計的系統框架"
  - "各類型輸入獨立發射、最終聚合至單一 LLM 呼叫，提升處理效率"
  - "由業界重量級人物正式命名，已成為企業文檔智慧系統的標準術語"
tags: [rag, context-engineering, retrieval-augmented-generation, llm-design]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Context Engineering for RAG : The Four Typed Inputs Behind Every RAG Answer

Context Engineering 是 RAG 系統的新興框架，於 2025 年由 Tobi Lütke 和 Andrej Karpathy 正式命名。該框架將 RAG 輸入組織為四種類型的上下文，每個文檔的各類型輸入獨立生成，最終聚合到單一 LLM 呼叫以提升效率與精確度。此框架提供系統化思考方式，後續工作涵蓋語料庫層級、對話延續與工具整合。

### 重點
- 四類型上下文輸入模型（Four Typed Inputs）提供 RAG 設計的系統框架
- 各類型輸入獨立發射、最終聚合至單一 LLM 呼叫，提升處理效率
- 由業界重量級人物正式命名，已成為企業文檔智慧系統的標準術語

**原文：** [medium-towards-data-science](https://towardsdatascience.com/context-engineering-for-rag-the-four-typed-inputs-behind-every-rag-answer/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Enterprise Document Intelligence [Vol.1 #7bis] - Tobi Lütke and Andrej Karpathy named the practice in 2025. For a single document, each brick emits typed pieces that converge on one LLM call. Corpus, conversation, and tool extensions are follow-up work 
 The post Context Engineering for RAG : The Four Typed Inputs Behind Every RAG Answer appeared first on Towards Data Science .

</details>