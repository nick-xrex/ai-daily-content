---
id: inbox_5a5cf9c8
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_5a5cf9c8]]"
title: "Gemini 3.1 Flash TTS"
url: https://simonwillison.net/2026/Apr/15/gemini-31-flash-tts/#atom-everything
source: (resumed)
published_at: 2026-04-15T17:13:14+00:00
fetched_at: 2026-04-21T02:39:16.462751+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 發佈 Gemini 3.1 Flash TTS 文本轉語音模型，可透過 `gemini-3.1-flash-tts-preview` 模型 ID 經由標準 Gemini API 調用。該模型支持詳細的 prompt 工程，允許使用者定義說話者身份、口音、語調、說話風格、動態與節奏等特徵，實現高度可控的語音生成。示例展示同一段腳本可生成倫敦 Brixton 口音、Newcastle 口音、Devon 口音等多種區域方言的音頻檔案，證明模型對細微語音差異的掌控能力。模型僅輸出音頻檔案而不支持文本輸出。Simon Willison 並基於 Gemini 3.1 Pro 開發了交互式測試 UI，支持多說話者對話模式，便於使用者實驗不同配置。"
key_points:
  - "Gemini 3.1 Flash TTS 模型 ID 為 `gemini-3.1-flash-tts-preview`，透過標準 Gemini API 調用，支持極其詳細的 prompt 工程（聲音特徵、口音、風格、速度、動態等可控）"
  - "模型展示區域口音精確度：同一腳本可精確生成倫敦、Newcastle、Devon 等不同英倫口音的音頻輸出"
  - "支持多說話者對話模式：可定義不同說話者名稱與聲音風格，模型根據腳本自動分配音頻"
tags: [gemini-tts, text-to-speech, prompt-engineering, google-ai, audio-generation]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemini 3.1 Flash TTS

Google 發佈 Gemini 3.1 Flash TTS 文本轉語音模型，可透過 `gemini-3.1-flash-tts-preview` 模型 ID 經由標準 Gemini API 調用。該模型支持詳細的 prompt 工程，允許使用者定義說話者身份、口音、語調、說話風格、動態與節奏等特徵，實現高度可控的語音生成。示例展示同一段腳本可生成倫敦 Brixton 口音、Newcastle 口音、Devon 口音等多種區域方言的音頻檔案，證明模型對細微語音差異的掌控能力。模型僅輸出音頻檔案而不支持文本輸出。Simon Willison 並基於 Gemini 3.1 Pro 開發了交互式測試 UI，支持多說話者對話模式，便於使用者實驗不同配置。

### 重點
- Gemini 3.1 Flash TTS 模型 ID 為 `gemini-3.1-flash-tts-preview`，透過標準 Gemini API 調用，支持極其詳細的 prompt 工程（聲音特徵、口音、風格、速度、動態等可控）
- 模型展示區域口音精確度：同一腳本可精確生成倫敦、Newcastle、Devon 等不同英倫口音的音頻輸出
- 支持多說話者對話模式：可定義不同說話者名稱與聲音風格，模型根據腳本自動分配音頻

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/15/gemini-31-flash-tts/#atom-everything)