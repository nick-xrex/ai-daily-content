---
id: inbox_67de88a2
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_67de88a2]]"
title: "GPT-5.5 Computer Use Agent Harness"
url: https://cobusgreyling.medium.com/gpt-5-5-computer-use-agent-harness-4c8a9a48c9ea?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-05T06:01:01+00:00
fetched_at: 2026-05-05T09:19:46.602209+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 2026 年 4 月發布 GPT-5.5，引入原生電腦使用能力（Computer Using Agent, CUA）。性能指標：OSWorld-Verified 達 78.7%（略領先 Claude 78.0%），Terminal-Bench 2.0 達 82.7%（相比前版 GPT-5.4 的 75% 進步 7.7%）。技術升級：原生多模態處理文本、圖像、音頻、視頻於單次推理無視覺 token 轉譯；1M token 超長上下文保留完整對話歷史；高達 1024M pixel 截圖無重縮放精準識別細微 UI；`reasoning.effort` 參數 5 級調整成本/延遲/精準度權衡。核心洞察：「模型提供願景，harness 提供代理」——產品本質是完整系統架構（環境配置、動作執行、截圖管線、錯誤恢復、安全邊界），而非模型本身。"
key_points:
  - "GPT-5.5（Apr 2026）性能：OSWorld 78.7% vs Claude 78.0%；Terminal-Bench 82.7% 相比前版 +7.7%"
  - "技術突破：原生多模態（文本+圖像+音頻+視頻單次），1M token 超長上下文，1024M 像素截圖保留微細 UI 元素細節"
  - "系統勝於模型：CUA harness 架構（環境配置、動作執行管線、錯誤恢復、安全邊界）決定產品成敗，不只 LLM 能力"
tags: [gpt-5-5, computer-use, agent-architecture, multimodality, openai-release]
topics: [foundation_models.gpt]
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## GPT-5.5 Computer Use Agent Harness

OpenAI 2026 年 4 月發布 GPT-5.5，引入原生電腦使用能力（Computer Using Agent, CUA）。性能指標：OSWorld-Verified 達 78.7%（略領先 Claude 78.0%），Terminal-Bench 2.0 達 82.7%（相比前版 GPT-5.4 的 75% 進步 7.7%）。技術升級：原生多模態處理文本、圖像、音頻、視頻於單次推理無視覺 token 轉譯；1M token 超長上下文保留完整對話歷史；高達 1024M pixel 截圖無重縮放精準識別細微 UI；`reasoning.effort` 參數 5 級調整成本/延遲/精準度權衡。核心洞察：「模型提供願景，harness 提供代理」——產品本質是完整系統架構（環境配置、動作執行、截圖管線、錯誤恢復、安全邊界），而非模型本身。

### 重點
- GPT-5.5（Apr 2026）性能：OSWorld 78.7% vs Claude 78.0%；Terminal-Bench 82.7% 相比前版 +7.7%
- 技術突破：原生多模態（文本+圖像+音頻+視頻單次），1M token 超長上下文，1024M 像素截圖保留微細 UI 元素細節
- 系統勝於模型：CUA harness 架構（環境配置、動作執行管線、錯誤恢復、安全邊界）決定產品成敗，不只 LLM 能力

**原文：** [medium-tag-llm](https://cobusgreyling.medium.com/gpt-5-5-computer-use-agent-harness-4c8a9a48c9ea?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Cobus Greyling"
published_at: 2026-05-05T06:01:01+00:00
fetched_at: 2026-05-05T08:19:18.667072+00:00
content_hash: "ef656567a941d65ca2b0c269d21b6302334c1316d890507ec6bb4059fd2056c2"
lang: en
caption_quality: None
raw: true
topics: []
---

# GPT-5.5 Computer Use Agent Harness

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://cobusgreyling.medium.com/gpt-5-5-computer-use-agent-harness-4c8a9a48c9ea?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/2086/1*AffjhaJJr6pU86xgrrgOsg.png" width="2086" /></a></p><p class="medium-feed-snippet">OpenAI released GPT-5.5 April 2026 &amp; among its headline capabilities is native computer use&#x2026;</p><p class="medium-feed-link"><a href="https://cobusgreyling.medium.com/gpt-5-5-computer-use-agent-harness-4c8a9a48c9ea?source=rss------large_language_models-5">Continue reading on Medium »</a></p></div>

</details>