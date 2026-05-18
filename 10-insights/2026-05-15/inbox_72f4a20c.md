---
id: inbox_72f4a20c
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_72f4a20c]]"
title: "club-5060ti: practical RTX 5060 Ti local LLM notes and configs"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdikc4/club5060ti_practical_rtx_5060_ti_local_llm_notes/
source: reddit-localllama
published_at: 2026-05-15T02:07:04+00:00
fetched_at: 2026-05-18T03:57:49.572446+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "club-5060ti 項目發布，針對 RTX 5060 Ti 16GB 的實務化本地 LLM 配置文檔庫（類似 club-3090）。測試硬件配置為 2x RTX 5060 Ti 16GB on Linux，提供 vLLM (NVFP4/MTP) 和 llama.cpp (Q4/Q6 GGUF) 運行 Qwen 3.6 27B 及初步 35B 測試。長上下文支持達 204800（Q6）及安全預設 65536；含具體版本號、KV 設置、VRAM 計算器、模型下載和 OpenAI 兼容測試腳本。強調精確可複製配置勝過虛假速度宣稱。"
key_points:
  - "club-5060ti repo：2x RTX 5060 Ti 16GB Linux 實測配置，支援 vLLM + llama.cpp 並行部署 Qwen 3.6 27B"
  - "Qwen 3.6 27B Q6 長上下文可達 204800 token，安全預設 65536，提供具體版本和 KV 參數"
  - "包含 VRAM 計算器、模型下載腳本、OpenAI 兼容煙火測試工具，強調可複製性"
tags: [rtx-5060-ti, qwen, vllm, llama-cpp, local-llm]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## club-5060ti: practical RTX 5060 Ti local LLM notes and configs

club-5060ti 項目發布，針對 RTX 5060 Ti 16GB 的實務化本地 LLM 配置文檔庫（類似 club-3090）。測試硬件配置為 2x RTX 5060 Ti 16GB on Linux，提供 vLLM (NVFP4/MTP) 和 llama.cpp (Q4/Q6 GGUF) 運行 Qwen 3.6 27B 及初步 35B 測試。長上下文支持達 204800（Q6）及安全預設 65536；含具體版本號、KV 設置、VRAM 計算器、模型下載和 OpenAI 兼容測試腳本。強調精確可複製配置勝過虛假速度宣稱。

### 重點
- club-5060ti repo：2x RTX 5060 Ti 16GB Linux 實測配置，支援 vLLM + llama.cpp 並行部署 Qwen 3.6 27B
- Qwen 3.6 27B Q6 長上下文可達 204800 token，安全預設 65536，提供具體版本和 KV 參數
- 包含 VRAM 計算器、模型下載腳本、OpenAI 兼容煙火測試工具，強調可複製性

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdikc4/club5060ti_practical_rtx_5060_ti_local_llm_notes/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# club-5060ti: practical RTX 5060 Ti local LLM notes and configs

I put together a small public repo for RTX 5060 Ti 16GB local LLM setups: I took inspiration from the club-3090 repo, but this one is focused on documenting what we’ve actually tested on 5060 Ti hardware so the setup details are easier to share and reproduce. Current seed setup is 2x RTX 5060 Ti 16GB on Linux, with notes for: - vLLM serving Qwen3.6 27B NVFP4/MTP - llama.cpp MTP GGUF serving for Qwen3.6 27B Q4/Q6 - Q6 long-context fit checks, including a 204800 direct long-context preset - a safer 65536 llama.cpp router preset for extra headroom - initial Qwen3.6 35B A3B checks on llama.cpp and vLLM - sanitized launch examples - model download and llama.cpp update helper scripts - simple OpenAI-compatible smoke/bench scripts - CSV seed results and report templates The aim is to keep it practical: exact configs, versions, context lengths, KV settings, and caveats rather than vague tokens/sec claims. If anyone else is testing similar 5060 Ti setups, feel free to open an issue or PR with enough detail to reproduce the result. &#32; submitted by &#32; /u/do_u_think_im_spooky [link] &#32; [comments]

</details>