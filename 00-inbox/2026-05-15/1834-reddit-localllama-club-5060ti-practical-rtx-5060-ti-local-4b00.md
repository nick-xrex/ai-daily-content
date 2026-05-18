---
id: inbox_72f4a20c
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdikc4/club5060ti_practical_rtx_5060_ti_local_llm_notes/"
author: "/u/do_u_think_im_spooky"
published_at: 2026-05-15T02:07:04+00:00
fetched_at: 2026-05-15T18:34:22.462222+00:00
content_hash: "4b00b528d4a593149fcb13ae9ec2f3677af8cea11ce42c5a06c9a3a56c721e7c"
lang: en
caption_quality: None
raw: true
topics: []
---

# club-5060ti: practical RTX 5060 Ti local LLM notes and configs

I put together a small public repo for RTX 5060 Ti 16GB local LLM setups: I took inspiration from the club-3090 repo, but this one is focused on documenting what we’ve actually tested on 5060 Ti hardware so the setup details are easier to share and reproduce. Current seed setup is 2x RTX 5060 Ti 16GB on Linux, with notes for: - vLLM serving Qwen3.6 27B NVFP4/MTP - llama.cpp MTP GGUF serving for Qwen3.6 27B Q4/Q6 - Q6 long-context fit checks, including a 204800 direct long-context preset - a safer 65536 llama.cpp router preset for extra headroom - initial Qwen3.6 35B A3B checks on llama.cpp and vLLM - sanitized launch examples - model download and llama.cpp update helper scripts - simple OpenAI-compatible smoke/bench scripts - CSV seed results and report templates The aim is to keep it practical: exact configs, versions, context lengths, KV settings, and caveats rather than vague tokens/sec claims. If anyone else is testing similar 5060 Ti setups, feel free to open an issue or PR with enough detail to reproduce the result. &#32; submitted by &#32; /u/do_u_think_im_spooky [link] &#32; [comments]