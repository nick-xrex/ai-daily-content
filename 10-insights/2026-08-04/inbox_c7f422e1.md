---
id: inbox_c7f422e1
date: 2026-08-04
source_ref: "[[00-inbox/.../inbox_c7f422e1]]"
title: "The LLM in my app is not allowed to decide anything"
url: https://shanliu.medium.com/the-llm-in-my-app-is-not-allowed-to-decide-anything-402e7f8fdd8a?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-08-04T21:58:22+00:00
fetched_at: 2026-08-05T02:14:20.808905+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者 Shan Liu 分享在 BaZi（中國四柱命理）應用中集成 LLM 的經驗。指出命理是「LLM 真實性最差的領域」之一。核心設計原則：嚴格限制 LLM 的決策權，不允許其直接給出最終判斷，而應將其作為輔助工具搭配人工驗證。"
key_points:
  - "在命理應用中 LLM 真實性是致命風險，不應被允許作主決策者"
  - "設計原則：LLM 輸出需人工核驗與多重約束機制"
  - "領域特性決定 LLM 角色邊界（工具輔助 vs 決策主體）"
tags: [llm-constraints, truthfulness-domains, application-design]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The LLM in my app is not allowed to decide anything

作者 Shan Liu 分享在 BaZi（中國四柱命理）應用中集成 LLM 的經驗。指出命理是「LLM 真實性最差的領域」之一。核心設計原則：嚴格限制 LLM 的決策權，不允許其直接給出最終判斷，而應將其作為輔助工具搭配人工驗證。

### 重點
- 在命理應用中 LLM 真實性是致命風險，不應被允許作主決策者
- 設計原則：LLM 輸出需人工核驗與多重約束機制
- 領域特性決定 LLM 角色邊界（工具輔助 vs 決策主體）

**原文：** [medium-tag-llm](https://shanliu.medium.com/the-llm-in-my-app-is-not-allowed-to-decide-anything-402e7f8fdd8a?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Shan Liu"
published_at: 2026-08-04T21:58:22+00:00
fetched_at: 2026-08-04T22:51:17.239101+00:00
content_hash: "1786115d0e2bd840e37f70e11480f7410c4c4d162ecb0819ff3948d8b007e078"
lang: en
caption_quality: None
raw: true
topics: []
---

# The LLM in my app is not allowed to decide anything

I build software in the single worst domain for LLM truthfulness: fortune-telling. A BaZi (Chinese Four-Pillars astrology) reading app&#x2026; Continue reading on Medium »

</details>