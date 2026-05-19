---
id: inbox_34650013
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tg4mw0/benchmarking_vllm_vs_sglang_vs_llamacpp_on_a/"
author: "/u/Temporary-Sector-947"
published_at: 2026-05-17T22:57:54+00:00
fetched_at: 2026-05-18T18:51:02.666825+00:00
content_hash: "eafe8fe74a93483591ab5b1622cadd95e2a69e127a3e56aa0d5ca6f37ca70adc"
lang: en
caption_quality: None
raw: true
topics: []
---

# Benchmarking vLLM vs SGLang vs llama.cpp on a mixed Blackwell/Ada cluster

I have been running some benchmarks on a heterogeneous 7-GPU cluster to see how different inference engines handle long context prefill using pipeline parallelism. My setup consists of a mix of Blackwell and Ada cards: one RTX PRO 6000 96GB, one PRO 5000 48GB, two 5090 32GB, and three modded 4090 48GB. All tests were done using 4-bit weights, specifically NVFP4 for vLLM and SGLang, and MXFP4 for llama.cpp. The main takeaway is that vLLM significantly outperforms the others on mixed multi-GPU setups for long context prefill. Llama.cpp struggles heavily with pipeline parallelism under these conditions, falling behind by a factor of 4 to 6. This appears to be due to how the execution graph is handled across multiple devices, with CPU-side embeddings causing graph splits and pipeline bubbles. SGLang performs wonderfully on a pure Blackwell setup, almost matching vLLM. However, it instantly crashes if you introduce an Ada card into the pipeline because it currently lacks a software fallback for FP4 weights, strictly requiring Compute Capability 10.0. vLLM handles this seamlessly by emulating FP4 on the older cards. Another interesting finding is how well vLLM handles uneven GPU splits. By manually tweaking the layer distribution using the VLLM_PP_LAYER_PARTITION environment variable, I was able to balance the compute load between the fast Blackwells and the slower 4090s doing FP4 emulation. This eliminated pipeline bottlenecks and resulted in massive speedups even on a 397B model. Here is the summary of the benchmark results. Model and Context GPU Setup Engine TTFT Prefill Speed Qwen3.6-35B-A3B (184k tokens) 2 GPUs (6000 + 5090) vLLM 10.2s 18060 t/s Qwen3.6-35B-A3B (184k tokens) 2 GPUs (6000 + 5090) llama.cpp 24.9s 7405 t/s MiniMax-M2.7 (82k tokens) 6 GPUs (Mixed) vLLM 13.2s 6212 t/s MiniMax-M2.7 (82k tokens) 6 GPUs (Mixed) llama.cpp 77.0s 1065 t/s MiniMax-M2.7 (82k tokens) 6 GPUs (Mixed) SGLang Crashed N/A Qwen3.5-122B-A10B (75k tokens) 4 GPUs (Pure Blackwell) vLLM 5.0s 15084 t/s Qwen3.5-122B-A10B (75k tokens) 4 GPUs (Pure Blackwell) SGLang 5.3s 14177 t/s Qwen3.5-122B-A10B (75k tokens) 4 GPUs (Pure Blackwell) llama.cpp 20.6s 3662 t/s Qwen3.5-397B-A17B (75k tokens) 7 GPUs (Uneven PP split) vLLM 9.8s 7683 t/s Qwen3.5-397B-A17B (75k tokens) 7 GPUs (Uneven PP split) llama.cpp 57.2s 1319 t/s If you are building a mixed cluster or relying heavily on pipeline parallelism for large models, vLLM chunked prefill and manual layer partitioning are incredibly useful. I hope this data is helpful for anyone planning their hardware topologies or struggling with prefill times on multi-GPU setups. I'm not a native English speaker so I used LLM to translate. Edit: typo &#32; submitted by &#32; /u/Temporary-Sector-947 [link] &#32; [comments]