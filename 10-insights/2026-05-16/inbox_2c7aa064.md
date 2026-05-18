---
id: inbox_2c7aa064
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_2c7aa064]]"
title: "Local Qwen 3.6 vs frontier models on a coding primitive: single-file HTML canvas driving animation - results and GIFs"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf3p6c/local_qwen_36_vs_frontier_models_on_a_coding/
source: reddit-localllama
published_at: 2026-05-16T19:51:05+00:00
fetched_at: 2026-05-18T04:08:06.626109+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 使用者在 Ryzen 5 5600 + RX 5700 XT 上測試本地 Qwen3.6 與 frontier 模型在 HTML canvas 單文件動畫任務上的表現。測試任務：逼真側視駕駛場景（分層視差、車輪動畫、柔和光照）。Frontier 模型（Claude Sonnet 4.6 Thinking、Gemini 3.1 Pro、GPT 5.4、Kimi k2.6）vs 本地量化模型。驚人發現：本地 Qwen3.6-27B Q4_K_M（2.7 tok/s）在視覺動畫原始任務上的表現超過多數 frontier 輸出，排名第二；Kimi k2.6 Thinking 排第一。暗示在特定視覺編碼任務上，本地中等尺寸模型可匹敵雲端旗艦。"
key_points:
  - "本地 Qwen3.6-27B Q4 量化版在複雜 canvas 動畫上表現超預期，僅次於 Kimi k2.6"
  - "Frontier 模型（Claude Sonnet 4.6、GPT 5.4）在該類視覺編碼任務上並無絕對優勢"
  - "硬體配置：Ryzen 5 5600、24GB DDR4、RX 5700 XT 8GB，local 推理速度 2.7 tok/s（Qwen27B）vs 遠端的測速未記錄"
tags: [qwen3.6, local-llm, canvas-animation, model-comparison]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Local Qwen 3.6 vs frontier models on a coding primitive: single-file HTML canvas driving animation - results and GIFs

Reddit 使用者在 Ryzen 5 5600 + RX 5700 XT 上測試本地 Qwen3.6 與 frontier 模型在 HTML canvas 單文件動畫任務上的表現。測試任務：逼真側視駕駛場景（分層視差、車輪動畫、柔和光照）。Frontier 模型（Claude Sonnet 4.6 Thinking、Gemini 3.1 Pro、GPT 5.4、Kimi k2.6）vs 本地量化模型。驚人發現：本地 Qwen3.6-27B Q4_K_M（2.7 tok/s）在視覺動畫原始任務上的表現超過多數 frontier 輸出，排名第二；Kimi k2.6 Thinking 排第一。暗示在特定視覺編碼任務上，本地中等尺寸模型可匹敵雲端旗艦。

### 重點
- 本地 Qwen3.6-27B Q4 量化版在複雜 canvas 動畫上表現超預期，僅次於 Kimi k2.6
- Frontier 模型（Claude Sonnet 4.6、GPT 5.4）在該類視覺編碼任務上並無絕對優勢
- 硬體配置：Ryzen 5 5600、24GB DDR4、RX 5700 XT 8GB，local 推理速度 2.7 tok/s（Qwen27B）vs 遠端的測速未記錄

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf3p6c/local_qwen_36_vs_frontier_models_on_a_coding/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Local Qwen 3.6 vs frontier models on a coding primitive: single-file HTML canvas driving animation - results and GIFs

Saw this post comparing Qwen 3.6 variants on coding primitives, so I wanted to see how local quants stack up against frontier models on a similar dense, single-file coding task. I ran the exact same prompt across local and web-based models accessed through my Perplexity subscription. The prompt &quot;Write a single HTML file with a full-page canvas and no libraries. Simulate a realistic side-view of a moving car as the main subject. Keep the car visible in the foreground while the background landscape scrolls continuously to create the feeling that the car is driving forward. Use layered scenery for depth: nearby ground, roadside elements, trees, poles, and distant hills or mountains should move at different speeds for a natural parallax effect. Animate the wheels spinning realistically and add subtle body motion so the car feels connected to the road. Let the environment pass smoothly behind it, with repeating but varied scenery that makes the movement feel believable. Use cinematic lighting and a cohesive sky, such as sunset, dusk, or daylight, to enhance atmosphere. The overall motion should feel calm, immersive, and realistic, with a seamless looping animation.&quot; Models tested Frontier (web-based via Perplexity, tok/s not measured): Claude sonnet 4.6 Thinking — used internet for reasoning Gemini 3.1 Pro Thinking GPT 5.4 Thinking Kimi k2.6 Thinking Local (Ryzen 5 5600, 24 GB DDR4-3200, RX 5700 XT 8GB): Qwen3.5 9B Q4_K_M — ~50 tok/s Qwen3.6-27B (Claude-opus-reasoning-distilled) Q4_K_M — 2.65 tok/s Qwen3.6-27B Q4_K_M — 2.70 tok/s Qwen3.6-35B A3B Q4_K_M — 12.13 tok/s Gemma-4-31b-it — 1.91 tok/s Qwen3.5 4B Q8 — 60 tok/s — used internet for reasoning Qwen3.5 4B Q4_K_M — 80 tok/s — used internet for reasoning What I looked for Realistic side-view driving animation: layered parallax scenery, spinning wheels, subtle chassis motion, cohesive sky and lighting, and seamless looping — all vanilla JS/canvas, zero libraries. Subjective ranking for this specific task Kimi k2.6 Thinking — cleanest overall visual result Qwen3.6-27B Q4_K_M (local) — stronger than I expected; good parallax and road feel Qwen3.6-27B Claude-opus-reasoning-distilled — close third The local 27B quant delivered more natural motion and layering than some frontier outputs for this specific visual primitive. I was expecting frontier models to do much better — am I missing something? Outputs I only changed the HTML &lt;title&gt; tags to track which model generated which file. I’ll share all the output files and probably a few screenshots of the running animations so you can judge the visual quality yourself. If anyone wants to run the exact same prompt on their setup — especially other MoE cuts or distills — feel free to share your results. &#32; submitted by &#32; /u/Fragrant-Remove-9031 [link] &#32; [comments]

</details>