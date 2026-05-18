---
id: inbox_0c7e7647
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_0c7e7647]]"
title: "Llama.cpp MTP with Qwen3.6 27B on Headless RTX 3090"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfilwx/llamacpp_mtp_with_qwen36_27b_on_headless_rtx_3090/
source: reddit-localllama
published_at: 2026-05-17T07:31:41+00:00
fetched_at: 2026-05-18T04:10:16.966955+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Llama.cpp MTP 實測：RTX 3090 + Qwen3.6-27B-Q4_K_M 在 85k tokens 工作量上，MTP 帶來 41% 總耗時縮減（39 分鐘 → 23 分鐘）。Prefill 速度下降 42%（1050 → 600 tok/s），但 Token generation 加倍（27 → 50 tok/s），整體吞吐 1.7 倍加速。對非 prefill 密集型工作流有顯著收益，建議嘗試。"
key_points:
  - "MTP 啟用後 41% 時間縮減：39 分鐘 → 23 分鐘（85k token 工作負荷）"
  - "Prefill 速度 −42%（1050→600 tok/s）；Token generation +85%（27→50 tok/s）；整體 1.7x speedup"
  - "Dual-agent setup 下效果更明顯；建議非 prefill 密集型優先啟用 MTP"
tags: [llama-cpp, mtp, qwen-3.6, benchmark, gpu-optimization]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Llama.cpp MTP with Qwen3.6 27B on Headless RTX 3090

Llama.cpp MTP 實測：RTX 3090 + Qwen3.6-27B-Q4_K_M 在 85k tokens 工作量上，MTP 帶來 41% 總耗時縮減（39 分鐘 → 23 分鐘）。Prefill 速度下降 42%（1050 → 600 tok/s），但 Token generation 加倍（27 → 50 tok/s），整體吞吐 1.7 倍加速。對非 prefill 密集型工作流有顯著收益，建議嘗試。

### 重點
- MTP 啟用後 41% 時間縮減：39 分鐘 → 23 分鐘（85k token 工作負荷）
- Prefill 速度 −42%（1050→600 tok/s）；Token generation +85%（27→50 tok/s）；整體 1.7x speedup
- Dual-agent setup 下效果更明顯；建議非 prefill 密集型優先啟用 MTP

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfilwx/llamacpp_mtp_with_qwen36_27b_on_headless_rtx_3090/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Llama.cpp MTP with Qwen3.6 27B on Headless RTX 3090

Saw some posts around PP being slower, so they were cautious on trying it. Here's a real-world datapoint. Settings: Headless RTX 3090 24G OpenCode Model unsloth's Qwen3.6-27B-MTP-Q4_K_M.gguf 128k context q8_0 kv cache --spec-draft-n-max: 3 --draft-p-min: 0 Use Cases: Research task that uses ~85,000 tokens Coding task that uses ~85,000 tokens. Without MTP (llama.cpp:server-cuda13-b9174): PP: 1,050 tok/s TG: 27 toks/s Total time to complete 85k tokens: ~39 mins With MTP (latest master fork): PP: 600 tok/s (down 42%) TG: 50 tok/s (up 85%) Total time to complete 85k tokens: ~23 mins (1.7x faster or 41% reduction) A 41% time savings is quite huge, so unless you're PP heavy, I'd recommend giving MTP a try on your use cases! I have it on a dual agent set-up so your total processing times may be better since I have another critic agent check the main agent's work. &#32; submitted by &#32; /u/cleversmoke [link] &#32; [comments]

</details>