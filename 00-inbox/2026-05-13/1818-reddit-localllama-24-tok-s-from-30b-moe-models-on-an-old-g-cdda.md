---
id: inbox_613ded27
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tcc7h5/24_toks_from_30b_moe_models_on_an_old_gtx_1080_8/"
author: "/u/mdda"
published_at: 2026-05-13T20:41:56+00:00
fetched_at: 2026-05-14T18:18:30.407820+00:00
content_hash: "cdda57db4f0f05131505892ae3cebb4c2ceb7048540f75cad23464d8ac8a0206"
lang: en
caption_quality: None
raw: true
topics: []
---

# 24+ tok/s from ~30B MoE models on an old GTX 1080 (8 GB VRAM, 128k context)

I got Qwen 3.6 35B-A3B and Gemma 4 26B-A4B running on a $200 secondhand machine (i7-6700 / GTX 1080 / 32 GB RAM) using llama.cpp (the TurboQuant/RotorQuant KV cache quantisation allows 128k context within the 8 GB VRAM). Results (Q4_K_M models, 128k context): Model tok/s Key flags Qwen 3.6 35B-A3B ~24 --n-cpu-moe 30, K=turbo4 V=turbo3 Gemma 4 26B-A4B (no MTP) ~20 --n-cpu-moe 20, K=V=turbo3, --flash-attn Gemma 4 26B-A4B + MTP (naive) ~21 embedding table silently on CPU Gemma 4 26B-A4B + MTP (fixed) ~24.5 --override-tensor-draft &quot;token_embd\.weight=CUDA0&quot; The trick is MoE offloading: llama.cpp can park the cold expert weights in system RAM, and stream over PCIe to the GPU, while keeping hot layers + KV cache on GPU. The system is fully PCIe bandwidth-limited (GPU sits at ~40-50% utilisation while PCIe 3.0 x16 is maxed out). Biggest finding: Gemma 4's MTP speculative decoding barely helps out of the box (~5% gain). Turns out llama.cpp unconditionally keeps the token embedding table on CPU. Normally that's fine (just a get_rows lookup), but Gemma 4's MTP assistant has a tied LM head - so every draft token does a full 262k×1024 matmul across PCIe. Forcing it onto GPU with --override-tensor-draft gives the real ~22% speedup and ~79% draft acceptance rate. Setup pain points (Fedora 42 + Pascal GPU): Pin akmod-nvidia to 580xx branch (Pascal is going legacy) Force gcc-14 for CUDA 12.9 (newer gcc rejected) Patch CUDA's math_functions.h for glibc 2.41 compatibility Used the AtomicBot-ai/atomic-llama-cpp-turboquant fork for both TurboQuant cache + Gemma MTP support Full blog post with all the grindy build details (every command, and the debugging deep-dive into the MTP embedding table issue) I'm also planning a YouTube video walkthrough soon - I'll update when that's live. Happy to answer questions about the setup. &#32; submitted by &#32; /u/mdda [link] &#32; [comments]