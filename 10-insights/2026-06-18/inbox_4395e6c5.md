---
id: inbox_4395e6c5
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-medium-tag-llm-raft-teach-llms-to-be-better-at-rag-9ab9]]"
title: "RAFT: Teach LLMs to be better at RAG"
url: https://medium.com/@nageshchauhanc4/raft-teach-llms-to-be-better-at-rag-9db6456a9965?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-18T13:02:37+00:00
fetched_at: 2026-06-18T22:14:42.168109+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RAFT（檢索增強微調）是 UC Berkeley 研究者開發的方法，結合領域特定微調與檢索增強生成（RAG）兩者優勢。傳統領域微調易過擬合導致幻覺，RAG 有時檢索到無關文件。RAFT 使用包含問題、相關與無關文件、思維鏈答案的合成資料集進行訓練，類似「學生在開卷考前先讀教科書比只在考試時查閱更有優勢」。在維基百科、API 文件、醫療研究等多個資料集測試均優於基準方案；Meta Llama 2 7B 等模型能更有效從檢索內容中萃取資訊。"
key_points:
  - "RAFT 用合成資料集（含相關/無關文件＋思維鏈）微調模型，達到比純 RAG 或領域微調更好效果"
  - "在維基百科問答、API 文件、醫療研究三類資料集測試，優於零樣本提示、標準 RAG、單純領域微調"
  - "使 Llama 2 7B 等中等規模模型能在檢索上下文中更有效識別和使用相關資訊"
tags: [raft, retrieval-augmented-generation, fine-tuning, domain-adaptation, llama]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## RAFT: Teach LLMs to be better at RAG

RAFT（檢索增強微調）是 UC Berkeley 研究者開發的方法，結合領域特定微調與檢索增強生成（RAG）兩者優勢。傳統領域微調易過擬合導致幻覺，RAG 有時檢索到無關文件。RAFT 使用包含問題、相關與無關文件、思維鏈答案的合成資料集進行訓練，類似「學生在開卷考前先讀教科書比只在考試時查閱更有優勢」。在維基百科、API 文件、醫療研究等多個資料集測試均優於基準方案；Meta Llama 2 7B 等模型能更有效從檢索內容中萃取資訊。

### 重點
- RAFT 用合成資料集（含相關/無關文件＋思維鏈）微調模型，達到比純 RAG 或領域微調更好效果
- 在維基百科問答、API 文件、醫療研究三類資料集測試，優於零樣本提示、標準 RAG、單純領域微調
- 使 Llama 2 7B 等中等規模模型能在檢索上下文中更有效識別和使用相關資訊

**原文：** [medium-tag-llm](https://medium.com/@nageshchauhanc4/raft-teach-llms-to-be-better-at-rag-9db6456a9965?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

&#x201c;Blending the Best of Both Worlds: How &#x2018;Retrieval-Augmented Fine-Tuning&#x2019; Merges Retrieval-Augmented Generation with Fine-Tuning for&#x2026; Continue reading on Medium »

</details>