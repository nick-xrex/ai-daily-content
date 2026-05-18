---
id: inbox_d358942a
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-local-llm-autocomplete-agentic-coding-on-40e5]]"
title: "Local LLM autocomplete + agentic coding on a single 16GB GPU + 64GB RAM"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tb3zxp/local_llm_autocomplete_agentic_coding_on_a_single/
source: reddit-localllama
published_at: 2026-05-12T14:53:30+00:00
fetched_at: 2026-05-12T18:12:25.042339+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 RTX 5090（支持 RAM offloading）上同時運行 autocomplete 和 agentic coding，實現可用的本地編碼工具鏈。Autocomplete 使用 Qwen2.5-Coder-7B Q6_K_L (~8GB VRAM，建議速度即時)，agentic 使用 Qwen3.6-35B-A3B UD-Q8_K_XL（Q8 品質可用，Q4 會迷路；3.8B active params 保持速度快，共用剩餘 8GB VRAM）。系統需求最少 64GB RAM，作者 96GB 用量達 56GB（浮動）。推理速度 pp4096 ~2093 tok/s、tg128 ~35.29 tok/s。作者發現 Qwen2.5 仍最佳 infill 模型，Gemma4 E4B 和 Qwen3.5 有奇怪建議。"
key_points:
  - "Qwen2.5-Coder-7B 是最佳 infill 選擇，Gemma4 E4B 和 Qwen3.5 產生異常 completion"
  - "MoE 模型 Q8 可用但 Q4 不可用（質量大幅下降），Q6_K 是質量-大小折中點"
  - "單塊 H100 等級 GPU + 64GB+ RAM 可支撐兩個並行推理服務，但硬件門檻高"
tags: [local-inference, qwen-models, agentic-coding, gpu-optimization, moe]
topics: []
importance: 3
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Local LLM autocomplete + agentic coding on a single 16GB GPU + 64GB RAM

用戶在 RTX 5090（支持 RAM offloading）上同時運行 autocomplete 和 agentic coding，實現可用的本地編碼工具鏈。Autocomplete 使用 Qwen2.5-Coder-7B Q6_K_L (~8GB VRAM，建議速度即時)，agentic 使用 Qwen3.6-35B-A3B UD-Q8_K_XL（Q8 品質可用，Q4 會迷路；3.8B active params 保持速度快，共用剩餘 8GB VRAM）。系統需求最少 64GB RAM，作者 96GB 用量達 56GB（浮動）。推理速度 pp4096 ~2093 tok/s、tg128 ~35.29 tok/s。作者發現 Qwen2.5 仍最佳 infill 模型，Gemma4 E4B 和 Qwen3.5 有奇怪建議。

### 重點
- Qwen2.5-Coder-7B 是最佳 infill 選擇，Gemma4 E4B 和 Qwen3.5 產生異常 completion
- MoE 模型 Q8 可用但 Q4 不可用（質量大幅下降），Q6_K 是質量-大小折中點
- 單塊 H100 等級 GPU + 64GB+ RAM 可支撐兩個並行推理服務，但硬件門檻高

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tb3zxp/local_llm_autocomplete_agentic_coding_on_a_single/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Today I set up a full coding toolbox on a single RTX 5080 (with RAM offloading) that's actually viable. Autocomplete : bartowski/Qwen2.5-Coder-7B-Instruct-GGUF:Q6_K_L Agentic : unsloth/Qwen3.6-35B-A3B-GGUF:UD-Q8_K_XL Why these models: Qwen2.5 is still the best model for infill imo. I tried Gemma4 E4B and Qwen3.5 9B/4B and both produce weird suggestions. This autocomplete model takes ~8GB VRAM using the command below. The speed of suggestions is basically instant. Qwen3.6 35B-A3B is actually good at agentic coding at Q8 if you give it a good prompt. At Q4 it's not usable tbh and gets lost a lot, but at Q8 it can figure stuff out and actually finish its work correctly. If you don't have a lot of RAM for MoE experts, try Q6_K, but lower quants have noticable quality issues. You probably need 64GB total RAM minimum. I have 96 but with both models running and a bunch of random stuff open (browser, IDE, Teams) I'm at 56GB used. Because it has 3B active params, it's still fast and fits into the remaining 8GB VRAM. Commands: bash llama-server -hf bartowski/Qwen2.5-Coder-7B-Instruct-GGUF:Q6_K_L \ -ngl 99 --no-mmap --ctx-size 0 -ctk q8_0 -ctv q8_0 \ -np 1 --temp 0.5 --top-p 0.95 --top-k 20 --min-p 0.0 --port 8081 Note: I actually have no idea which hyperparameters to use for Qwen2.5, maybe someone will enlighten me and I'll edit the post. bash llama-server -hf unsloth/Qwen3.6-35B-A3B-GGUF:UD-Q8_K_XL \ --no-mmap --no-mmproj -fitt 0 -ngl 99 --cpu-moe \ -b 2048 -ub 2048 --jinja \ --temp 0.6 --top-p 0.95 --top-k 20 --min-p 0.01 llama.cpp autofits the model and I get ~145k context with this command. You can use -ctv q8_0 -ctk q8_0 if you want more context. 35B-A3B speed with this setup: pp4096 | 2093.93 ± 22.64 tg128 | 35.29 ± 0.48 &#32; submitted by &#32; /u/grumd [link] &#32; [comments]

</details>