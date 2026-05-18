---
id: inbox_39949f4a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tflngz/dual_gpu_llamacpp_speedup/"
author: "/u/Legitimate-Dog5690"
published_at: 2026-05-17T10:24:36+00:00
fetched_at: 2026-05-17T18:00:47.118855+00:00
content_hash: "5bb53ff287fc0e1a35970fd54539b2b6aa1406dfc6236f2734df9c328a884b0a"
lang: en
caption_quality: None
raw: true
topics: []
---

# Dual GPU llama.cpp speedup

Llama.cpp has an issue with &quot;--split-mode tensor&quot;, you'll get great results but it only supports non-quantized KV caches, for this very reason a lot of people decide to go with a healthy sized KV cache and ignore tensor parallelism. &nbsp; I've had a stab at fixing the issue here - https://github.com/RedToasty/llama.cpp_qts - it's branched from mainline as of today, with minimal changes. &nbsp; I'm personally running a 3060 12gb + 4070 Super 12gb, for a combined 24gb. &nbsp; Here's my results with Q8_0/Q8_0 and &quot;-sm tensor&quot;: &nbsp; llama-bench.exe -m Qwen3.6-27B-Q4_K_M.gguf -sm tensor -fa 1 -ctk q8_0 -ctv q8_0 -p 128 -n 32 -b 128 -ub 128 &nbsp; Model Size Params Backend NGL Batch UBatch Type K Type V SM FA Test Tokens/s Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 tensor 1 pp128 544.82 ± 6.01 Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 tensor 1 tg32 30.05 ± 0.38 Here's without tensor splitting: &nbsp; llama-bench.exe -m Qwen3.6-27B-Q4_K_M.gguf -fa 1 -ctk q8_0 -ctv q8_0 -p 128 -n 32 -b 128 -ub 128 &nbsp; Model Size Params Backend NGL Batch UBatch Type K Type V FA Test Tokens/s Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 1 pp128 582.60 ± 28.57 Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 1 tg32 21.22 ± 0.52 Just over a 40% speed increase, with no loss of quality . This branch also supports the latest mtp changes , I've personally been using: &nbsp; --spec-type draft-mtp --spec-draft-p-min 0.75 --spec-draft-n-max 2 &nbsp; In personal use my tokens per second have gone from around 25tps to around 40tps, in short &quot;write a story&quot; style contexts. I think it's due to limited vram, but I've personally had more joy with ngram-mod when using agentic coding and longer contexts. &nbsp; I'd love to hear any feedback from anyone running dual 5060 ti or similar. Also anything dual Vulkan would be interesting, I'm looking for issues. &nbsp; TLDR : If you run dual GPUs, grab/build this fork, add &quot;-sm tensor&quot; to your current command line and see if it goes 50% faster! Note : I've just spotted there's an issue with MoE models and &quot;-sm tensor&quot;, not related to this fix. Test against dense models for the moment, Qwen3.6 27b/9b etc. Tensor split seems very unloved, given it's a free 50% boost! If this proves popular I'll look at fixing MoE and pulling Turboquants in. &#32; submitted by &#32; /u/Legitimate-Dog5690 [link] &#32; [comments]