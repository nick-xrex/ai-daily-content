---
id: inbox_a19d4018
date: 2026-07-17
source_ref: "[[00-inbox/.../inbox_a19d4018]]"
title: "Token Maxxing Is Dead. Long Live Token Minning."
url: https://medium.com/@zwolf25/token-maxxing-is-dead-long-live-token-minning-707fffbf2b95?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-17T19:24:17+00:00
fetched_at: 2026-07-18T01:53:39.611553+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "大語言模型社群目前的主流做法是擴展上文長度（Context Window），試圖透過更多的輸入 token 來提升模型效能，這被稱為「Token Maxxing」。本文提出反駁，主張「Token Minning」才是正確的優化方向，核心觀點是訊號密度優於上文容量。作者引入物理學原理，闡述連貫性（Coherence）受基礎物理規律制約，因此不會無限隨著上文窗口擴大而改善。文章主張優化 LLM 時，應聚焦於提升輸入訊號的品質與密度，而非盲目堆積 token 數量。這個觀點直接挑戰當前業界追求超大上文窗口的流行趨勢。雖然完整論證邏輯未見於預覽，但核心洞察對 LLM 設計策略與成本效益分析具有重要參考意義。"
key_points:
  - "訊號密度優於上文容量：「token minning」（最適化訊號品質）應取代「token maxxing」（盲目擴展窗口）"
  - "連貫性（coherence）受物理規律制約，無法無限隨上文窗口擴大而線性改善"
  - "對業界主流超大上文窗口設計趨勢的直接質疑與替代框架"
tags: [context-window, signal-density, token-efficiency, llm-optimization, coherence]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Token Maxxing Is Dead. Long Live Token Minning.

大語言模型社群目前的主流做法是擴展上文長度（Context Window），試圖透過更多的輸入 token 來提升模型效能，這被稱為「Token Maxxing」。本文提出反駁，主張「Token Minning」才是正確的優化方向，核心觀點是訊號密度優於上文容量。作者引入物理學原理，闡述連貫性（Coherence）受基礎物理規律制約，因此不會無限隨著上文窗口擴大而改善。文章主張優化 LLM 時，應聚焦於提升輸入訊號的品質與密度，而非盲目堆積 token 數量。這個觀點直接挑戰當前業界追求超大上文窗口的流行趨勢。雖然完整論證邏輯未見於預覽，但核心洞察對 LLM 設計策略與成本效益分析具有重要參考意義。

### 重點
- 訊號密度優於上文容量：「token minning」（最適化訊號品質）應取代「token maxxing」（盲目擴展窗口）
- 連貫性（coherence）受物理規律制約，無法無限隨上文窗口擴大而線性改善
- 對業界主流超大上文窗口設計趨勢的直接質疑與替代框架

**原文：** [medium-tag-llm](https://medium.com/@zwolf25/token-maxxing-is-dead-long-live-token-minning-707fffbf2b95?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Zac"
published_at: 2026-07-17T19:24:17+00:00
fetched_at: 2026-07-17T22:58:06.650361+00:00
content_hash: "c7f6129c160d3a88a9186bd3d9150dd72c66bb98d8c8f3de4480c6889bc761cf"
lang: en
caption_quality: None
raw: true
topics: []
---

# Token Maxxing Is Dead. Long Live Token Minning.

Signal density beats context volume. Here&#x2019;s why coherence has physics. Continue reading on Medium »

</details>