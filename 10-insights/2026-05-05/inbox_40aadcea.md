---
id: inbox_40aadcea
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/0819-reddit-localllama-vllm-just-merged-turboquant-fix-for-qwen-3fc4]]"
title: "vLLM Just Merged TurboQuant Fix for Qwen 3.5+"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/
source: reddit-localllama
published_at: 2026-05-05T00:30:24+00:00
fetched_at: 2026-05-05T08:38:51.516324+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "vLLM 合併 PR#39931 修復了 TurboQuant 對 Qwen 3.5+ 和 Qwen 3.6 的支援問題，解決之前因 Mamba 層導致的「Not Implemented」錯誤。用戶可使用 `--kv-cache-dtype turboquant_4bit_nc` 等選項，支援 turboquant_k8v4、turboquant_k3v4_nc、turboquant_3bit_nc 等多種量化配置，已在 Qwen 3.6 27B 測試通過。使用 `--enable-chunked-prefill` 時需搭配 `--max-num-batched-tokens 4096` 以解決 Mamba 對齊問題。"
key_points:
  - "vLLM TurboQuant 對 Qwen 3.5+/3.6 的 Mamba 層支援已修復，可正常使用"
  - "可用量化選項：turboquant_4bit_nc、turboquant_k8v4、turboquant_3bit_nc 等多種配置"
  - "chunked-prefill 模式需搭配 max-num-batched-tokens 4096 避免 Mamba 對齊錯誤"
tags: [vllm-0.20.1, turboquant-4bit-nc, qwen-3.6-27b, mamba-layers, bug-fix]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## vLLM Just Merged TurboQuant Fix for Qwen 3.5+

vLLM 合併 PR#39931 修復了 TurboQuant 對 Qwen 3.5+ 和 Qwen 3.6 的支援問題，解決之前因 Mamba 層導致的「Not Implemented」錯誤。用戶可使用 `--kv-cache-dtype turboquant_4bit_nc` 等選項，支援 turboquant_k8v4、turboquant_k3v4_nc、turboquant_3bit_nc 等多種量化配置，已在 Qwen 3.6 27B 測試通過。使用 `--enable-chunked-prefill` 時需搭配 `--max-num-batched-tokens 4096` 以解決 Mamba 對齊問題。

### 重點
- vLLM TurboQuant 對 Qwen 3.5+/3.6 的 Mamba 層支援已修復，可正常使用
- 可用量化選項：turboquant_4bit_nc、turboquant_k8v4、turboquant_3bit_nc 等多種配置
- chunked-prefill 模式需搭配 max-num-batched-tokens 4096 避免 Mamba 對齊錯誤

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Previously it was throwing a 'Not Implemented' error due to Mamba layers. Going to test it now!</p> <p><a href="https://github.com/vllm-project/vllm/pull/39931">https://github.com/vllm-project/vllm/pull/39931</a></p> <p>Edit: Works with Qwen 3.6, tested with 27B<br /> Can be used with argument;</p> <pre><code>--kv-cache-dtype turboquant_4bit_nc </code></pre> <p>Other available options;</p> <ul> <li>turboquant_k8v4</li> <li>turboquant_4bit_nc</li> <li>turboquant_k3v4_nc</li> <li>turboquant_3bit_nc</li> </ul> <p>When running with <code>--enable-chunked-prefill</code> it complained about mamba align, you just need to have more batched tokens than the value that error gives. I used 4096 to fix. <code>--max-num-batched-tokens 4096</code></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/havenoammo"> /u/havenoammo </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/">[comments]</a></span>

</details>