---
id: inbox_7086c9ed
date: 2026-07-19
source_ref: "[[00-inbox/.../inbox_7086c9ed]]"
title: "Onboarding Agent from Scratch. Part 3: A Shape the Model Can’t Break"
url: https://medium.com/@spodsky/onboarding-agent-from-scratch-part-3-a-shape-the-model-cant-break-c566d88153af?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-07-19T17:24:33+00:00
fetched_at: 2026-07-20T01:02:51.611650+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Serge 在「從零開始打造 Onboarding Agent」系列的第三部分中，焦點聚集在將模型的輸出限制於特定且堅硬的結構形狀，使模型無法逃脫預設的輸出格式。該系列前一部分（第二階段）教導代理將回答接地在真實文檔而非依賴模型自身的知識庫；第三部分進一步解決輸出端的散漫性問題。通過強制實施格式約束，確保結構化回應而非游散的自然語言文本。此技術對於構建可靠、可預測的代理系統至關重要，特別是在需要機器可讀輸出或與下游系統整合時。"
key_points:
  - "輸出形狀約束（shape constraint）：設計堅硬的結構格式防止模型偏離預設格式"
  - "文檔接地（document grounding）策略替代模型記憶以提升回答準確性"
  - "結構化輸出設計是構建健壯 agent 系統的核心技術方案"
tags: [claude, agents, prompting, output-formatting, structured-output]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Onboarding Agent from Scratch. Part 3: A Shape the Model Can’t Break

Serge 在「從零開始打造 Onboarding Agent」系列的第三部分中，焦點聚集在將模型的輸出限制於特定且堅硬的結構形狀，使模型無法逃脫預設的輸出格式。該系列前一部分（第二階段）教導代理將回答接地在真實文檔而非依賴模型自身的知識庫；第三部分進一步解決輸出端的散漫性問題。通過強制實施格式約束，確保結構化回應而非游散的自然語言文本。此技術對於構建可靠、可預測的代理系統至關重要，特別是在需要機器可讀輸出或與下游系統整合時。

### 重點
- 輸出形狀約束（shape constraint）：設計堅硬的結構格式防止模型偏離預設格式
- 文檔接地（document grounding）策略替代模型記憶以提升回答準確性
- 結構化輸出設計是構建健壯 agent 系統的核心技術方案

**原文：** [medium-tag-claude](https://medium.com/@spodsky/onboarding-agent-from-scratch-part-3-a-shape-the-model-cant-break-c566d88153af?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Serge"
published_at: 2026-07-19T17:24:33+00:00
fetched_at: 2026-07-19T22:00:45.597865+00:00
content_hash: "82e0213f703ec2befc57c94fc7bc797b18cfbce47f73674e04d1a3f17041adbe"
lang: en
caption_quality: None
raw: true
topics: []
---

# Onboarding Agent from Scratch. Part 3: A Shape the Model Can’t Break

Stage 2 taught the agent to ground its answers in a real document instead of the model&#x2019;s own memory. It still handed back a blob of prose&#x2026; Continue reading on Medium »

</details>