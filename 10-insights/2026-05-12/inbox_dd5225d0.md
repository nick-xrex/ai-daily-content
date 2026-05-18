---
id: inbox_dd5225d0
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-mtp-ggml-cuda-enable-unified-memory-1-ll-71ad]]"
title: "MTP+GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 - llama.cpp"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tb17bp/mtpggml_cuda_enable_unified_memory1_llamacpp/
source: reddit-localllama
published_at: 2026-05-12T13:10:26+00:00
fetched_at: 2026-05-12T18:14:18.620915+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 使用 MTP（推測解碼）與 CUDA 統一記憶體優化的性能基準測試。搭配 RTX5090 與 Ryzen 9 9950X3D，啟用 GGML_CUDA_ENABLE_UNIFIED_MEMORY 後，Qwen3.6-27B-Q8_0 模型推論速度從 49 token/秒提升至 64 token/秒，達成約 30% 的吞吐量增益。該優化配置對本地高效推論有實務價值。"
key_points:
  - "MTP 推測解碼在 RTX5090 上達成 30% 吞吐量提升（49→64 tok/sec）"
  - "CUDA 統一記憶體模式（GGML_CUDA_ENABLE_UNIFIED_MEMORY=1）是觸發優化的關鍵標誌"
  - "支援 Qwen3.6-27B-Q8_0 等大型量化模型的本地推論加速"
tags: [llama.cpp, mtp, speculative-decoding, cuda-optimization, inference-throughput]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## MTP+GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 - llama.cpp

llama.cpp 使用 MTP（推測解碼）與 CUDA 統一記憶體優化的性能基準測試。搭配 RTX5090 與 Ryzen 9 9950X3D，啟用 GGML_CUDA_ENABLE_UNIFIED_MEMORY 後，Qwen3.6-27B-Q8_0 模型推論速度從 49 token/秒提升至 64 token/秒，達成約 30% 的吞吐量增益。該優化配置對本地高效推論有實務價值。

### 重點
- MTP 推測解碼在 RTX5090 上達成 30% 吞吐量提升（49→64 tok/sec）
- CUDA 統一記憶體模式（GGML_CUDA_ENABLE_UNIFIED_MEMORY=1）是觸發優化的關鍵標誌
- 支援 Qwen3.6-27B-Q8_0 等大型量化模型的本地推論加速

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tb17bp/mtpggml_cuda_enable_unified_memory1_llamacpp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I was wondering what will be the difference in results with flag: GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 vs MTP+GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 Results are quite interesting 49tok/sec without MTP vs 64 tok/sec with MTP. PC: RTX5090+128GB DDR5 5600 CL36+Ryzen 9 9950X3D Model: Qwen3.6-27B-Q8_0.gguf (Unsloth with MTP) Command: CUDA_VISIBLE_DEVICES=0 GGML_CUDA_ENABLE_UNIFIED_MEMORY=1 /home/marcin/llama-server \ -m /home/marcin/Pobrane/Qwen3.6-27B-Q8_0.gguf \ --threads 16 \ -c 262144 -fa on -np 1 \ --spec-type mtp --spec-draft-n-max 3 \ --webui-mcp-proxy \ --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' \ --host 0.0.0.0 \ --port 8090 \ --jinja &#32; submitted by &#32; /u/mossy_troll_84 [link] &#32; [comments]

</details>