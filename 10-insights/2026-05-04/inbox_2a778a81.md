---
id: inbox_2a778a81
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_2a778a81]]"
title: "Llama.cpp MTP support now in beta!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t3guzw/llamacpp_mtp_support_now_in_beta/
source: reddit-localllama
published_at: 2026-05-04T12:54:14+00:00
fetched_at: 2026-05-04T14:23:44.105366+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 宣布多 Token 預測（MTP）支援進入 beta 階段，感謝 Aman 等貢獻者推進該功能。目前支援 Qwen3.5 MTP，其他模型預期後續跟進。配合已成熟的張量並行（Tensor Parallel）功能，預期可消弭 llama.cpp 與 vLLM 在 Token 生成速度上的效能落差，推進本地推理優化。"
key_points:
  - "llama.cpp 新增 MTP（多 Token 預測）beta 支援，優化 Token 生成速度"
  - "首批支援 Qwen3.5 MTP，其他模型預期後續集成"
  - "結合張量並行成熟支援，預期縮小與 vLLM 推理性能的差距"
tags: [llama-cpp, mtp-inference, qwen, optimization]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Llama.cpp MTP support now in beta!

llama.cpp 宣布多 Token 預測（MTP）支援進入 beta 階段，感謝 Aman 等貢獻者推進該功能。目前支援 Qwen3.5 MTP，其他模型預期後續跟進。配合已成熟的張量並行（Tensor Parallel）功能，預期可消弭 llama.cpp 與 vLLM 在 Token 生成速度上的效能落差，推進本地推理優化。

### 重點
- llama.cpp 新增 MTP（多 Token 預測）beta 支援，優化 Token 生成速度
- 首批支援 Qwen3.5 MTP，其他模型預期後續集成
- 結合張量並行成熟支援，預期縮小與 vLLM 推理性能的差距

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t3guzw/llamacpp_mtp_support_now_in_beta/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Llama.cpp MTP support now in beta!

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3guzw/llamacpp_mtp_support_now_in_beta/"> <img alt="Llama.cpp MTP support now in beta!" src="https://external-preview.redd.it/Lr1I-xhkf0oKGlVfW5Dk1nUCX3CXo25GbKVGJcPuLr8.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=b498ac915c47be70d5aa3c028d8c73d36ebe8051" title="Llama.cpp MTP support now in beta!" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Happy to report that llama.cpp MTP support is now in beta, thanks to Aman (and all the others that have pushed the various issues in the meantime). This has the potential to actually get merged soon-ish. Currently contains support for Qwen3.5 MTP, but other models are likely to follow suit.</p> <p>Between this and the maturing tensor-parallel support, expect most performance gaps between llama.cpp and vLLM, at least when it comes to token generation speeds, to be erased.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/ilintar"> /u/ilintar </a> <br /> <span><a href="https://github.com/ggml-org/llama.cpp/pull/22673">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3guzw/llamacpp_mtp_support_now_in_beta/">[comments]</a></span> </td></tr></table>

</details>