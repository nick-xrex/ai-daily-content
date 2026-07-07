---
id: inbox_9f8c7020
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2255-medium-towards-data-science-validating-the-rag-answer-before-the-use-edce]]"
title: "Validating the RAG Answer Before the User Sees It: Spans, Quotes, and the Feedback Loop"
url: https://towardsdatascience.com/validating-the-rag-answer-before-the-user-sees-it-spans-quotes-and-the-feedback-loop/
source: medium-towards-data-science
published_at: 2026-07-06T13:30:00+00:00
fetched_at: 2026-07-07T00:41:46.831669+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文為《企業文件智能》專欄第 8 期，提出 RAG 系統驗證的新框架。作者關鍵主張：「結構化輸出只是驗證的起點，不是終點」。系統需在答案展示給用戶前，透過提取 span 與引用文本（quotes）來追蹤證據來源，並透過反饋迴路機制持續改進驗證邏輯。該方法特別適合需要可追溯性與透明度的企業應用。相比單純返回結構化 JSON，這套框架將驗證責任往前推進，從答案生成階段就開始把關。

```mermaid
graph LR
    A[RAG Query] --> B[LLM Response]
    B --> C[Structured Output]
    C --> D[Evidence Extraction<br/>Spans & Quotes]
    D --> E{Validation<br/>Check}
    E -->|Pass| F[Return Answer]
    E -->|Fail| G[Feedback Loop]
    G --> H[Improve Prompt/Logic]
    H --> B
```"
key_points:
  - "結構化輸出不等於完成驗證；需進一步提取 span、quotes 追蹤證據來源"
  - "「接受未找到」(accept not-found) 優於硬行提供錯誤答案或幻覺內容"
  - "反饋迴路允許系統在用戶看到答案前持續改進，提升可信度"
tags: [rag-validation, enterprise-document-intelligence, evidence-tracking, feedback-loop]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Validating the RAG Answer Before the User Sees It: Spans, Quotes, and the Feedback Loop

本文為《企業文件智能》專欄第 8 期，提出 RAG 系統驗證的新框架。作者關鍵主張：「結構化輸出只是驗證的起點，不是終點」。系統需在答案展示給用戶前，透過提取 span 與引用文本（quotes）來追蹤證據來源，並透過反饋迴路機制持續改進驗證邏輯。該方法特別適合需要可追溯性與透明度的企業應用。相比單純返回結構化 JSON，這套框架將驗證責任往前推進，從答案生成階段就開始把關。

```mermaid
graph LR
    A[RAG Query] --> B[LLM Response]
    B --> C[Structured Output]
    C --> D[Evidence Extraction<br/>Spans & Quotes]
    D --> E{Validation<br/>Check}
    E -->|Pass| F[Return Answer]
    E -->|Fail| G[Feedback Loop]
    G --> H[Improve Prompt/Logic]
    H --> B
```

### 重點
- 結構化輸出不等於完成驗證；需進一步提取 span、quotes 追蹤證據來源
- 「接受未找到」(accept not-found) 優於硬行提供錯誤答案或幻覺內容
- 反饋迴路允許系統在用戶看到答案前持續改進，提升可信度

**原文：** [medium-towards-data-science](https://towardsdatascience.com/validating-the-rag-answer-before-the-user-sees-it-spans-quotes-and-the-feedback-loop/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Enterprise Document Intelligence [Vol.1 #8C] - Structured output is the start of validation, not the end: check the evidence, accept not-found, loop the feedback 
 The post Validating the RAG Answer Before the User Sees It: Spans, Quotes, and the Feedback Loop appeared first on Towards Data Science .

</details>