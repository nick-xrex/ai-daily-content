---
id: inbox_3b366ec5
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_3b366ec5]]"
title: "How to Get Relevant Chunks for Recall@k and Precision@k in RAG"
url: https://medium.com/@anshdeshwal1234/how-to-get-relevant-chunks-for-recall-k-and-precision-k-in-rag-014bb294d30c?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-10T16:25:05+00:00
fetched_at: 2026-05-11T02:16:35.058203+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "評估與改進 RAG 檢索品質的關鍵在於定義「相關性」與採用混合標註策略。核心指標為 Recall@k（頂k結果中有多少相關chunk）與 Precision@k（頂k中實際相關的比例）。文章提出二層方法：(1) Manual labeling 建立ground truth，限於50-100查詢規模；(2) Hybrid方案用人工標籤seed dataset訓練LLM標籤器擴展規模。強調迭代改進relevance定義、prompt設計、查詢多樣性與chunking策略。"
key_points:
  - "Recall@k 與 Precision@k 評估前，必須顯式定義該系統的「相關性」基準"
  - "Manual labeling = 準確度優先（ground truth），LLM labeling = 規模優先（production），混合方案平衡兩者"
  - "檢索品質改進是iterative loop：relevance definition → prompt → query diversity → chunking strategy"
tags: [rag, retrieval-evaluation, recall-precision, labeling-strategy]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Get Relevant Chunks for Recall@k and Precision@k in RAG

評估與改進 RAG 檢索品質的關鍵在於定義「相關性」與採用混合標註策略。核心指標為 Recall@k（頂k結果中有多少相關chunk）與 Precision@k（頂k中實際相關的比例）。文章提出二層方法：(1) Manual labeling 建立ground truth，限於50-100查詢規模；(2) Hybrid方案用人工標籤seed dataset訓練LLM標籤器擴展規模。強調迭代改進relevance定義、prompt設計、查詢多樣性與chunking策略。

### 重點
- Recall@k 與 Precision@k 評估前，必須顯式定義該系統的「相關性」基準
- Manual labeling = 準確度優先（ground truth），LLM labeling = 規模優先（production），混合方案平衡兩者
- 檢索品質改進是iterative loop：relevance definition → prompt → query diversity → chunking strategy

**原文：** [medium-tag-llm](https://medium.com/@anshdeshwal1234/how-to-get-relevant-chunks-for-recall-k-and-precision-k-in-rag-014bb294d30c?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Ansh Deshwal"
published_at: 2026-05-10T16:25:05+00:00
fetched_at: 2026-05-10T22:37:10.195142+00:00
content_hash: "8b8e9f827f6ff1a7004b667a470f75e9c53b9c6a57004ac7d609e0fbee0a1229"
lang: en
caption_quality: None
raw: true
topics: []
---

# How to Get Relevant Chunks for Recall@k and Precision@k in RAG

1. The Missing Piece in Retrieval Evaluation Continue reading on Medium »

</details>