---
id: inbox_a1f812e5
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_a1f812e5]]"
title: "2 old RTX 2080 Ti with 22GB vram each Qwen3.6 27B at 38 token/s with f16 kv cache"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdty58/2_old_rtx_2080_ti_with_22gb_vram_each_qwen36_27b/
source: reddit-localllama
published_at: 2026-05-15T11:48:52+00:00
fetched_at: 2026-05-18T03:59:25.016211+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在兩張老舊 RTX 2080 Ti（各 22GB 改裝 VRAM，功率限制 150W/卡）上部署 Qwen3.6-27B，達成 38 tokens/s 吞吐。使用 llama.cpp server、IQ4_XS 量化、f16 KV cache。三項關鍵優化：(1) --split-mode tensor 將吞吐從 14 t/s 推升至 38 t/s (+171%)，單項優化收益最大；(2) --fit on 動態管理 VRAM 以避免 95% 滿載，進一步穩定效能；(3) f16 KV cache 防止長編譯任務中的迴圈問題。總投資 <$1K，peak 功耗 400W（牆面），適合編譯、Hermes 應用。NVLINK 無顯著效益，因系統為計算而非頻寬受限。此案例展示老舊硬體透過量化與優化可達現代推理效能。"
key_points:
  - "2x RTX 2080 Ti (22GB ea, IQ4_XS 量化) 達 38 t/s，150W/卡功耗限制保持安靜；無功率限制估 45 t/s"
  - "--split-mode tensor 單項優化達 +171% 吞吐 (14→38 t/s)，遠優於 NVLINK、MTP 等硬體升級"
  - "總投資 <$1K USD，peak 400W，compute bound 而非 bandwidth bound；f16 KV cache 防長 context 迴圈"
tags: [qwen-3.6, local-inference, optimization, quantization, hardware-efficiency]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 2 old RTX 2080 Ti with 22GB vram each Qwen3.6 27B at 38 token/s with f16 kv cache

使用者在兩張老舊 RTX 2080 Ti（各 22GB 改裝 VRAM，功率限制 150W/卡）上部署 Qwen3.6-27B，達成 38 tokens/s 吞吐。使用 llama.cpp server、IQ4_XS 量化、f16 KV cache。三項關鍵優化：(1) --split-mode tensor 將吞吐從 14 t/s 推升至 38 t/s (+171%)，單項優化收益最大；(2) --fit on 動態管理 VRAM 以避免 95% 滿載，進一步穩定效能；(3) f16 KV cache 防止長編譯任務中的迴圈問題。總投資 <$1K，peak 功耗 400W（牆面），適合編譯、Hermes 應用。NVLINK 無顯著效益，因系統為計算而非頻寬受限。此案例展示老舊硬體透過量化與優化可達現代推理效能。

### 重點
- 2x RTX 2080 Ti (22GB ea, IQ4_XS 量化) 達 38 t/s，150W/卡功耗限制保持安靜；無功率限制估 45 t/s
- --split-mode tensor 單項優化達 +171% 吞吐 (14→38 t/s)，遠優於 NVLINK、MTP 等硬體升級
- 總投資 <$1K USD，peak 400W，compute bound 而非 bandwidth bound；f16 KV cache 防長 context 迴圈

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdty58/2_old_rtx_2080_ti_with_22gb_vram_each_qwen36_27b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 2 old RTX 2080 Ti with 22GB vram each Qwen3.6 27B at 38 token/s with f16 kv cache

PLEASE KEEP IN MIND BOTH OF MY CARDS ARE POWER LIMITED TO 150W (i hate noise) ------- Just wanted to share my current setup, that might help some users out there... services: llama-server: image: ghcr.io/ggml-org/llama.cpp:full-cuda12-b9128 container_name: llama-server restart: unless-stopped ports: - &quot;16384:8080&quot; volumes: - ./models:/models:ro command: &gt; --server --model /models/Qwen3.6-27B-IQ4_XS-uc.gguf --alias &quot;Qwen3.6 27B&quot; --temp 0.6 --top-p 0.95 --min-p 0.00 --top-k 20 --port 8080 --host 0.0.0.0 --cache-type-k f16 --cache-type-v f16 --fit on --presence-penalty 1.32 --repeat-penalty 1.0 --jinja --chat-template-file /models/Qwen3.6.jinja --mmproj /models/Qwen3.6-27B-mmproj-BF16.gguf --webui --spec-default --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' --reasoning-budget 8192 --reasoning-budget-message &quot;... thinking budget exceeded, let's answer now.\n&quot; --split-mode tensor user: &quot;1000:1000&quot; deploy: resources: reservations: devices: - driver: nvidia count: all capabilities: [gpu] environment: - NVIDIA_VISIBLE_DEVICES=all This is my exact config, my 2 extremely old 2080Ti gpus where upgraded in china to have 22GB vram each... and on ebay i bought a NVLINK (i do not recommend bying it, as no meassurable difference appears) Quantisation i run is IQ4_XS if i change the kv cache to q8_0 it sometimes happens during long coding sessions that the model loops, this is why i run kv-cache@f16 and never have this problem since then. i use the hauhaucs qwen3.6 model uncensored on IQ4 matrix quants. You can also forget about MTP as you are compute bound with those cards and not bandwidth bound. The absolut biggest boost came from --split-mode tensor , this gave me a boost from 14 token/s to 38t/s i think without the power limit we should get 45 token/s what i also never did think about is the --fit on ... i always declared context length manually worked great but it looks like its not a good idea to always run at 95% vram consumption. fit on also improved token gen a little. Btw. this is a &lt; 1k USD setup running on 400w peak on the wall, and it works great with hermes and opencode. the jinja template i use is this one: https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates (in this setup template 11, i did not yet test the newer templates) https://preview.redd.it/gasb8yo8ga1h1.png?width=476&amp;format=png&amp;auto=webp&amp;s=0450efcae279b0bcbd33f9d6d4f7241d8e3581d4 &#32; submitted by &#32; /u/snapo84 [link] &#32; [comments]

</details>