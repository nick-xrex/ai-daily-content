---
id: inbox_6a68d1db
date: 2026-05-08
source_ref: "[[00-inbox/.../inbox_6a68d1db]]"
title: "Qwen 35B-A3B is very usable with 12GB of VRAM"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7l56a/qwen_35ba3b_is_very_usable_with_12gb_of_vram/
source: reddit-localllama
published_at: 2026-05-08T21:22:55+00:00
fetched_at: 2026-05-09T02:53:47.595015+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 Reddit 報告 Qwen 35B-A3B (MoE 模型) 在 RTX 3060 12GB VRAM 上的推理效能測試。通過調整 -ncmoe 參數 (專家卸載)，在 32k context 下達到 prefix 速度 914 t/s、生成速度 43.4 t/s，保留 ~273MB 顯存。經測試，MTP (Multi-Token Prediction) 推測解碼相比優化的純解碼僅帶來 ~2% 生成加速 (46.8→47.7 t/s)。作者認為 12GB VRAM 是該 MoE 模型的實用甜蜜點，在 -ncmoe 18-20 範圍內純解碼最穩定，-ncmoe 16 會觸發性能懸崖。"
key_points:
  - "Qwen 35B-A3B 在 RTX 3060 12GB 上達到 914 t/s (prefill/pp512) 與 43.4 t/s (generation/32k context)，驗證 MoE 在中等顯存上的可行性"
  - "-ncmoe 18-20 是純解碼安全區間，-ncmoe 16 性能暴跌至 25.8 t/s，示範 MoE 專家卸載的臨界值"
  - "MTP depth=2 僅增加 ~2% 生成速度，調優純解碼成本效益更高"
tags: [qwen-35b-moe, llama-cpp, 12gb-vram, mtp-speculative, inference-tuning]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 35B-A3B is very usable with 12GB of VRAM

用戶在 Reddit 報告 Qwen 35B-A3B (MoE 模型) 在 RTX 3060 12GB VRAM 上的推理效能測試。通過調整 -ncmoe 參數 (專家卸載)，在 32k context 下達到 prefix 速度 914 t/s、生成速度 43.4 t/s，保留 ~273MB 顯存。經測試，MTP (Multi-Token Prediction) 推測解碼相比優化的純解碼僅帶來 ~2% 生成加速 (46.8→47.7 t/s)。作者認為 12GB VRAM 是該 MoE 模型的實用甜蜜點，在 -ncmoe 18-20 範圍內純解碼最穩定，-ncmoe 16 會觸發性能懸崖。

### 重點
- Qwen 35B-A3B 在 RTX 3060 12GB 上達到 914 t/s (prefill/pp512) 與 43.4 t/s (generation/32k context)，驗證 MoE 在中等顯存上的可行性
- -ncmoe 18-20 是純解碼安全區間，-ncmoe 16 性能暴跌至 25.8 t/s，示範 MoE 專家卸載的臨界值
- MTP depth=2 僅增加 ~2% 生成速度，調優純解碼成本效益更高

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7l56a/qwen_35ba3b_is_very_usable_with_12gb_of_vram/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Qwen 35B-A3B is very usable with 12GB of VRAM

