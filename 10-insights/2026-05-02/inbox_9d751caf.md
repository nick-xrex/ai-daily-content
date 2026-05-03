---
id: inbox_9d751caf
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-kv-cache-quantization-ignorance-or-malic-4e51]]"
title: "Kv cache quantization: ignorance, or malice?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/
source: reddit-localllama
published_at: 2026-05-02T15:34:22+00:00
fetched_at: 2026-05-03T02:00:28.278360+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者質疑 KV 快取量化在實務上的合理性：在雙 3090 上運行 Qwen-3.6 27B FP8 量化版本於多代理編碼工作負載時，發現 FP8 KV 快取導致工具呼叫失敗、推理邏輯錯誤等問題，改用 FP16 KV 快取後品質大幅改善。作者質疑為何業界推廣 KV 量化，認為對複雜代理系統不值得權衡。"
key_points:
  - "實測結果：FP8 KV 快取在 Qwen-3.6 27B 上造成微妙推理失敗（工具呼叫、邏輯錯誤）"
  - "FP16 KV 快取在兩張 3090 上無記憶體瓶頸，性能損失可接受"
  - "質疑 TurboQuant 等量化方案對生產級代理工作負載的適用性"
tags: [kv-cache-quantization, qwen-3.6, quality-tradeoff, agentic-workloads, fp8-vs-fp16]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Kv cache quantization: ignorance, or malice?

使用者質疑 KV 快取量化在實務上的合理性：在雙 3090 上運行 Qwen-3.6 27B FP8 量化版本於多代理編碼工作負載時，發現 FP8 KV 快取導致工具呼叫失敗、推理邏輯錯誤等問題，改用 FP16 KV 快取後品質大幅改善。作者質疑為何業界推廣 KV 量化，認為對複雜代理系統不值得權衡。

### 重點
- 實測結果：FP8 KV 快取在 Qwen-3.6 27B 上造成微妙推理失敗（工具呼叫、邏輯錯誤）
- FP16 KV 快取在兩張 3090 上無記憶體瓶頸，性能損失可接受
- 質疑 TurboQuant 等量化方案對生產級代理工作負載的適用性

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I run Qwen-3.6 27B with the FP8 safetensors on vllm for long-horizon agentic coding harness workloads with high context window and concurrent sub-agents. On two 3090s that aren’t used for anything else, it seems reasonable to expect a good balance between speed and reliability. I want to bring up a particular point of contention regarding this optimization process. I have extensive software engineering background but am relatively new to this so feel free to correct me if I’m not on the right track.</p> <p>It seems like conventional wisdom is that you shouldn’t quantize kv cache. In my experience, with my specific workloads, that remains true: with kv at fp8, I see many subtle mistakes, tool calling issues, and just plain bad reasoning. The performance is dramatically higher when I pin it at 16 bit.</p> <p>So with that in mind why do I keep seeing people gesturing at this like it’s a serious solution? I guess I can see it if it’d just low stakes chatbot stuff. But why would anyone run anything serious at anything less than full sized kv? I keep seeing stuff about turboquant as well and haven’t tried it but from what I understood, it seems like it comes with an intelligence hit too.</p> <p>So am I understanding correctly?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/wombweed"> /u/wombweed </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/">[comments]</a></span>

</details>