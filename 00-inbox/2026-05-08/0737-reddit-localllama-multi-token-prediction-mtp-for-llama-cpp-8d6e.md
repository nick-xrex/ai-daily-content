---
id: inbox_b6252903
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t6se6r/multitoken_prediction_mtp_for_llamacpp_gemma_4/"
author: "/u/gladkos"
published_at: 2026-05-08T00:27:44+00:00
fetched_at: 2026-05-08T07:37:41.261710+00:00
content_hash: "8d6ec4ec77fda4fe6ed61dce4528e501040e4a421968b1f3bb18c5af8f7d1464"
lang: en
caption_quality: None
raw: true
topics: []
---

# Multi-Token Prediction (MTP) for LLaMA.cpp - Gemma 4 speedup by 40%

Implemented Multi-Token Prediction for LLaMA.cpp. Quantized Gemma 4 assistant models into GGUF format. Ran tests on a MacBook Pro M5Max. Gemma 26B with MTP drafts tokens 40% faster. Prompt: Write a Python program to find the nth Fibonacci number using recursion Outputs: LLaMA.cpp: 97 tokens/s LLaMA.cpp + MTP: 138 tokens/s Gemma4-assistant GGUF Quantized models: https://huggingface.co/collections/AtomicChat/gemma-4-assistant-gguf Local AI models app: http://atomic.chat Patched llama.cpp: https://github.com/AtomicBot-ai/atomic-llama-cpp-turboquant &#32; submitted by &#32; /u/gladkos [link] &#32; [comments]