Hardware: RTX 3060 12GB 32GB DDR4-3200 Windows CUDA 13.x Model: Qwen3.6-35B-A3B-MTP-IQ4_XS.gguf The model is a 35B MoE, so -ncmoe matters a lot. Lower -ncmoe means more MoE blocks stay on GPU. Main takeaway 12GB VRAM feels like a very practical size for this model. It lets you keep enough MoE blocks on GPU that plain decoding becomes quite strong, while still leaving room for useful context sizes like 16k/32k. For prompt processing / prefill, I trust the llama-bench numbers more than llama-cli ’s interactive Prompt: line, because llama-bench gives a cleaner pp512 measurement. Best plain llama-bench result: -ncmoe 18 -t 9 -ctk q8_0 -ctv q8_0 pp512: ~914 t/s tg128: ~46.8 t/s So raw prefill is very fast on this setup. Best practical coding profile For daily coding, I would use this: llama-cli.exe ^ -m &quot;Qwen3.6-35B-A3B-MTP-IQ4_XS.gguf&quot; ^ -p &quot;...&quot; ^ -n 512 ^ -c 32768 ^ --temp 0 --top-k 1 ^ -ngl 999 -ncmoe 20 ^ -fa on ^ -ctk q8_0 -ctv q8_0 ^ --no-mmap ^ --no-jinja ^ -t 9 ^ --perf Result: Context: 32k Prompt: ~88.9 t/s in llama-cli Generation: ~43.4 t/s VRAM free: ~273 MiB This is a nice balance: large enough context for coding, still fast, and not completely out of VRAM. Faster 16k profile -c 16384 -ncmoe 19 -ctk q8_0 -ctv q8_0 -t 9 Result: Prompt: ~91.5 t/s in llama-cli Generation: ~44.5 t/s VRAM free: ~37 MiB This is slightly faster, but very close to the VRAM edge. MoE offload sweep Plain decoding, q4 KV, -t 11 : -ncmoe 22: tg128 ~41.6 t/s -ncmoe 20: tg128 ~41.7 t/s -ncmoe 19: tg128 ~44.2 t/s -ncmoe 18: tg128 ~45.9 t/s -ncmoe 17: tg128 ~46.6 t/s -ncmoe 16: tg128 ~25.8 t/s &lt;-- cliff / too aggressive So for plain decoding: safe: -ncmoe 18 edge: -ncmoe 17 avoid: -ncmoe 16 KV cache sweep At -ncmoe 18 , -t 11 : q4_0 KV: pp512 ~913 t/s, tg128 ~45.8 t/s q8_0 KV: pp512 ~915 t/s, tg128 ~45.9 t/s q5_0 KV: much slower mixed q8 K + q4/q5 V: much slower So on this GPU, q8 KV is basically free and preferable: -ctk q8_0 -ctv q8_0 MTP / speculative decoding I also tested MTP with the llama.cpp MTP branch. Best MTP command: llama-cli.exe ^ -m &quot;Qwen3.6-35B-A3B-MTP-IQ4_XS.gguf&quot; ^ --spec-type mtp ^ -p &quot;...&quot; ^ -n 512 ^ --spec-draft-n-max 2 ^ -c 4096 ^ --temp 0 --top-k 1 ^ -ngl 999 -ncmoe 19 ^ -fa on ^ -ctk q4_0 -ctv q4_0 ^ --no-mmap ^ --no-jinja ^ -t 11 ^ --perf Result: Generation: ~47.7 t/s MTP sweep: -ncmoe 24, depth 2: ~43.8 t/s -ncmoe 20, depth 2: ~46.6 t/s -ncmoe 19, depth 2: ~47.7 t/s -ncmoe 18: failed / invalid vector subscript -ncmoe 16: failed / invalid vector subscript Depth 3 was worse: depth 3, -ncmoe 20: ~39.8 t/s So the MTP sweet spot was: --spec-draft-n-max 2 Conclusion With 12GB VRAM, plain decoding is already very strong: Plain llama-bench: ~914 t/s pp512, ~46.8 t/s tg128 Best MTP observed: ~47.7 t/s generation So MTP only gave about a 2% generation speedup over well-tuned plain decoding. For coding, I would personally use plain decoding with 32k context: -c 32768 -ncmoe 20 -ctk q8_0 -ctv q8_0 -t 9 The big lesson: for this MoE model, 12GB VRAM is a very practical sweet spot . It keeps enough experts on GPU that plain decoding becomes fast, q8 KV is usable, and 32k context is realistic. &#32; submitted by &#32; /u/jwestra [link] &#32; [comments]

</details>