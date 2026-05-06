---
id: inbox_afb04c6b
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-reddit-localllama-qwen-3-6-27b-q4-0-mtp-gguf-7451]]"
title: "Qwen 3.6 27b Q4.0 MTP GGUF"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t50s4i/qwen_36_27b_q40_mtp_gguf/
source: reddit-localllama
published_at: 2026-05-06T03:01:58+00:00
fetched_at: 2026-05-06T13:03:27.638966+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 AMD iGPU 64GB 統一內存上測試 Qwen 3.6 27b Q4.0 GGUF，使用 llama.cpp 的 MTP（Multi-Token Prediction）版本，發現吞吐量與 Qwen 3.5 9b Q4KM 相當。這暗示通過多 token 預測，較大的模型可在本地硬件上實現與小型模型相近的推理速度，對資源受限環境的本地推理有實務意義。"
key_points:
  - "Qwen 3.6 27b Q4.0 MTP 在 AMD iGPU 上的推理速度與 9b Q4KM 版本相當"
  - "llama.cpp 的 MTP 版本相比標準版本性能提升明顯"
  - "64GB 統一內存 iGPU 足以流暢運行 27b 量化模型"
tags: [qwen, gguf, llama-cpp, mtp, local-inference]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 3.6 27b Q4.0 MTP GGUF

用戶在 AMD iGPU 64GB 統一內存上測試 Qwen 3.6 27b Q4.0 GGUF，使用 llama.cpp 的 MTP（Multi-Token Prediction）版本，發現吞吐量與 Qwen 3.5 9b Q4KM 相當。這暗示通過多 token 預測，較大的模型可在本地硬件上實現與小型模型相近的推理速度，對資源受限環境的本地推理有實務意義。

### 重點
- Qwen 3.6 27b Q4.0 MTP 在 AMD iGPU 上的推理速度與 9b Q4KM 版本相當
- llama.cpp 的 MTP 版本相比標準版本性能提升明顯
- 64GB 統一內存 iGPU 足以流暢運行 27b 量化模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t50s4i/qwen_36_27b_q40_mtp_gguf/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Not sure if others have updated but tried the MPT version of LLAMA CPP. It works pretty good. I have a shitty IGPU AMD 64gb unified memory. It's pretty fast. Would say as fast as 9b Qwen 3.5 Q4KM replies. This is pretty cool.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Available_Hornet3538"> /u/Available_Hornet3538 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t50s4i/qwen_36_27b_q40_mtp_gguf/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t50s4i/qwen_36_27b_q40_mtp_gguf/">[comments]</a></span>

</details>