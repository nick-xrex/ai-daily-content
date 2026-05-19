---
id: inbox_a49dd323
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0201-reddit-localllama-mlx-engine-comparison-and-omlx-is-the-to-3652]]"
title: "MLX engine comparison... and oMLX is the top choice."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgszn9/mlx_engine_comparison_and_omlx_is_the_top_choice/
source: reddit-localllama
published_at: 2026-05-18T17:07:47+00:00
fetched_at: 2026-05-19T02:09:43.220908+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "部落客對 MLX 推理引擎進行評測對比，在 M5 Max 64GB 上運行 Qwen3.6-35B-A3B-4bit 時，oMLX 表現最優。文章提及另一篇博客涉及 MTPLX 與其他引擎對標（但使用 Qwen 3.6 27B，非完全對標），為 Mac 和 ARM 設備用戶提供推理框架選型參考。"
key_points:
  - "oMLX 在 M5 Max 64GB + Qwen3.6-35B-A3B-4bit 上表現最優"
  - "M5 Max 64GB 是 Apple Silicon 最高配置，提供充足 VRAM 用於大模型推理"
  - "涉及 MTPLX 與其他 MLX 引擎對比，但樣本不完全對標"
tags: [mlx-engine, apple-silicon, inference-engine-comparison, m5-max]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## MLX engine comparison... and oMLX is the top choice.

部落客對 MLX 推理引擎進行評測對比，在 M5 Max 64GB 上運行 Qwen3.6-35B-A3B-4bit 時，oMLX 表現最優。文章提及另一篇博客涉及 MTPLX 與其他引擎對標（但使用 Qwen 3.6 27B，非完全對標），為 Mac 和 ARM 設備用戶提供推理框架選型參考。

### 重點
- oMLX 在 M5 Max 64GB + Qwen3.6-35B-A3B-4bit 上表現最優
- M5 Max 64GB 是 Apple Silicon 最高配置，提供充足 VRAM 用於大模型推理
- 涉及 MTPLX 與其他 MLX 引擎對比，但樣本不完全對標

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgszn9/mlx_engine_comparison_and_omlx_is_the_top_choice/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Just stumbled on this blog. A very interesting read if you are picking inference engine. M5 Max 64GB with mlx-community/Qwen3.6-35B-A3B-4bit. The MTPLX in the article use 3.6 27B so it's not apple to apple. https://preview.redd.it/huxhasc4gx1h1.png?width=990&amp;format=png&amp;auto=webp&amp;s=88cf7828b18eb8dea7a4c92c041f2b5c795f1824 https://preview.redd.it/fhevre6agx1h1.png?width=990&amp;format=png&amp;auto=webp&amp;s=7bbc9aecbb5684aeeedf712e5a1017d0aab68fa7 https://www.largitdata.com/blog_detail/20260511 &#32; submitted by &#32; /u/Beamsters [link] &#32; [comments]

</details>