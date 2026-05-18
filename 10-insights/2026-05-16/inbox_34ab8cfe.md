---
id: inbox_34ab8cfe
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_34ab8cfe]]"
title: "Qwen3.5-122B-Q5-MTP - Qwen3.5-122B-Q6-MTP"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf6qeb/qwen35122bq5mtp_qwen35122bq6mtp/
source: reddit-localllama
published_at: 2026-05-16T21:54:55+00:00
fetched_at: 2026-05-18T04:10:16.969890+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen3.5-122B MTP 量化版本（Q5 vs Q6）性能對比測試。Strix Halo 平台，llama.cpp rocm-mtp 後端。Q5-General 達 20.24 tok/s（4200 tokens），Q6-General 17.17 tok/s（3283 tokens）。Q5 比 Q6 快約 18%，但量化位深度與速度存儲權衡需按使用場景決定。"
key_points:
  - "Qwen3.5-122B-Q5-MTP-General：20.24 tok/s @ 4200 tokens；Prompt eval 408.99ms/19 tokens"
  - "Qwen3.5-122B-Q6-MTP-General：17.17 tok/s @ 3283 tokens；Prompt eval 488.39ms/19 tokens"
  - "Q5 vs Q6 速度優勢約 18%，量化位深與推理速度/VRAM 存儲的權衡"
tags: [qwen-3.5, mtp, quantization, performance-benchmark]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.5-122B-Q5-MTP - Qwen3.5-122B-Q6-MTP

Qwen3.5-122B MTP 量化版本（Q5 vs Q6）性能對比測試。Strix Halo 平台，llama.cpp rocm-mtp 後端。Q5-General 達 20.24 tok/s（4200 tokens），Q6-General 17.17 tok/s（3283 tokens）。Q5 比 Q6 快約 18%，但量化位深度與速度存儲權衡需按使用場景決定。

### 重點
- Qwen3.5-122B-Q5-MTP-General：20.24 tok/s @ 4200 tokens；Prompt eval 408.99ms/19 tokens
- Qwen3.5-122B-Q6-MTP-General：17.17 tok/s @ 3283 tokens；Prompt eval 488.39ms/19 tokens
- Q5 vs Q6 速度優勢約 18%，量化位深與推理速度/VRAM 存儲的權衡

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf6qeb/qwen35122bq5mtp_qwen35122bq6mtp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Qwen3.5-122B-Q5-MTP - Qwen3.5-122B-Q6-MTP

for anyone who cares... 😄 prompt = spen a 1000 tokens unsloth MTP models strix halo llama.cpp:server-rocm-mtp \ --spec-type draft-mtp \ --spec-draft-n-max 3 Qwen3.5-122B-Q5-MTP-General n_decoded = 100 tg = 29.77 t/s n_decoded = 179 tg = 27.95 t/s n_decoded = 254 tg = 26.80 t/s n_decoded = 4056 tg = 20.23 t/s n_decoded = 4120 tg = 20.23 t/s n_decoded = 4181 tg = 20.22 t/s prompt eval time = 408.99 ms / 19 tokens eval time = 207516.64 ms / 4200 tokens tg = 20.24 t/s Qwen3.5-122B-Q6-MTP-General n_decoded = 102 tg = 25.10 t/s n_decoded = 174 tg = 24.25 t/s n_decoded = 225 tg = 22.04 t/s n_decoded = 3193 tg = 17.27 t/s n_decoded = 3244 tg = 17.26 t/s n_decoded = 3281 tg = 17.18 t/s prompt eval time = 488.39 ms / 19 tokens eval time = 191156.72 ms / 3283 tokens tg = 17.17 t/s &#32; submitted by &#32; /u/Boring_Office [link] &#32; [comments]

</details>