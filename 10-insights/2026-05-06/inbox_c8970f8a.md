---
id: inbox_c8970f8a
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-reddit-localllama-most-people-seem-obsessed-with-token-gen-b5ad]]"
title: "Most people seem obsessed with token generation speed, but isn’t prefill the real bottleneck? Am I missing something?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/
source: reddit-localllama
published_at: 2026-05-06T20:02:22+00:00
fetched_at: 2026-05-07T01:30:59.381024+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者指出社群過度關注解碼速度（tokens/s），卻忽視提示詞處理（prefill）才是真正瓶頸。以 Qwen 27B Q6 為例，生成速度 15 t/s 已足用，但 prefill 只有 300 t/s，大量時間浪費在處理提示上。特別在 agentic work 場景（模型需先吃掉大段代碼）問題更突出。質疑當前優化方向為何不改善 prefill 效率。"
key_points:
  - "Qwen 27B Q6 實測：生成 15 t/s 足夠，prefill 300 t/s 卻造成長等待（實際用戶感知瓶頸）"
  - "agentic work 場景最受影響：需先吸入大量上下文（如代碼），prefill 延遲被放大"
  - "社群優化誤區：過度投資解碼速度改進（如 MTP），忽視 prefill 才是真實瓶頸"
tags: [prefill-bottleneck, local-llm-inference, agentic-workflows, qwen-27b]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Most people seem obsessed with token generation speed, but isn’t prefill the real bottleneck? Am I missing something?

作者指出社群過度關注解碼速度（tokens/s），卻忽視提示詞處理（prefill）才是真正瓶頸。以 Qwen 27B Q6 為例，生成速度 15 t/s 已足用，但 prefill 只有 300 t/s，大量時間浪費在處理提示上。特別在 agentic work 場景（模型需先吃掉大段代碼）問題更突出。質疑當前優化方向為何不改善 prefill 效率。

### 重點
- Qwen 27B Q6 實測：生成 15 t/s 足夠，prefill 300 t/s 卻造成長等待（實際用戶感知瓶頸）
- agentic work 場景最受影響：需先吸入大量上下文（如代碼），prefill 延遲被放大
- 社群優化誤區：過度投資解碼速度改進（如 MTP），忽視 prefill 才是真實瓶頸

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I read this sub every day and I keep seeing benchmarks and discussions focused almost entirely on tokens/s generation speed. Prompt processing speed barely gets mentioned.</p> <p>From my own experience running a bunch of different models on different GPUs for all kinds of tasks, the prefill stage is usually the part that actually feels slow. Once generation starts, even “only” 15 t/s is perfectly usable for me. The wait for the model to eat the prompt is what eats most of the time.</p> <p>Seeing all the hype around MTP lately kind of reinforces that feeling. If generation speed improvements don’t really move the needle on total wall-clock time for typical use cases, why is everyone laser-focused on it?</p> <p>For example, with Qwen 27B Q6 I’m getting ~15 t/s generation with my current setup (which feels fine no matter what I’m doing) but only ~300 t/s on prefill. I spend way more time staring at the processing than I do waiting for the actual reply to finish. Even with prompt caching.</p> <p>Am I misunderstanding something about how most people use these models? Curious what others are seeing.</p> <p>Edit: I forgot to mention that I mostly do agentic work, where the model has to ingest part of the codebase before it can actually do anything useful. For normal chat this obviously isn’t an issue, context stays small and you just need enough t/s to keep up with your reading speed.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/wbulot"> /u/wbulot </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/">[comments]</a></span>

</details>