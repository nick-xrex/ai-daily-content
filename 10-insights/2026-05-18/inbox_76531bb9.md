---
id: inbox_76531bb9
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_76531bb9]]"
title: "Quantizing MTP KV Cache = free lunch?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgk9y6/quantizing_mtp_kv_cache_free_lunch/
source: reddit-localllama
published_at: 2026-05-18T11:52:58+00:00
fetched_at: 2026-05-19T02:36:18.268725+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 對 Qwen 3.6-27B MTP（多令牌預測）draft 層的 KV cache 也可獨立量化（-cache-type-k-draft q8_0 -cache-type-v-draft q8_0），在 2× MI50 32GB @ PCIe 4.0 上測試，接受率維持 ~73.5% 無損，牆鐘時間基本無差（49.32s 對 49.46s），提供無性能損失的 VRAM 優化路徑。"
key_points:
  - "MTP draft KV cache 獨立量化：-cache-type-k-draft q8_0 -cache-type-v-draft q8_0"
  - "接受率穩定 ~73.5%，牆鐘時間無明顯差異（49.32s vs 49.46s）"
  - "支援 tensor parallelism，PCIe 4.0 x8 配置下可行"
tags: [mtp, kvache-quantization, llama-cpp, qwen, vram-optimization]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Quantizing MTP KV Cache = free lunch?

llama.cpp 對 Qwen 3.6-27B MTP（多令牌預測）draft 層的 KV cache 也可獨立量化（-cache-type-k-draft q8_0 -cache-type-v-draft q8_0），在 2× MI50 32GB @ PCIe 4.0 上測試，接受率維持 ~73.5% 無損，牆鐘時間基本無差（49.32s 對 49.46s），提供無性能損失的 VRAM 優化路徑。

### 重點
- MTP draft KV cache 獨立量化：-cache-type-k-draft q8_0 -cache-type-v-draft q8_0
- 接受率穩定 ~73.5%，牆鐘時間無明顯差異（49.32s vs 49.46s）
- 支援 tensor parallelism，PCIe 4.0 x8 配置下可行

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgk9y6/quantizing_mtp_kv_cache_free_lunch/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Quantizing MTP KV Cache = free lunch?

With the MTP llama.cpp implementation in the Qwen3.6/3.5 models more VRAM is required for the MTP layer. However, many people don't realize this layer comes with its own KV cache which can also be quantized: -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 edit: This is NOT quantizing the main KV Cache of the model So is it free lunch thus allowing us to fit slightly more context? From a short benchmark on Qwen3.6-27B-Q8_0 it certainly seems so: --spec-type draft-mtp --spec-draft-n-max 3 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1302, &quot;total_draft_accepted&quot;: 957, &quot;aggregate_accept_rate&quot;: 0.735, &quot;wall_s_total&quot;: 49.46 } --spec-type draft-mtp --spec-draft-n-max 3 -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1302, &quot;total_draft_accepted&quot;: 957, &quot;aggregate_accept_rate&quot;: 0.735, &quot;wall_s_total&quot;: 49.32 } Also tested with tensor parallelism: -sm tenor --spec-type draft-mtp --spec-draft-n-max 3 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1294, &quot;total_draft_accepted&quot;: 959, &quot;aggregate_accept_rate&quot;: 0.7411, &quot;wall_s_total&quot;: 38.42 } -sm tensor --spec-type draft-mtp --spec-draft-n-max 3 -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1294, &quot;total_draft_accepted&quot;: 959, &quot;aggregate_accept_rate&quot;: 0.7411, &quot;wall_s_total&quot;: 38.29 } Let me know if I'm coping or if you have other experiences. Tested on 2xMi50 32GBs @ PCIe 4.0 x 8 &#32; submitted by &#32; /u/legit_split_ [link] &#32; [comments]

</details>