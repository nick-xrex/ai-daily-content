---
id: inbox_dd5225d0
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tb17bp/mtpggml_cuda_enable_unified_memory1_llamacpp/"
author: "/u/mossy_troll_84"
published_at: 2026-05-12T13:10:26+00:00
fetched_at: 2026-05-12T18:00:40.933795+00:00
content_hash: "71ad3e1f2a146e6a3b6f67cfd2fd4f5c9a9fc588d0db3d76b16f772b9baa1731"
lang: en
caption_quality: None
raw: true
topics: []
---

# MTP+GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 - llama.cpp

I was wondering what will be the difference in results with flag: GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 vs MTP+GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 Results are quite interesting 49tok/sec without MTP vs 64 tok/sec with MTP. PC: RTX5090+128GB DDR5 5600 CL36+Ryzen 9 9950X3D Model: Qwen3.6-27B-Q8_0.gguf (Unsloth with MTP) Command: CUDA_VISIBLE_DEVICES=0 GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 /home/marcin/llama-server \ -m /home/marcin/Pobrane/Qwen3.6-27B-Q8_0.gguf \ --threads 16 \ -c 262144 -fa on -np 1 \ --spec-type mtp --spec-draft-n-max 3 \ --webui-mcp-proxy \ --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' \ --host 0.0.0.0 \ --port 8090 \ --jinja &#32; submitted by &#32; /u/mossy_troll_84 [link] &#32; [comments]