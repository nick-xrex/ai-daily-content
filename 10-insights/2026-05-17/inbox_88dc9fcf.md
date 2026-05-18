---
id: inbox_88dc9fcf
date: 2026-05-17
source_ref: "[[00-inbox/2026-05-17/0308-reddit-localllama-moving-from-composer-2-kimi-2-6-to-qwen3-a143]]"
title: "Moving from Composer 2/Kimi 2.6 to Qwen3.6:35b-a3b"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfxah9/moving_from_composer_2kimi_26_to_qwen3635ba3b/
source: reddit-localllama
published_at: 2026-05-17T18:18:04+00:00
fetched_at: 2026-05-18T03:15:00.027675+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者分享用 Qwen 3.6:35b-a3b 模型進行日常生產開發的體驗。該開發者負責 50–70 萬行企業軟件維護，每週 60 小時，經由 OpenRouter 使用該模型成本約 $0.08/1M tokens（含緩存折扣）。Qwen 3.6 在代碼理解、指令遵循能力上超越 Composer 2、Kimi 2.6、DeepSeek 4 Pro/Flash，支持圖像輸入與截圖上下文，可作為 Cursor 替代方案。唯一缺陷為無雲代理功能與 Composer 2 的高吞吐量自動模式。"
key_points:
  - "Qwen 3.6:35b-a3b 可滿足生產級代碼開發（50–70 萬行、每週 60 小時），性能優於 Composer 2/Kimi 2.6/DeepSeek 4 Pro/Flash，OpenRouter 成本 ~$0.08/1M tokens"
  - "支持圖像輸入與截圖，可作 Cursor 部分替代；缺少雲代理功能與 Composer 2 高吞吐量自動模式"
  - "開發者評價：代碼理解、指令遵循能力「意外出色」，推翻對開源 LLM 生產可行性的既有認知"
tags: [qwen-3.6, code-generation, openrouter, cursor-alternative, cost-efficient-inference]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Moving from Composer 2/Kimi 2.6 to Qwen3.6:35b-a3b

開發者分享用 Qwen 3.6:35b-a3b 模型進行日常生產開發的體驗。該開發者負責 50–70 萬行企業軟件維護，每週 60 小時，經由 OpenRouter 使用該模型成本約 $0.08/1M tokens（含緩存折扣）。Qwen 3.6 在代碼理解、指令遵循能力上超越 Composer 2、Kimi 2.6、DeepSeek 4 Pro/Flash，支持圖像輸入與截圖上下文，可作為 Cursor 替代方案。唯一缺陷為無雲代理功能與 Composer 2 的高吞吐量自動模式。

### 重點
- Qwen 3.6:35b-a3b 可滿足生產級代碼開發（50–70 萬行、每週 60 小時），性能優於 Composer 2/Kimi 2.6/DeepSeek 4 Pro/Flash，OpenRouter 成本 ~$0.08/1M tokens
- 支持圖像輸入與截圖，可作 Cursor 部分替代；缺少雲代理功能與 Composer 2 高吞吐量自動模式
- 開發者評價：代碼理解、指令遵循能力「意外出色」，推翻對開源 LLM 生產可行性的既有認知

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfxah9/moving_from_composer_2kimi_26_to_qwen3635ba3b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I can't believe it, but I'm able to do my daily software development work on this model. We have a 500-700k line of code enterprise software suite that I'm devving for 60 hours a week. I've been hunting for a cursor replacement for a little bit now, and was previously toying with Kimi 2.6 and deepseek 4 pro and flash. There are some minor issues I've had with each of those, and Q3.6:35b-a3b actually feels the best for me, anecdotally, of all of them. I can't articulate how insanely excited and shocked I am. I've been hearing the hype here for a bit and I have to say it lived up to it. I could run this model locally, but I don't have the hardware for it, so for now I'm using it on openrouter at ~$0.08/1M tokens averaged out for our usage (what we're actually getting billed after caching and whatever is figured out). That's so insanely cheap for a model that can actually understand what I need it to with this workload / use case, and can accept image input / screenshots. If you haven't tried this model, I implore you, take a look at it. It's shockingly good. The only thing that I miss from Cursor at this point is the cloud agents functionality, and the high throughput they have on auto/Composer 2. &#32; submitted by &#32; /u/NotARedditUser3 [link] &#32; [comments]

</details>