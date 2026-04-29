---
id: inbox_9f370c42
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0658-hackernews-vibevoice-open-source-frontier-voice-ai-5bcc]]"
title: "VibeVoice: Open-source frontier voice AI"
url: https://github.com/microsoft/VibeVoice
source: hackernews
published_at: 2026-04-28T11:56:04+00:00
fetched_at: 2026-04-29T07:36:26.607565+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft 開源 VibeVoice 語音 AI 框架，包含 ASR 和 TTS 模型系列。核心創新是採用 7.5 Hz 超低幀率的連續語音 tokenizer，結合 LLM 和 next-token diffusion 架構以實現高效長序列處理。VibeVoice-ASR（7B）支援 60 分鐘單pass 長音訊，涵蓋 50+ 語言、自定義熱詞、結構化轉錄（發言人/時間戳/內容），已於 2026-03-06 整合至 Hugging Face Transformers；VibeVoice-TTS（1.5B）支援 90 分鐘長form、4 位發言人；VibeVoice-Realtime（0.5B）提供實時 TTS，新增 9 語言多國籍語音。並支援 vLLM 推論加速部署。"
key_points:
  - "VibeVoice-ASR 7B：60 分鐘單pass 處理（無 context 丟失）、50+ 語言、自定義熱詞、已入 Hugging Face Transformers 官方支援"
  - "連續語音 tokenizer @ 7.5 Hz + next-token diffusion 框架：相對於傳統短片段 ASR 大幅降低計算量並保持音質"
  - "模型族完整：ASR (7B)、TTS (1.5B)、Realtime (0.5B)；vLLM 推論支援快速部署"
tags: [voice-ai, speech-recognition, text-to-speech, open-source, microsoft]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## VibeVoice: Open-source frontier voice AI

Microsoft 開源 VibeVoice 語音 AI 框架，包含 ASR 和 TTS 模型系列。核心創新是採用 7.5 Hz 超低幀率的連續語音 tokenizer，結合 LLM 和 next-token diffusion 架構以實現高效長序列處理。VibeVoice-ASR（7B）支援 60 分鐘單pass 長音訊，涵蓋 50+ 語言、自定義熱詞、結構化轉錄（發言人/時間戳/內容），已於 2026-03-06 整合至 Hugging Face Transformers；VibeVoice-TTS（1.5B）支援 90 分鐘長form、4 位發言人；VibeVoice-Realtime（0.5B）提供實時 TTS，新增 9 語言多國籍語音。並支援 vLLM 推論加速部署。

### 重點
- VibeVoice-ASR 7B：60 分鐘單pass 處理（無 context 丟失）、50+ 語言、自定義熱詞、已入 Hugging Face Transformers 官方支援
- 連續語音 tokenizer @ 7.5 Hz + next-token diffusion 框架：相對於傳統短片段 ASR 大幅降低計算量並保持音質
- 模型族完整：ASR (7B)、TTS (1.5B)、Realtime (0.5B)；vLLM 推論支援快速部署

**原文：** [hackernews](https://github.com/microsoft/VibeVoice)