---
id: inbox_57a0e57c
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1td7gp8/introducing_cyankiwi_awq_4bit_quantization_2605/"
author: "/u/_cpatonn"
published_at: 2026-05-14T18:49:21+00:00
fetched_at: 2026-05-15T18:34:22.483532+00:00
content_hash: "314e220570210b30a311963b1f85d07f5c00bfe444e9a8e70f6cb07e8b976988"
lang: en
caption_quality: None
raw: true
topics: []
---

# Introducing cyankiwi AWQ 4-bit Quantization — 26.05 update

In standard AWQ, per-channel scales and quantization ranges are picked in separate steps: scales first, then the quantization parameters. But they're not independent, i.e., the rounding error from one depends on the choice of the other, so optimizing them in sequence leaves quality on the table. Our cyankiwi AWQ 26.05 update jointly fits scales and quantization ranges against a reconstruction objective. We benchmarked cyankiwi AWQ 26.05 update against every major 4-bit method on Llama-3 as examples, measuring KL Divergence vs the BF16 baseline on GPQA Diamond responses. Result: cyankiwi posts the lowest KLD on all three base models. Lower is better. Llama-3.2-3B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.2-3B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.00510 unsloth/Llama-3.2-3B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.00785 unsloth/Llama-3.2-3B-Instruct-bnb-4bit BNB NF4 0.00896 nvidia/Meta-Llama-3.2-3B-Instruct-ONNX-INT4 AWQ INT4 0.01494 casperhansen/llama-3.2-3b-instruct-awq AWQ INT4 0.02437 Llama-3.1-8B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.1-8B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.00478 RedHatAI/Meta-Llama-3.1-8B-Instruct-quantized.w4a16 GPTQ INT4 0.00729 unsloth/Meta-Llama-3.1-8B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.00769 unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit BNB NF4 0.00835 RedHatAI/Llama-3.1-8B-Instruct-NVFP4 SmoothQuant NVFP4 0.01059 nvidia/Llama-3.1-8B-Instruct-NVFP4 NVFP4 0.01190 Llama-3.3-70B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.3-70B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.02826 unsloth/Llama-3.3-70B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.04444 casperhansen/llama-3.3-70b-instruct-awq AWQ INT4 0.04859 unsloth/Llama-3.3-70B-Instruct-bnb-4bit BNB NF4 0.06879 nvidia/Llama-3.3-70B-Instruct-NVFP4 NVFP4 0.08307 RedHatAI/Llama-3.3-70B-Instruct-quantized.w4a16 GPTQ INT4 0.09272 https://preview.redd.it/uicubbg6951h1.png?width=6400&amp;format=png&amp;auto=webp&amp;s=2f7f1d4e46c9953f00c68518b3c2aa058fc34e32 &#32; submitted by &#32; /u/_cpatonn [link] &#32; [comments]