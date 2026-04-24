---
id: inbox_8d85193e
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0246-simon-willison-qwen3-6-27b-flagship-level-coding-in-a-2-7e33]]"
title: "Qwen3.6-27B: Flagship-Level Coding in a 27B Dense Model"
url: https://simonwillison.net/2026/Apr/22/qwen36-27b/#atom-everything
source: simon-willison
published_at: 2026-04-22T16:45:23+00:00
fetched_at: 2026-04-24T02:56:27.845186+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen 發布 Qwen3.6-27B 密集模型，聲稱在編碼基準測試中超越前代旗艦 Qwen3.5-397B（397B 總規模 / 17B active MoE），但參數量僅為 1/15。模型完整版 55.6GB，GGUF Q4_K_M 量化版 16.8GB。Simon Willison 用 llama-server 本機測試，生成效能 ~25 tokens/s（讀取 54 tokens/s），生成 4,444 tokens 耗時 2 分 53 秒。產生高品質 SVG 輸出，展現開源小型模型逼近閉源旗艦的進展。Unsloth 量化版可在消費級硬體上本機運行，推理成本為零。"
key_points:
  - "Qwen3.6-27B 參數量為前代 1/15 卻編碼效能超越，密集架構優勢明顯"
  - "GGUF Q4_K_M 量化至 16.8GB，本機 25 tokens/s 生成速度，SVG 品質媲美商用模型"
  - "開源量化模型 + llama.cpp 方案：零推理成本、隱私優勢、適合本機開發迭代"
tags: [qwen, open-source-models, coding-models, quantization, llama-cpp]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6-27B: Flagship-Level Coding in a 27B Dense Model

Qwen 發布 Qwen3.6-27B 密集模型，聲稱在編碼基準測試中超越前代旗艦 Qwen3.5-397B（397B 總規模 / 17B active MoE），但參數量僅為 1/15。模型完整版 55.6GB，GGUF Q4_K_M 量化版 16.8GB。Simon Willison 用 llama-server 本機測試，生成效能 ~25 tokens/s（讀取 54 tokens/s），生成 4,444 tokens 耗時 2 分 53 秒。產生高品質 SVG 輸出，展現開源小型模型逼近閉源旗艦的進展。Unsloth 量化版可在消費級硬體上本機運行，推理成本為零。

### 重點
- Qwen3.6-27B 參數量為前代 1/15 卻編碼效能超越，密集架構優勢明顯
- GGUF Q4_K_M 量化至 16.8GB，本機 25 tokens/s 生成速度，SVG 品質媲美商用模型
- 開源量化模型 + llama.cpp 方案：零推理成本、隱私優勢、適合本機開發迭代

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/22/qwen36-27b/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://qwen.ai/blog?id=qwen3.6-27b">Qwen3.6-27B: Flagship-Level Coding in a 27B Dense Model</a></strong></p>
Big claims from Qwen about their latest open weight model:</p>
<blockquote>
<p>Qwen3.6-27B delivers flagship-level agentic coding performance, surpassing the previous-generation open-source flagship Qwen3.5-397B-A17B (397B total / 17B active MoE) across all major coding benchmarks.</p>
</blockquote>
<p>On Hugging Face <a href="https://huggingface.co/Qwen/Qwen3.5-397B-A17B/tree/main">Qwen3.5-397B-A17B</a> is 807GB, this new <a href="https://huggingface.co/Qwen/Qwen3.6-27B/tree/main">Qwen3.6-27B</a> is 55.6GB.</p>
<p>I tried it out with the 16.8GB Unsloth <a href="https://huggingface.co/unsloth/Qwen3.6-27B-GGUF">Qwen3.6-27B-GGUF:Q4_K_M</a> quantized version and <code>llama-server</code> using this recipe by <a href="https://news.ycombinator.com/item?id=47863217#47865140">benob on Hacker News</a>, after first installing <code>llama-server</code> using <code>brew install llama.cpp</code>:</p>
<pre><code>llama-server \
    -hf unsloth/Qwen3.6-27B-GGUF:Q4_K_M \
    --no-mmproj \
    --fit on \
    -np 1 \
    -c 65536 \
    --cache-ram 4096 -ctxcp 2 \
    --jinja \
    --temp 0.6 \
    --top-p 0.95 \
    --top-k 20 \
    --min-p 0.0 \
    --presence-penalty 0.0 \
    --repeat-penalty 1.0 \
    --reasoning on \
    --chat-template-kwargs '{"preserve_thinking": true}'
</code></pre>
<p>On first run that saved the ~17GB model to <code>~/.cache/huggingface/hub/models--unsloth--Qwen3.6-27B-GGUF</code>.</p>
<p>Here's <a href="https://gist.github.com/simonw/4d99d730c840df594096366db1d27281">the transcript</a> for "Generate an SVG of a pelican riding a bicycle". This is an <em>outstanding</em> result for a 16.8GB local model:</p>
<p><img alt="Bicycle has spokes, a chain and a correctly shaped frame. Handlebars are a bit detached. Pelican has wing on the handlebars, weirdly bent legs that touch the pedals and a good bill. Background details are pleasant - semi-transparent clouds, birds, grass, sun." src="https://static.simonwillison.net/static/2026/Qwen3.6-27B-GGUF-Q4_K_M.png" /></p>
<p>Performance numbers reported by <code>llama-server</code>:</p>
<ul>
<li>Reading: 20 tokens, 0.4s, 54.32 tokens/s</li>
<li>Generation: 4,444 tokens, 2min 53s, 25.57 tokens/s</li>
</ul>
<p>For good measure, here's <a href="https://gist.github.com/simonw/95735fe5e76e6fdf1753e6dcce360699">Generate an SVG of a NORTH VIRGINIA OPOSSUM ON AN E-SCOOTER</a> (run previously <a href="https://simonwillison.net/2026/Apr/7/glm-51/">with GLM-5.1</a>):</p>
<p><img alt="Digital illustration in a neon Tron-inspired style of a grey cat-like creature wearing cyan visor goggles riding a glowing cyan futuristic motorcycle through a dark cityscape at night, with its long tail trailing behind, silhouetted buildings with yellow-lit windows in the background, and a glowing magenta moon on the right." src="https://static.simonwillison.net/static/2026/qwen3.6-27b-possum.jpg" /></p>
<p>That one took 6,575 tokens, 4min 25s, 24.74 t/s.

    <p><small></small>Via <a href="https://news.ycombinator.com/item?id=47863217">Hacker News</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/local-llms">local-llms</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/qwen">qwen</a>, <a href="https://simonwillison.net/tags/pelican-riding-a-bicycle">pelican-riding-a-bicycle</a>, <a href="https://simonwillison.net/tags/llama-cpp">llama-cpp</a>, <a href="https://simonwillison.net/tags/llm-release">llm-release</a>, <a href="https://simonwillison.net/tags/ai-in-china">ai-in-china</a></p>

</details>