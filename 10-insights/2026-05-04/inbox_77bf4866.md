---
id: inbox_77bf4866
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_77bf4866]]"
title: "Granite 4.1 3B SVG Pelican Gallery"
url: https://simonwillison.net/2026/May/4/granite-41-3b-svg-pelican-gallery/#atom-everything
source: simon-willison
published_at: 2026-05-04T23:49:24+00:00
fetched_at: 2026-05-05T09:17:34.111351+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 測試了 IBM Granite 4.1 3B 模型的 21 個量化變體（由 Unsloth 發布，大小範圍 1.2GB 至 6.34GB）生成 SVG 圖像的能力。透過提示「生成騎自行車的鵜鶘 SVG」，發現不同模型大小間沒有明確的品質差異——所有輸出結果都相當糟糕。Granite 4.1 採用 Apache 2.0 開源授權，提供 3B、8B、30B 等多種規格，展示了量化部署的多樣性，但本實驗未能發現模型規模與生成質量的相關模式。"
key_points:
  - "Granite 4.1 3B 提供 21 個 GGUF 量化變體，規格 1.2GB–6.34GB，由 Unsloth 發行"
  - "不同量化規模的 SVG 生成質量無明顯差異；最小模型在自行車渲染上表現略優"
  - "Apache 2.0 開源授權支持多規格部署（3B、8B、30B），適合邊緣設備推理"
tags: [granite-4.1, open-source-llm, quantization, gguf]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Granite 4.1 3B SVG Pelican Gallery

Simon Willison 測試了 IBM Granite 4.1 3B 模型的 21 個量化變體（由 Unsloth 發布，大小範圍 1.2GB 至 6.34GB）生成 SVG 圖像的能力。透過提示「生成騎自行車的鵜鶘 SVG」，發現不同模型大小間沒有明確的品質差異——所有輸出結果都相當糟糕。Granite 4.1 採用 Apache 2.0 開源授權，提供 3B、8B、30B 等多種規格，展示了量化部署的多樣性，但本實驗未能發現模型規模與生成質量的相關模式。

### 重點
- Granite 4.1 3B 提供 21 個 GGUF 量化變體，規格 1.2GB–6.34GB，由 Unsloth 發行
- 不同量化規模的 SVG 生成質量無明顯差異；最小模型在自行車渲染上表現略優
- Apache 2.0 開源授權支持多規格部署（3B、8B、30B），適合邊緣設備推理

**原文：** [simon-willison](https://simonwillison.net/2026/May/4/granite-41-3b-svg-pelican-gallery/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Granite 4.1 3B SVG Pelican Gallery

<p><strong><a href="https://simonw.github.io/granite-4.1-3b-gguf-pelicans/">Granite 4.1 3B SVG Pelican Gallery</a></strong></p>
IBM released their <a href="https://research.ibm.com/blog/granite-4-1-ai-foundation-models">Granite 4.1 family</a> of LLMs a few days ago. They're Apache 2.0 licensed and come in 3B, 8B and 30B sizes.</p>
<p><a href="https://huggingface.co/blog/ibm-granite/granite-4-1">Granite 4.1 LLMs: How They’re Built</a> by Granite team member Yousaf Shah describes the training process in detail.</p>
<p>Unsloth released the <a href="https://huggingface.co/unsloth/granite-4.1-3b-GGUF">unsloth/granite-4.1-3b-GGUF</a> collection of GGUF encoded quantized variants of the 3B model - 21 different model files ranging in size from 1.2GB to 6.34GB.</p>
<p>All 21 of those Unsloth files add up to 51.3GB, which inspired me to finally try an experiment I've been wanting to run for ages: prompting "Generate an SVG of a pelican riding a bicycle" against different sized quantized variants of the same model to see what the results would look like.</p>
<p>Honestly, <a href="https://simonw.github.io/granite-4.1-3b-gguf-pelicans/">the results</a> are less interesting than I expected. There's no distinguishable pattern relating quality to size - they're all pretty terrible!</p>
<p><img alt="Six different SVG images from models ranging in size from 1.67GB to 1.2GB. They are almost all an abstract collection of shapes - weirdly the smallest model had the best version of a bicycle, while the largest one had something that looked a tiny bit like a pelican." src="https://static.simonwillison.net/static/2026/granite-3B-pelicans.jpg" /></p>
<p>I'll likely try this again in the future with a model that's better at drawing pelicans.


    <p>Tags: <a href="https://simonwillison.net/tags/ibm">ibm</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/pelican-riding-a-bicycle">pelican-riding-a-bicycle</a>, <a href="https://simonwillison.net/tags/llm-release">llm-release</a></p>

</details>