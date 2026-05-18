---
id: inbox_d358942a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tb3zxp/local_llm_autocomplete_agentic_coding_on_a_single/"
author: "/u/grumd"
published_at: 2026-05-12T14:53:30+00:00
fetched_at: 2026-05-12T18:00:40.898132+00:00
content_hash: "40e54480b3b1bcaacda7ee12fe8ea39508c10181e8b384250c43b89981432475"
lang: en
caption_quality: None
raw: true
topics: []
---

# Local LLM autocomplete + agentic coding on a single 16GB GPU + 64GB RAM

Today I set up a full coding toolbox on a single RTX 5080 (with RAM offloading) that's actually viable. Autocomplete : bartowski/Qwen2.5-Coder-7B-Instruct-GGUF:Q6_K_L Agentic : unsloth/Qwen3.6-35B-A3B-GGUF:UD-Q8_K_XL Why these models: Qwen2.5 is still the best model for infill imo. I tried Gemma4 E4B and Qwen3.5 9B/4B and both produce weird suggestions. This autocomplete model takes ~8GB VRAM using the command below. The speed of suggestions is basically instant. Qwen3.6 35B-A3B is actually good at agentic coding at Q8 if you give it a good prompt. At Q4 it's not usable tbh and gets lost a lot, but at Q8 it can figure stuff out and actually finish its work correctly. If you don't have a lot of RAM for MoE experts, try Q6_K, but lower quants have noticable quality issues. You probably need 64GB total RAM minimum. I have 96 but with both models running and a bunch of random stuff open (browser, IDE, Teams) I'm at 56GB used. Because it has 3B active params, it's still fast and fits into the remaining 8GB VRAM. Commands: bash llama-server -hf bartowski/Qwen2.5-Coder-7B-Instruct-GGUF:Q6_K_L \ -ngl 99 --no-mmap --ctx-size 0 -ctk q8_0 -ctv q8_0 \ -np 1 --temp 0.5 --top-p 0.95 --top-k 20 --min-p 0.0 --port 8081 Note: I actually have no idea which hyperparameters to use for Qwen2.5, maybe someone will enlighten me and I'll edit the post. bash llama-server -hf unsloth/Qwen3.6-35B-A3B-GGUF:UD-Q8_K_XL \ --no-mmap --no-mmproj -fitt 0 -ngl 99 --cpu-moe \ -b 2048 -ub 2048 --jinja \ --temp 0.6 --top-p 0.95 --top-k 20 --min-p 0.01 llama.cpp autofits the model and I get ~145k context with this command. You can use -ctv q8_0 -ctk q8_0 if you want more context. 35B-A3B speed with this setup: pp4096 | 2093.93 ± 22.64 tg128 | 35.29 ± 0.48 &#32; submitted by &#32; /u/grumd [link] &#32; [comments]