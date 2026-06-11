---
id: inbox_f0ff30fa
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_f0ff30fa]]"
title: "DiffusionGemma"
url: https://simonwillison.net/2026/Jun/10/diffusiongemma/#atom-everything
source: simon-willison
published_at: 2026-06-10T20:00:54+00:00
fetched_at: 2026-06-11T00:25:10.282793+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 開源發布 DiffusionGemma-26B-A4B-it 模型（Apache 2 許可），源於 2025 年的實驗性 Gemini Diffusion 研究。該模型目前由 NVIDIA NIM 雲 API 免費託管。Simon Willison 實測生成 2,409 token 耗時 4.4 秒，達到 500+ tokens/秒的吞吐量。相比去年原型的 857 tokens/秒，性能提升顯著。DiffusionGemma 是 26B 參數的開源文本生成模型，為開發者提供了無成本訪問高性能推理的途徑。"
key_points:
  - "Google 開源 DiffusionGemma-26B-A4B-it（Apache 2 許可），基於 2025 年實驗性 Gemini Diffusion 研究升級"
  - "NVIDIA NIM 雲 API 免費託管，實測吞吐量：2,409 tokens / 4.4 秒 = 500+ tokens/秒（相比去年原型 857 tokens/秒）"
  - "26B 參數開源模型，提供全球開發者免費高性能推理訪問"
tags: [google, gemma, diffusion-model, open-source, nvidia]
topics: []
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## DiffusionGemma

Google 開源發布 DiffusionGemma-26B-A4B-it 模型（Apache 2 許可），源於 2025 年的實驗性 Gemini Diffusion 研究。該模型目前由 NVIDIA NIM 雲 API 免費託管。Simon Willison 實測生成 2,409 token 耗時 4.4 秒，達到 500+ tokens/秒的吞吐量。相比去年原型的 857 tokens/秒，性能提升顯著。DiffusionGemma 是 26B 參數的開源文本生成模型，為開發者提供了無成本訪問高性能推理的途徑。

### 重點
- Google 開源 DiffusionGemma-26B-A4B-it（Apache 2 許可），基於 2025 年實驗性 Gemini Diffusion 研究升級
- NVIDIA NIM 雲 API 免費託管，實測吞吐量：2,409 tokens / 4.4 秒 = 500+ tokens/秒（相比去年原型 857 tokens/秒）
- 26B 參數開源模型，提供全球開發者免費高性能推理訪問

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/10/diffusiongemma/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# DiffusionGemma

DiffusionGemma 
Last May Google briefly released an experimental Gemini Diffusion model. I tried the preview at the time and recorded it running at 857 tokens/second. It was an exciting model, but Google made no further announcements about it. 
 That research has returned in the best possible way: as a new open weight (Apache 2 licensed) Gemma model, google/diffusiongemma-26B-A4B-it . 
 NVIDIA are currently hosting the model for free on their NIM cloud API. I used that API to generate this pelican , which took 4.4s (according to time uv run generate.py ) to return 2,409 tokens - so at least 500 tokens/second. 
 

 Via Hacker News 

 Tags: google , ai , generative-ai , llms , nvidia , pelican-riding-a-bicycle , gemma , llm-release , llm-performance

</details>