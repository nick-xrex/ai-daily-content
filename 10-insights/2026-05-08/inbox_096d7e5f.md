---
id: inbox_096d7e5f
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-vllm-rocm-has-been-added-to-lemonade-as-16d5]]"
title: "vLLM ROCm has been added to Lemonade as an experimental backend"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7g70j/vllm_rocm_has_been_added_to_lemonade_as_an/
source: reddit-localllama
published_at: 2026-05-08T18:21:15+00:00
fetched_at: 2026-05-09T02:07:45.170565+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lemonade LLM 伺服器新增 vLLM ROCm 作為實驗性後端支援。核心優勢：vLLM 可直接執行 .safetensors 格式 LLM 而無需轉換為 GGUF 格式。安裝和運行極簡單（`lemonade backends install vllm:rocm` 再執行 `lemonade run Qwen3.5-0.8B-vLLM`）。雖是實驗性階段，但基礎功能已完整實現；AMD 貢獻者 krishna2910-amd、mikkoph、sa1sr1 將 vLLM 整合得與 llama.cpp 一樣易用。"
key_points:
  - "vLLM ROCm 後端支援直接執行 .safetensors，無需 GGUF 轉換步驟，加快模型測試流程"
  - "一行指令安裝 `lemonade backends install vllm:rocm`，再用 `lemonade run` 啟動模型，易用性等同 llama.cpp"
  - "實驗性但功能完整，已知粗糙邊角，明確邀請社群反饋以決定後續投入"
tags: [vllm, rocm, lemonade, backend, safetensors, amd]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## vLLM ROCm has been added to Lemonade as an experimental backend

Lemonade LLM 伺服器新增 vLLM ROCm 作為實驗性後端支援。核心優勢：vLLM 可直接執行 .safetensors 格式 LLM 而無需轉換為 GGUF 格式。安裝和運行極簡單（`lemonade backends install vllm:rocm` 再執行 `lemonade run Qwen3.5-0.8B-vLLM`）。雖是實驗性階段，但基礎功能已完整實現；AMD 貢獻者 krishna2910-amd、mikkoph、sa1sr1 將 vLLM 整合得與 llama.cpp 一樣易用。

### 重點
- vLLM ROCm 後端支援直接執行 .safetensors，無需 GGUF 轉換步驟，加快模型測試流程
- 一行指令安裝 `lemonade backends install vllm:rocm`，再用 `lemonade run` 啟動模型，易用性等同 llama.cpp
- 實驗性但功能完整，已知粗糙邊角，明確邀請社群反饋以決定後續投入

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7g70j/vllm_rocm_has_been_added_to_lemonade_as_an/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

vLLM has the ability to run .safetensors LLMs before they are converted to GGUF and represents a new engine to explore. I personally had never tried it out until u/krishna2910-amd/ u/mikkoph and u/sa1sr1 made it as easy as running llama.cpp in Lemonade: lemonade backends install vllm:rocm lemonade run Qwen3.5-0.8B-vLLM This is an experimental backend for us in the sense that the essentials are implemented, but there are known rough edges. We want the community's feedback to see where and how far we should take this. If you find it interesting, please let us know your thoughts! Quick start guide: https://lemonade-server.ai/news/vllm-rocm.html GitHub: https://github.com/lemonade-sdk/lemonade Discord: https://discord.gg/5xXzkMu8Zk &#32; submitted by &#32; /u/jfowers_amd [link] &#32; [comments]

</details>