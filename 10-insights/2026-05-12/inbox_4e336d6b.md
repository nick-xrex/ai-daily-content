---
id: inbox_4e336d6b
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-stop-wasting-electricity-b4c9]]"
title: "Stop wasting electricity"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tayu5t/stop_wasting_electricity/
source: reddit-localllama
published_at: 2026-05-12T11:32:23+00:00
fetched_at: 2026-05-12T18:11:04.456283+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "分享在 RTX4090 上透過 GPU 功耗限制（nvidia-smi -pl）最佳化 llama.cpp 推理的方法。通過降低功耗限制至原本的 40%，在無性能損失的情況下大幅降低電力消耗、噪音與熱量，延長 GPU 壽命。文中提供了具體的 llama-server 參數配置（-ngl all、-ctk/-ctv q4_0、-t 32 等），適用於 Qwen3.6-27B 等大規模量化模型的部署。"
key_points:
  - "GPU 功耗降至 40% 原限制值而無性能損失，使用 nvidia-smi -pl 指令設置"
  - "同步降低噪音、熱量，延長 GPU 壽命，提升運行環境品質"
  - "配置案例：RTX4090 + Qwen3.6-27B-UD-Q4_K_XL，配合 flash attention、-ngl all GPU 卸載、q4_0 KV cache、32 執行緒"
tags: [power-optimization, rtx4090, llama-cpp, energy-efficiency]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop wasting electricity

分享在 RTX4090 上透過 GPU 功耗限制（nvidia-smi -pl）最佳化 llama.cpp 推理的方法。通過降低功耗限制至原本的 40%，在無性能損失的情況下大幅降低電力消耗、噪音與熱量，延長 GPU 壽命。文中提供了具體的 llama-server 參數配置（-ngl all、-ctk/-ctv q4_0、-t 32 等），適用於 Qwen3.6-27B 等大規模量化模型的部署。

### 重點
- GPU 功耗降至 40% 原限制值而無性能損失，使用 nvidia-smi -pl 指令設置
- 同步降低噪音、熱量，延長 GPU 壽命，提升運行環境品質
- 配置案例：RTX4090 + Qwen3.6-27B-UD-Q4_K_XL，配合 flash attention、-ngl all GPU 卸載、q4_0 KV cache、32 執行緒

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tayu5t/stop_wasting_electricity/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Run on my rtx4090 llama.cpp params: llama-server -m ~/Projects/llm/models/Qwen3.6-27B-UD-Q4_K_XL.gguf --flash-attn on -ngl all -ctk q4_0 -ctv q4_0 -t 32 -c 262144 Power limit was set using sudo nvidia-smi -pl N On my observation, GPU constantly hitting power limit, so its safe to say that it actual consumption. You can cut power consumption to 40% without losing performance(and also reduce noise, heat from pc, and extend lifespan of gpu). &#32; submitted by &#32; /u/OkFly3388 [link] &#32; [comments]

</details>