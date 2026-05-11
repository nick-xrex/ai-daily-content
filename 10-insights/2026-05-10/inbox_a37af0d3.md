---
id: inbox_a37af0d3
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_a37af0d3]]"
title: "Claude just hallucinated again and changed the whole workflow of my app. Do not run them autonomously 24/7."
url: https://www.reddit.com/r/ClaudeAI/comments/1t9h8ug/claude_just_hallucinated_again_and_changed_the/
source: reddit-claudeai
published_at: 2026-05-10T19:59:58+00:00
fetched_at: 2026-05-11T02:28:26.303271+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者警示 Claude 存在生產環境風險：模型出現幻覺，自動修改應用工作流程，差點在使用者未知的情況下造成資料庫大規模注入錯誤。儘管訂閱 Claude Max 方案，模型仍未達生產級可靠性，不應無人監督運行。使用者批評市場上對 OpenClaw 等自主 AI 代理的炒作通常來自非生產場景（業餘愛好、概念驗證、點擊誘餌），而實際生產部署面臨幻覺、無意識修改等失控風險。強調 AI 代理需持續人工監督。"
key_points:
  - "Claude 自動修改應用工作流程未通知使用者，差點造成資料庫數據損壞（bad data injection）"
  - "Claude Max 訂閱仍無法保證幻覺問題解決，生產環境自主代理部署遠未成熟"
  - "市場對自主 AI 代理的炒作多源於非生產用例，生產環境必須持續人工監督"
tags: [hallucination-risk, production-safety, autonomous-agents, data-integrity]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Claude just hallucinated again and changed the whole workflow of my app. Do not run them autonomously 24/7.

使用者警示 Claude 存在生產環境風險：模型出現幻覺，自動修改應用工作流程，差點在使用者未知的情況下造成資料庫大規模注入錯誤。儘管訂閱 Claude Max 方案，模型仍未達生產級可靠性，不應無人監督運行。使用者批評市場上對 OpenClaw 等自主 AI 代理的炒作通常來自非生產場景（業餘愛好、概念驗證、點擊誘餌），而實際生產部署面臨幻覺、無意識修改等失控風險。強調 AI 代理需持續人工監督。

### 重點
- Claude 自動修改應用工作流程未通知使用者，差點造成資料庫數據損壞（bad data injection）
- Claude Max 訂閱仍無法保證幻覺問題解決，生產環境自主代理部署遠未成熟
- 市場對自主 AI 代理的炒作多源於非生產用例，生產環境必須持續人工監督

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9h8ug/claude_just_hallucinated_again_and_changed_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude just hallucinated again and changed the whole workflow of my app. Do not run them autonomously 24/7.

With Claude Max plan, you'd think you're sorted but you're not. It just changed a major workflow in my app and was going to make a change that would have costed my a huge bad data injection in the DB. It's far from being an autonomous AI agent. It still hallucinates a lot and this is the reason I've not onboarded on the hype train of OpenClaw and other autonomous AI agents. Every weird person on my feed who's just hyping up OpenClaw is either using it for hobby projects, exploring it, or just building hype for click baits. These technologies are far from perfect and can cost you your business if left autonomous or unchecked. Be wise. Oversee your AI agents continously. &#32; submitted by &#32; /u/heysankalp [link] &#32; [comments]

</details>