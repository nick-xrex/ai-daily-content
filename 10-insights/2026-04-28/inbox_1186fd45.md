---
id: inbox_1186fd45
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0248-medium-tag-ai-how-to-use-claude-code-for-free-no-gpu-n-235f]]"
title: "How to Use Claude Code for Free (No GPU, No Subscription, No Limits)"
url: https://mediawrites.medium.com/how-to-use-claude-code-for-free-no-gpu-no-subscription-no-limits-21d1d6b18295?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-04-28T02:32:30+00:00
fetched_at: 2026-04-28T02:59:27.823771+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章教學如何透過本地代理伺服器搭配免費 AI 模型供應商（NVIDIA NIM、DeepSeek、OpenRouter）免費執行 Claude Code。該方案建立 Anthropic API 相容層，將 Claude Code 請求轉發至免費後端，避免每月 $20–$100 的訂閱費用。用戶可為 Opus、Sonnet、Haiku 等不同模型層級分別路由至不同免費提供商，實現成本最佳化。文章提供完整逐步設置指南：安裝 uv 和 Python 3.14、複製 GitHub 倉庫、配置 API key 與環境變數、啟動本地代理伺服器。最終使用者透過設定 `ANTHROPIC_BASE_URL=\"http://localhost:8082\"` 即可讓 Claude Code 改用本地後端，完全無費用地構建生產級專案（如 tic-tac-toe 遊戲範例）。"
key_points:
  - "本地 Anthropic API 相容代理 + 免費模型供應商（NVIDIA NIM、DeepSeek、OpenRouter）= 零成本 Claude Code"
  - "支援模型層級差異化路由：MODEL=\"nvidia_nim/z-ai/glm4.7\"、MODEL_SONNET=\"open_router/gemma-2\"、MODEL_HAIKU=\"deepseek/deepseek-reasoner\""
  - "環境變數配置 `ANTHROPIC_AUTH_TOKEN=\"freecc\"` + `ANTHROPIC_BASE_URL=\"http://localhost:8082\"` + `uv run uvicorn server:app --port 8082` 完成部署"
tags: [claude-code, local-proxy, free-alternative, api-routing, cost-optimization]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Use Claude Code for Free (No GPU, No Subscription, No Limits)

文章教學如何透過本地代理伺服器搭配免費 AI 模型供應商（NVIDIA NIM、DeepSeek、OpenRouter）免費執行 Claude Code。該方案建立 Anthropic API 相容層，將 Claude Code 請求轉發至免費後端，避免每月 $20–$100 的訂閱費用。用戶可為 Opus、Sonnet、Haiku 等不同模型層級分別路由至不同免費提供商，實現成本最佳化。文章提供完整逐步設置指南：安裝 uv 和 Python 3.14、複製 GitHub 倉庫、配置 API key 與環境變數、啟動本地代理伺服器。最終使用者透過設定 `ANTHROPIC_BASE_URL="http://localhost:8082"` 即可讓 Claude Code 改用本地後端，完全無費用地構建生產級專案（如 tic-tac-toe 遊戲範例）。

### 重點
- 本地 Anthropic API 相容代理 + 免費模型供應商（NVIDIA NIM、DeepSeek、OpenRouter）= 零成本 Claude Code
- 支援模型層級差異化路由：MODEL="nvidia_nim/z-ai/glm4.7"、MODEL_SONNET="open_router/gemma-2"、MODEL_HAIKU="deepseek/deepseek-reasoner"
- 環境變數配置 `ANTHROPIC_AUTH_TOKEN="freecc"` + `ANTHROPIC_BASE_URL="http://localhost:8082"` + `uv run uvicorn server:app --port 8082` 完成部署

**原文：** [medium-tag-ai](https://mediawrites.medium.com/how-to-use-claude-code-for-free-no-gpu-no-subscription-no-limits-21d1d6b18295?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://mediawrites.medium.com/how-to-use-claude-code-for-free-no-gpu-no-subscription-no-limits-21d1d6b18295?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/1280/1*PFTFLAAE4a0uD9eea4A7SQ.jpeg" width="1280" /></a></p><p class="medium-feed-snippet">Most developers are stuck between two bad options:</p><p class="medium-feed-link"><a href="https://mediawrites.medium.com/how-to-use-claude-code-for-free-no-gpu-no-subscription-no-limits-21d1d6b18295?source=rss------artificial_intelligence-5">Continue reading on Medium »</a></p></div>

</details>