---
id: inbox_b8bcc8c7
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_b8bcc8c7]]"
title: "Simpler self hosted alt to Open WebUI"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tciwwt/simpler_self_hosted_alt_to_open_webui/
source: reddit-localllama
published_at: 2026-05-14T01:05:45+00:00
fetched_at: 2026-05-18T03:44:23.040025+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "介紹 overtchat，一個專為本地 LLM 設計的簡化聊天介面。作者在自己的 4x 3090 rig 上運行 Qwen 3.6 27B，發現 Open WebUI 雖改進但仍過於複雜，決定構建 overtchat 專注核心聊天體驗。單 docker-compose 部署，內建 searxng web search 和 kokoro TTS（無需 API keys），PWA 行動優化，MIT 開源無遙測。目標提供「開箱即用」的自託管 ChatGPT 替代方案，讓非技術用戶輕鬆採納本地 AI 工作流。"
key_points:
  - "單檔案部署（docker-compose），針對非技術用戶簡化設置流程"
  - "內建 searxng web search 與 kokoro TTS，無須額外 API keys"
  - "PWA 行動優化，MIT 開源無遙測，補足 Open WebUI 過度工程化"
tags: [overtchat, local-llm, self-hosted, ui, pwa]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Simpler self hosted alt to Open WebUI

介紹 overtchat，一個專為本地 LLM 設計的簡化聊天介面。作者在自己的 4x 3090 rig 上運行 Qwen 3.6 27B，發現 Open WebUI 雖改進但仍過於複雜，決定構建 overtchat 專注核心聊天體驗。單 docker-compose 部署，內建 searxng web search 和 kokoro TTS（無需 API keys），PWA 行動優化，MIT 開源無遙測。目標提供「開箱即用」的自託管 ChatGPT 替代方案，讓非技術用戶輕鬆採納本地 AI 工作流。

### 重點
- 單檔案部署（docker-compose），針對非技術用戶簡化設置流程
- 內建 searxng web search 與 kokoro TTS，無須額外 API keys
- PWA 行動優化，MIT 開源無遙測，補足 Open WebUI 過度工程化

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tciwwt/simpler_self_hosted_alt_to_open_webui/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Simpler self hosted alt to Open WebUI

Got Qwen3.6 27B running on my newly assembled 4x 3090 rig (s/o 3090-club) and I'm trying to get the people in my house to adopt the local workflow. Open WebUI has improved a lot in the recent updates, but I still found it pretty rough for non-technical people. It often feels more like a dev tool than a self-hosted ChatGPT-style app that &quot;just works&quot;. I built overtchat to focus mainly on getting the core chat experience right: a polished ui, simple setup and fewer moving parts. The goal is not to compete on agentic workflow with LibreChat/LobeChat/OWUI but to provide a cleaner self-hosted interface for local models. Ships with its own tried &amp; tested searxng config for web search, kokoro tts (no api keys needed). Single docker compose file. MIT licensed of course, no telemetry. Optimized for mobile as PWA. Github . Also being upfront - I write code for a living and have been actively reviewing/debugging/changing things, but I did use quite a lot of AI lol. I promise it's not slop tho 😿 . Feedback is welcome! &#32; submitted by &#32; /u/anitamaxwynnn69 [link] &#32; [comments]

</details>