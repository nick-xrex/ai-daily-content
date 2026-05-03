---
id: inbox_7a04a488
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-unsloth-solved-bug-in-mistral-medium-3-5-3887]]"
title: "Unsloth solved bug in Mistral Medium 3.5 implementation"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1itn1/unsloth_solved_bug_in_mistral_medium_35/
source: reddit-localllama
published_at: 2026-05-02T07:13:13+00:00
fetched_at: 2026-05-03T01:59:12.941178+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Unsloth 與 Mistral 合作修復 Mistral Medium 3.5 推論錯誤。根本原因：YaRN 位置編碼解析 quirk，導致 mscale_all_dim 參數被誤讀（應為 0、實為 1），影響 transformers/llama.cpp 等多數實現。該 bug 致使長 context 輸出嚴重劣化。已發布修正版 GGUF，另修復 mmproj 檔案生成問題。"
key_points:
  - "mscale_all_dim 參數誤設：設為 0 而非 1 解決 YaRN 解析 quirk，直接影響 long-context 推論品質"
  - "跨實現通用 bug：transformers、llama.cpp、Unsloth 等均受影響；Unsloth 提供修正版 GGUF 可直接使用"
tags: [mistral-medium-3.5, gguf, yarn-encoding, inference-bug, mscale-parameter]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Unsloth solved bug in Mistral Medium 3.5 implementation

Unsloth 與 Mistral 合作修復 Mistral Medium 3.5 推論錯誤。根本原因：YaRN 位置編碼解析 quirk，導致 mscale_all_dim 參數被誤讀（應為 0、實為 1），影響 transformers/llama.cpp 等多數實現。該 bug 致使長 context 輸出嚴重劣化。已發布修正版 GGUF，另修復 mmproj 檔案生成問題。

### 重點
- mscale_all_dim 參數誤設：設為 0 而非 1 解決 YaRN 解析 quirk，直接影響 long-context 推論品質
- 跨實現通用 bug：transformers、llama.cpp、Unsloth 等均受影響；Unsloth 提供修正版 GGUF 可直接使用

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1itn1/unsloth_solved_bug_in_mistral_medium_35/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p><a href="https://unsloth.ai/docs/models/mistral-3.5">https://unsloth.ai/docs/models/mistral-3.5</a></p> <p>&quot;May 1, 2026 Update: We worked with Mistral to fix Mistral Medium 3.5 inference affecting some implementations, and released updated GGUFs with the fix (NOT related to Unsloth or our quants). The issue was caused by a YaRN parsing quirk affecting several implementations, including transformers and llama.cpp. Changing mscale_all_dim from 1 to 0 resolved it. We also fixed mmproj files not being generated correctly.&quot;</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Snail_Inference"> /u/Snail_Inference </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1itn1/unsloth_solved_bug_in_mistral_medium_35/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1itn1/unsloth_solved_bug_in_mistral_medium_35/">[comments]</a></span>

</details>