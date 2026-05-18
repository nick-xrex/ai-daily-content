---
id: inbox_23f616c2
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tfgxc8/testing_llamacpp_mtp_support_on_qwen36_rtx_5090/"
author: "/u/3VITAERC"
published_at: 2026-05-17T06:00:43+00:00
fetched_at: 2026-05-17T18:00:47.111162+00:00
content_hash: "9c44035b0c71823a9ba85501af600d6f1cb9da9ea2b15f0e7761bf9fbdc341b3"
lang: en
caption_quality: None
raw: true
topics: []
---

# Testing llama.cpp MTP support on Qwen3.6 - RTX 5090

Setup: - RTX 5090, 32 GB, Linux - Built llama.cpp from 4f13cb7 (the official ghcr.io/ggml-org/llama.cpp:server-cuda image hasn't picked up the merge yet as of writing — had to docker build from source with CUDA_DOCKER_ARCH=120) - Unsloth's Qwen3.6-27B-MTP-GGUF Q5_K_M and Qwen3.6-35B-A3B-MTP-GGUF UD-Q4_K_M - 128k context, flash-attn, q8_0 KV cache, temp 0.8, --parallel 1 (required for MTP) - Same GGUF for &quot;MTP on&quot; and &quot;MTP off&quot; — only the --spec-type draft-mtp --spec-draft-n-max 3 flag toggled. This isolates MTP from quant differences. - 2 prompts: &quot;short story about a cat&quot; (~400 tokens) and &quot;Flappy Bird clone as a single HTML file&quot; (~3000 tokens) - 3 seeds per config, averaged &#32; submitted by &#32; /u/3VITAERC [link] &#32; [comments]