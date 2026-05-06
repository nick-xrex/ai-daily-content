---
id: inbox_899f7cf0
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1002-medium-tag-llm-38-worse-on-64k-than-on-8k-same-model-sa-e4e7]]"
title: "38% Worse on 64k Than on 8k. Same Model. Same Task."
url: https://medium.com/@natevoss.dev/38-worse-on-64k-than-on-8k-same-model-same-task-2ba7bac7b6bf?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-06T06:23:08+00:00
fetched_at: 2026-05-06T10:16:15.638958+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者實測發現同一模型在 64k context window 下性能大幅下降：分類任務準確度從 91% 跌至 56%。核心發現：（1）分類/抽取任務應用最小 context size + 少量範例，寬 context 會導致模型發明不存在的類別；（2）綜合任務受益於更大 window，但在 30k 後出現衰退，模型開始過度強調近期信息（近期偏差）；（3）關鍵原則：選擇 context 應基於「任務需求」而非「模型容量」；透過自有 eval set 驗證收益，而非盲目信任模型卡宣傳。啟示：context 是預算而非功能。

```mermaid
graph TD
    A[同模型同任務 8k vs 64k] --> B[分類任務]
    A --> C[綜合任務]
    B --> B1[8k: 91%準確度]
    B --> B2[64k: 56%準確度 發明類別]
    C --> C1[64k有幫助 但30k後衰退]
    C --> C2[近期偏差 權重遠端信息降低]
    B2 --> D[結論: 最小化context]
    C2 --> E[結論: 30k上限]
    D --> F[原則: 按任務非容量選擇]
    E --> F
```"
key_points:
  - "量化數據：91% → 56% 準確度跌幅（分類任務 8k vs 64k）"
  - "框架：分類任務用最小 context + 綜合任務 30k 上限避免近期偏差"
  - "核心原則：context 大小應由任務驅動而非模型容量；自有 eval set 是唯一的真實信號"
tags: [context-window-optimization, prompt-engineering, token-efficiency, llm-eval, accuracy-regression]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## 38% Worse on 64k Than on 8k. Same Model. Same Task.

作者實測發現同一模型在 64k context window 下性能大幅下降：分類任務準確度從 91% 跌至 56%。核心發現：（1）分類/抽取任務應用最小 context size + 少量範例，寬 context 會導致模型發明不存在的類別；（2）綜合任務受益於更大 window，但在 30k 後出現衰退，模型開始過度強調近期信息（近期偏差）；（3）關鍵原則：選擇 context 應基於「任務需求」而非「模型容量」；透過自有 eval set 驗證收益，而非盲目信任模型卡宣傳。啟示：context 是預算而非功能。

```mermaid
graph TD
    A[同模型同任務 8k vs 64k] --> B[分類任務]
    A --> C[綜合任務]
    B --> B1[8k: 91%準確度]
    B --> B2[64k: 56%準確度 發明類別]
    C --> C1[64k有幫助 但30k後衰退]
    C --> C2[近期偏差 權重遠端信息降低]
    B2 --> D[結論: 最小化context]
    C2 --> E[結論: 30k上限]
    D --> F[原則: 按任務非容量選擇]
    E --> F
```

### 重點
- 量化數據：91% → 56% 準確度跌幅（分類任務 8k vs 64k）
- 框架：分類任務用最小 context + 綜合任務 30k 上限避免近期偏差
- 核心原則：context 大小應由任務驅動而非模型容量；自有 eval set 是唯一的真實信號

**原文：** [medium-tag-llm](https://medium.com/@natevoss.dev/38-worse-on-64k-than-on-8k-same-model-same-task-2ba7bac7b6bf?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@natevoss.dev/38-worse-on-64k-than-on-8k-same-model-same-task-2ba7bac7b6bf?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/2600/0*p_MmNgstHKKsXPG-" width="6014" /></a></p><p class="medium-feed-snippet">Stop Wasting Tokens: How to Optimize for Accuracy Over Length</p><p class="medium-feed-link"><a href="https://medium.com/@natevoss.dev/38-worse-on-64k-than-on-8k-same-model-same-task-2ba7bac7b6bf?source=rss------large_language_models-5">Continue reading on Medium »</a></p></div>

</details>