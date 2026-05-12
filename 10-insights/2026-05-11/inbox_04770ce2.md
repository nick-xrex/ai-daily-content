---
id: inbox_04770ce2
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-simon-willison-learning-on-the-shop-floor-339e]]"
title: "Learning on the Shop floor"
url: https://simonwillison.net/2026/May/11/learning-on-the-shop-floor/#atom-everything
source: simon-willison
published_at: 2026-05-11T15:46:36+00:00
fetched_at: 2026-05-11T18:04:20.657939+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 分享 Shopify 內部代碼代理工具 River 的設計哲學。River 強制所有對話在公開 Slack 頻道進行（拒絕私聊），使得整個開發過程對公司內部完全透明和可搜尋。這一設計創造了「Lehrwerkstatt」（教學工作坊）環境，員工可以通過觀看他人的工作來學習，而無需正式課程—稱之為「滲透性學習」（osmosis learning）。文章將此與 Midjourney 早期依賴公開 Discord 頻道的成功進行類比，都通過公開工作和互相觀摩來加速集體學習，降低學習摩擦。"
key_points:
  - "Shopify River：強制公開頻道的內部 AI 代碼助手，拒絕私聊模式"
  - "Lehrwerkstatt 學習設計：通過可見工作實現無課程滲透性學習"
  - "跨案例模式（River + Midjourney）：公開工作 > 正式培訓課程，降低學習摩擦"
tags: [coding-agents, organizational-learning, public-transparency, shopify-river, lehrwerkstatt]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Learning on the Shop floor

Simon Willison 分享 Shopify 內部代碼代理工具 River 的設計哲學。River 強制所有對話在公開 Slack 頻道進行（拒絕私聊），使得整個開發過程對公司內部完全透明和可搜尋。這一設計創造了「Lehrwerkstatt」（教學工作坊）環境，員工可以通過觀看他人的工作來學習，而無需正式課程—稱之為「滲透性學習」（osmosis learning）。文章將此與 Midjourney 早期依賴公開 Discord 頻道的成功進行類比，都通過公開工作和互相觀摩來加速集體學習，降低學習摩擦。

### 重點
- Shopify River：強制公開頻道的內部 AI 代碼助手，拒絕私聊模式
- Lehrwerkstatt 學習設計：通過可見工作實現無課程滲透性學習
- 跨案例模式（River + Midjourney）：公開工作 > 正式培訓課程，降低學習摩擦

**原文：** [simon-willison](https://simonwillison.net/2026/May/11/learning-on-the-shop-floor/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Learning on the Shop floor 
Tobias Lütke describes Shopify's internal coding agent tool, River, which operates entirely in public on their Slack: 
 
 River does not respond to direct messages. She politely declines and suggests to create a public channel for you and her to start working in. I myself work with river in #tobi_river channel and many followed this pattern. Every conversation is therefore searchable. Anyone at Shopify can jump in. In my own channel, there are over 100 people who, react to threads, add color and add context, pick up the torch, help with the reviews, remind me how rusty I am, and importantly, learn from watching. [...] 
 As so often with German, there is a word for the kind of environment: Lehrwerkstatt . Literally: A teaching workshop . The whole shop floor is the classroom. You learn by being near the work. Being a constant learner is one of the core values of the firm. 
 Shopify wants to be a Lehrwerkstatt at scale and River has now gotten us closer to this ideal than ever. It’s osmosis learning , because it does not require a curriculum, a training plan, or a manager. It just requires everyone's work to be visible to the maximum extent possible. Everyone learns from each other. 
 
 I'm reminded of how Midjourney spent its first few years with the primary interface being public Discord channels, forcing users to share their prompts and learn from each other's experiments. I continue to believe that the early success of Midjourney was tied to this mechanism, helping to compensate for how weird and finicky text-to-image prompting is.

 Tags: ai , slack , generative-ai , llms , midjourney , coding-agents , tobias-lutke

</details>