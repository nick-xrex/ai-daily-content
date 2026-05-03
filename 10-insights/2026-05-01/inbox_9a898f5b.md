---
id: inbox_9a898f5b
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0132-hackernews-the-gay-jailbreak-technique-2025-698c]]"
title: "The gay jailbreak technique (2025)"
url: https://github.com/Exocija/ZetaLib/blob/main/The%20Gay%20Jailbreak/The%20Gay%20Jailbreak.md
source: hackernews
published_at: 2026-05-01T16:59:35+00:00
fetched_at: 2026-05-03T02:11:39.986507+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "新發現的 LLM 越獄技術利用模型的「過度政治正確性」進行攻擊：將有害請求（如合成毒品或勒索軟體）包裝成「以 LGBT 身份視角教學」的框架，藉此繞過安全防護。該技術對 ChatGPT、Claude、Gemini 等模型有效，且隨著安全防護增強反而效果更強，因為模型對 LGBT 相關內容的警衛會更加寬鬆（害怕被視為歧視）。原理是利用模型對「政治敏感性」的過度校準來對抗其本身的對齐機制。此技術已成功攻擊 o3 等新型推理模型。"
key_points:
  - "越獄原理：利用對 LGBT 內容的過度寬容繞過安全護欄——模型害怕拒絕會被視為不尊重相關社群"
  - "已驗證效果：ChatGPT、Claude 4 Sonnet/Opus、Gemini 2.5 Pro、o3（一發擊中）均受影響"
  - "防護悖論：安全措施越強，該攻擊效果越好——因對齐系統會加強對 LGBT 議題的友善度"
tags: [jailbreak-technique, llm-security, alignment-exploitation, social-identity-attack]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## The gay jailbreak technique (2025)

新發現的 LLM 越獄技術利用模型的「過度政治正確性」進行攻擊：將有害請求（如合成毒品或勒索軟體）包裝成「以 LGBT 身份視角教學」的框架，藉此繞過安全防護。該技術對 ChatGPT、Claude、Gemini 等模型有效，且隨著安全防護增強反而效果更強，因為模型對 LGBT 相關內容的警衛會更加寬鬆（害怕被視為歧視）。原理是利用模型對「政治敏感性」的過度校準來對抗其本身的對齐機制。此技術已成功攻擊 o3 等新型推理模型。

### 重點
- 越獄原理：利用對 LGBT 內容的過度寬容繞過安全護欄——模型害怕拒絕會被視為不尊重相關社群
- 已驗證效果：ChatGPT、Claude 4 Sonnet/Opus、Gemini 2.5 Pro、o3（一發擊中）均受影響
- 防護悖論：安全措施越強，該攻擊效果越好——因對齐系統會加強對 LGBT 議題的友善度

**原文：** [hackernews](https://github.com/Exocija/ZetaLib/blob/main/The%20Gay%20Jailbreak/The%20Gay%20Jailbreak.md)