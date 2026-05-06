---
id: inbox_b00e325f
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-reddit-localllama-mtp-on-strix-halo-with-llama-cpp-pr-2267-ffa2]]"
title: "MTP on strix halo with llama.cpp (PR #22673)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/
source: reddit-localllama
published_at: 2026-05-05T22:26:41+00:00
fetched_at: 2026-05-06T10:26:51.819898+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在 AMD AI Max 395（128GB DDR5）上測試 llama.cpp PR #22673 的 MTP (Multi-Token Prediction) 新功能，運行 Qwen 3.6 35B A3B GGUF，配置 --spec-type mtp --spec-draft-n-max 3，推理吞吐量從 40-45 tok/s 提升至 60-80 tok/s（提升 33%-100%），prompt processing 無衰退；表示將擴展測試 Qwen 3.5 122B。"
key_points:
  - "MTP 在 llama.cpp Vulkan 實現下達成 60-80 tok/s，相較無 MTP 提升 33%-100%，prompt processing 無增加"
  - "spec-draft-n-max=3 參數在 36GB 模型大小下穩定運作，數學類任務吞吐量尤佳"
  - "消費級高端硬體（AI Max 395）可實現實用級加速，為 speculative decoding 的實踐驗證"
tags: [mtp, llama.cpp, qwen-3.6, speculative-decoding, amd-hardware]
topics: []
importance: 4
novelty: 5
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## MTP on strix halo with llama.cpp (PR #22673)

開發者在 AMD AI Max 395（128GB DDR5）上測試 llama.cpp PR #22673 的 MTP (Multi-Token Prediction) 新功能，運行 Qwen 3.6 35B A3B GGUF，配置 --spec-type mtp --spec-draft-n-max 3，推理吞吐量從 40-45 tok/s 提升至 60-80 tok/s（提升 33%-100%），prompt processing 無衰退；表示將擴展測試 Qwen 3.5 122B。

### 重點
- MTP 在 llama.cpp Vulkan 實現下達成 60-80 tok/s，相較無 MTP 提升 33%-100%，prompt processing 無增加
- spec-draft-n-max=3 參數在 36GB 模型大小下穩定運作，數學類任務吞吐量尤佳
- 消費級高端硬體（AI Max 395）可實現實用級加速，為 speculative decoding 的實踐驗證

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/"> <img alt="MTP on strix halo with llama.cpp (PR #22673)" src="https://preview.redd.it/xvtyf87u6ezg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=8ac472eeaa0c2957b855097981b9a8c631e92fbc" title="MTP on strix halo with llama.cpp (PR #22673)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I saw a post about incoming MTP support in llama.cpp so i tried it out on a AI max 395 with 128GB DDR5 8000:<br /> I rebuilt the radv container from <a href="https://github.com/kyuz0/amd-strix-halo-toolboxes">https://github.com/kyuz0/amd-strix-halo-toolboxes</a> with that PR : <a href="https://github.com/ggml-org/llama.cpp/pull/22673">https://github.com/ggml-org/llama.cpp/pull/22673</a><br /> I ran that GGUF : <a href="https://huggingface.co/am17an/Qwen3.6-35BA3B-MTP-GGUF/tree/main">https://huggingface.co/am17an/Qwen3.6-35BA3B-MTP-GGUF/tree/main</a> and added <code>--spec-type mtp --spec-draft-n-max 3</code></p> <p>Result : between 60 and 80 token/s from 40ish token/s without MTP (on the screen i was trying rocm but it's more like 40-45 token/s with vulkan) depending on the subject (some common math stuff seems to be the fastest). PP seems unchanged. The two GGUF on the screen capture are almost the same size : around 36GB each</p> <p>I have yet to try it on qwen 3.5 122B and there will be some tweaks to do with launch parameters but it's really impressive !!</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Edenar"> /u/Edenar </a> <br /> <span><a href="https://i.redd.it/xvtyf87u6ezg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/">[comments]</a></span> </td></tr></table>

</details>