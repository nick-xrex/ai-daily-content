---
id: inbox_ae6f1495
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_ae6f1495]]"
title: "Running Qwen3.6 35b a3b on 8gb vram and 32gb ram ~190k context"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9eo83/running_qwen36_35b_a3b_on_8gb_vram_and_32gb_ram/
source: reddit-localllama
published_at: 2026-05-10T18:24:29+00:00
fetched_at: 2026-05-11T02:21:09.105124+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在消費級硬體（RTX 4060 8GB + DDR5 5600MHz 32GB RAM）上成功執行 Qwen 3.6 35B A3B Q5 量化模型，支援 ~190K context，達 37–51 tokens/s。關鍵最佳化包括 TurboQuant KV cache（效果最顯著）、--no-mmap + --mlock 減少記憶體抖動、flash-attn、ctx-size=192640、n-gpu-layers=430。作者強調 Q5 相比 Q4 在長 context 推理穩定性更佳，DDR5 記憶體頻寬關鍵，Linux 優於 Windows。"
key_points:
  - "Qwen 3.6 35B A3B Q5 在 RTX 4060 達 37–51 tokens/s，支援 190K context；TurboQuant KV cache 效果最大"
  - "關鍵設置：ctx-size=192640、n-gpu-layers=430、n-cpu-moe=35、flash-attn=on、batch-size=2048"
  - "硬體與軟體均衡：DDR5 記憶體頻寬、Q5 vs Q4 穩定性權衡、Linux 效能優於 Windows"
tags: [qwen, quantization, turboquant, long-context, optimization]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Running Qwen3.6 35b a3b on 8gb vram and 32gb ram ~190k context

使用者在消費級硬體（RTX 4060 8GB + DDR5 5600MHz 32GB RAM）上成功執行 Qwen 3.6 35B A3B Q5 量化模型，支援 ~190K context，達 37–51 tokens/s。關鍵最佳化包括 TurboQuant KV cache（效果最顯著）、--no-mmap + --mlock 減少記憶體抖動、flash-attn、ctx-size=192640、n-gpu-layers=430。作者強調 Q5 相比 Q4 在長 context 推理穩定性更佳，DDR5 記憶體頻寬關鍵，Linux 優於 Windows。

### 重點
- Qwen 3.6 35B A3B Q5 在 RTX 4060 達 37–51 tokens/s，支援 190K context；TurboQuant KV cache 效果最大
- 關鍵設置：ctx-size=192640、n-gpu-layers=430、n-cpu-moe=35、flash-attn=on、batch-size=2048
- 硬體與軟體均衡：DDR5 記憶體頻寬、Q5 vs Q4 穩定性權衡、Linux 效能優於 Windows

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9eo83/running_qwen36_35b_a3b_on_8gb_vram_and_32gb_ram/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Running Qwen3.6 35b a3b on 8gb vram and 32gb ram ~190k context

If anyone is looking for a good high-speed setup with ~190k context, this config has been working insanely well for me. I’m using my laptop as a server over Tailscale. Installed Linux on it and running: - Qwen3.6 35B A3B - RTX 4060 8GB VRAM - 32GB DDR5 5600MHz RAM - Q5 quant models Current models tested: - `mudler/Qwen3.6-35B-A3B-APEX-GGUF` - ~40 tok/sec → 37 tok/sec - `hesamation/Qwen3.6-35B-A3B-Claude-4.6-Opus-Reasoning-Distilled-GGUF` - ~43 tok/sec → 37 tok/sec I can push it up to ~51 tok/sec by tweaking: - `--ctx-size 192640` - `--n-gpu-layers 430` - `--n-cpu-moe 35` and adjusting those values slightly higher/lower depending on stability and memory usage. Here’s my current config: #!/bin/bash # --- LLAMA SERVER LAUNCHER SCRIPT --- #SELECTED_MODEL=&quot;/home/atulloq/.lmstudio/models/hesamation/Qwen3.6-35B-A3B-Claude-4.6-Opus-Reasoning-Distilled-GGUF/Qwen3.6-35B-A3B-Claude-4.6-Opus-Reasoning-Distilled.Q5_K_M.gguf&quot; SELECTED_MODEL=&quot;/home/atulloq/.lmstudio/models/mudler/Qwen3.6-35B-A3B-APEX-GGUF/Qwen3.6-35B-A3B-APEX-I-Balanced.gguf&quot; echo &quot;Starting Llama Server...&quot; echo &quot;Model: $SELECTED_MODEL&quot; /home/atulloq/llama-cpp-turboquant/build/bin/llama-server \ --model &quot;$SELECTED_MODEL&quot; \ --host 0.0.0.0 \ --port 8085 \ --ctx-size 192640 \ --n-gpu-layers 430 \ --n-cpu-moe 35 \ --cache-type-k &quot;turbo4&quot; \ --cache-type-v &quot;turbo4&quot; \ --flash-attn on \ --batch-size 2048 \ --parallel 1 \ --no-mmap \ --mlock \ --ubatch-size 512 \ --threads 6 \ --cont-batching \ --timeout 300 \ --temp 0.2 \ --top-p 0.95 \ --min-p 0.05 \ --top-k 20 \ --metrics \ --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' I’m using this fork of llama.cpp with TurboQuant support: https://github.com/TheTom/turboquant_plus#build-llamacpp-with-turboquant A few honest notes: - Q4 is noticeably worse for long-context reasoning compared to Q5 on these models. - `--no-mmap` + `--mlock` helped reduce weird slowdowns for me. - TurboQuant KV cache makes a massive difference at high context sizes. - Linux performs way better than Windows for this setup. - Don’t expect these speeds if your RAM bandwidth is bad. DDR5 matters here. If anyone has optimizations for: - better long-context stability, - higher token throughput, - or smarter `n-cpu-moe` tuning, I’d love to test them. &#32; submitted by &#32; /u/Atul_Kumar_97 [link] &#32; [comments]

</details>