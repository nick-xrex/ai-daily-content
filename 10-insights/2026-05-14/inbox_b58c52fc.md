---
id: inbox_b58c52fc
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_b58c52fc]]"
title: "Multi-Token Prediction (MTP) for Qwen on LLaMA.cpp + TurboQuant"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tckzy2/multitoken_prediction_mtp_for_qwen_on_llamacpp/
source: reddit-localllama
published_at: 2026-05-14T02:35:49+00:00
fetched_at: 2026-05-18T03:40:23.829817+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在 LLaMA.cpp + TurboQuant 上實現 Qwen 多令牌預測（MTP），於 MacBook Pro M5 Max 64GB RAM 本地執行，推理速度從 21 tokens/s 提升至 34 tokens/s（提升 ~62%），接受率達 90%。公開修補 LLaMA.cpp 版本與量化模型（Qwen 3.6/3.5B GGUF），搭配 Atomic.Chat 應用發布，展示消費級硬體透過指定最佳化組合達成高效本地推理的可行性。"
key_points:
  - "多令牌預測實現：LLaMA.cpp + TurboQuant 組合下 Qwen 最佳化，21→34 tokens/s、90% 接受率"
  - "硬體環境：MacBook Pro M5 Max 64GB RAM 本地執行（零雲端依賴）"
  - "開源釋出：修補 LLaMA.cpp、Qwen 3.6/35B GGUF 量化模型、Atomic.Chat App、GitHub/HuggingFace 鏈結"
tags: [multi-token-prediction, qwen, llama-cpp, local-inference, turboquant]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Multi-Token Prediction (MTP) for Qwen on LLaMA.cpp + TurboQuant

開發者在 LLaMA.cpp + TurboQuant 上實現 Qwen 多令牌預測（MTP），於 MacBook Pro M5 Max 64GB RAM 本地執行，推理速度從 21 tokens/s 提升至 34 tokens/s（提升 ~62%），接受率達 90%。公開修補 LLaMA.cpp 版本與量化模型（Qwen 3.6/3.5B GGUF），搭配 Atomic.Chat 應用發布，展示消費級硬體透過指定最佳化組合達成高效本地推理的可行性。

### 重點
- 多令牌預測實現：LLaMA.cpp + TurboQuant 組合下 Qwen 最佳化，21→34 tokens/s、90% 接受率
- 硬體環境：MacBook Pro M5 Max 64GB RAM 本地執行（零雲端依賴）
- 開源釋出：修補 LLaMA.cpp、Qwen 3.6/35B GGUF 量化模型、Atomic.Chat App、GitHub/HuggingFace 鏈結

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tckzy2/multitoken_prediction_mtp_for_qwen_on_llamacpp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Multi-Token Prediction (MTP) for Qwen on LLaMA.cpp + TurboQuant

Implemented Multi-Token Prediction for QWEN on LLaMA.cpp with TurboQuant. +40% performance! 90% acceptance rate. Running locally on a MacBook Pro M5 Max 64GB RAM. Outputs: LLaMA.cpp + TurboQuant: 21 tokens/s LLaMA.cpp + TurboQuant + MTP: 34 tokens/s Patched LLaMA.cpp with MTP and TurboQuant: https://github.com/AtomicBot-ai/atomic-llama-cpp-turboquant Quantized Qwen 3.6 27B (and 35B) into GGUF with MTP: https://huggingface.co/collections/AtomicChat/qwen-36-udt-mtp Local Ai Models App: Atomic.Chat &#32; submitted by &#32; /u/gladkos [link] &#32; [comments]

</details>