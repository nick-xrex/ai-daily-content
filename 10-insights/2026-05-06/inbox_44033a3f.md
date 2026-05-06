---
id: inbox_44033a3f
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-medium-tag-claude-the-claude-waiting-room-when-inference-l-fdf9]]"
title: "The Claude Waiting Room — When Inference Limits Taught Me Patience"
url: https://medium.com/@bharathadapa/the-claude-waiting-room-when-inference-limits-taught-me-patience-c6d6daec5a83?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-06T12:35:03+00:00
fetched_at: 2026-05-06T12:58:06.130869+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "記錄在使用 Claude Sonnet 4 Pro（$20/月）時遇到的速率限制與輸出長度限制。作者詳述日限制在午夜後耗盡的困境、單次回應達到最大長度時需反覆輸入「Continue」繼續生成（最多七次）。應對策略是按任務性質分類使用：高價模型處理需完整代碼上下文的任務，低成本模型處理獨立任務，並維持「預熱替補模型」應對 Claude 額度耗盡。"
key_points:
  - "Claude Sonnet 4 Pro 存在日限制（具體值未披露）與單回應最大長度限制"
  - "實務工作流優化：複雜任務用 Claude，簡單任務用替補模型，減少開銷"
  - "輸出中斷問題需多次 Continue 才完成，是設計流程時的隱藏成本"
tags: [claude-rate-limits, cost-optimization, workflow-design]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## The Claude Waiting Room — When Inference Limits Taught Me Patience

記錄在使用 Claude Sonnet 4 Pro（$20/月）時遇到的速率限制與輸出長度限制。作者詳述日限制在午夜後耗盡的困境、單次回應達到最大長度時需反覆輸入「Continue」繼續生成（最多七次）。應對策略是按任務性質分類使用：高價模型處理需完整代碼上下文的任務，低成本模型處理獨立任務，並維持「預熱替補模型」應對 Claude 額度耗盡。

### 重點
- Claude Sonnet 4 Pro 存在日限制（具體值未披露）與單回應最大長度限制
- 實務工作流優化：複雜任務用 Claude，簡單任務用替補模型，減少開銷
- 輸出中斷問題需多次 Continue 才完成，是設計流程時的隱藏成本

**原文：** [medium-tag-claude](https://medium.com/@bharathadapa/the-claude-waiting-room-when-inference-limits-taught-me-patience-c6d6daec5a83?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@bharathadapa/the-claude-waiting-room-when-inference-limits-taught-me-patience-c6d6daec5a83?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/875/1*Lh0_XSNhMPtU398zYB9oQA.png" width="875" /></a></p><p class="medium-feed-snippet">Part 2 of 5 in From Side Gig to Production, a series on AI-assisted coding. Better code, longer waits, and the two-tool fallback ritual&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@bharathadapa/the-claude-waiting-room-when-inference-limits-taught-me-patience-c6d6daec5a83?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>