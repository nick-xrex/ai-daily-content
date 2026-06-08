---
id: inbox_4e55dc13
date: 2026-06-07
source_ref: "[[00-inbox/2026-06-07/1800-medium-tag-llm-what-if-were-building-ai-systems-the-wro-6fe4]]"
title: "What If We’re Building AI Systems The Wrong Way?"
url: https://medium.com/@WillNewmarch/what-if-were-building-ai-systems-the-wrong-way-ccb123cd8a8b?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-07T07:36:00+00:00
fetched_at: 2026-06-07T18:07:13.011256+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在構建聊天助手時發現了一個核心問題：傳統軟體工程採用確定性思維，試圖預測 LLM 行為並列舉所有邊界情況，但 LLM 本質上是非確定性的。作者透過實驗發現，簡潔的身份導向提示（如「你是反饋分析師」）勝過複雜的規則清單。受生物學啟發，他提出應該構建具有明確用途的專門元件，讓整體行為從各元件互動中自然浮現，而非依賴中央控制。該方法建議不用單一全能助手，而改用專門化管道（檢索、主題分析、情感分析等），每個元件明確其身份但不需預知所有場景。"
key_points:
  - "LLM 系統應拋棄確定性設計思維，改採最小身份導向的提示策略，避免無窮的邊界情況列舉"
  - "專門化元件模式：用多個小型、有明確目的的組件取代單一複雜助手，類似生物器官的功能模式"
  - "整體行為從元件互動自然浮現，而非預先規定，解決了傳統規則型系統試圖覆蓋所有場景的矛盾"
tags: [llm-architecture, prompt-design, non-determinism, system-design]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## What If We’re Building AI Systems The Wrong Way?

開發者在構建聊天助手時發現了一個核心問題：傳統軟體工程採用確定性思維，試圖預測 LLM 行為並列舉所有邊界情況，但 LLM 本質上是非確定性的。作者透過實驗發現，簡潔的身份導向提示（如「你是反饋分析師」）勝過複雜的規則清單。受生物學啟發，他提出應該構建具有明確用途的專門元件，讓整體行為從各元件互動中自然浮現，而非依賴中央控制。該方法建議不用單一全能助手，而改用專門化管道（檢索、主題分析、情感分析等），每個元件明確其身份但不需預知所有場景。

### 重點
- LLM 系統應拋棄確定性設計思維，改採最小身份導向的提示策略，避免無窮的邊界情況列舉
- 專門化元件模式：用多個小型、有明確目的的組件取代單一複雜助手，類似生物器官的功能模式
- 整體行為從元件互動自然浮現，而非預先規定，解決了傳統規則型系統試圖覆蓋所有場景的矛盾

**原文：** [medium-tag-llm](https://medium.com/@WillNewmarch/what-if-were-building-ai-systems-the-wrong-way-ccb123cd8a8b?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Over the last couple of years I&#x2019;ve spent a lot of time building chat assistants into web applications, and I&#x2019;m starting to wonder &#x2014; should&#x2026; Continue reading on Medium »

</details>