---
id: inbox_efb1e280
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-mistral-medium-3-5-128b-ggufs-are-fixed-9f74]]"
title: "Mistral Medium 3.5 128b ggufs are fixed"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1ispj/mistral_medium_35_128b_ggufs_are_fixed/
source: reddit-localllama
published_at: 2026-05-02T07:11:50+00:00
fetched_at: 2026-05-03T01:59:12.943984+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Mistral Medium 3.5 128B 的 GGUF 量化版本存在廣泛推論缺陷，特別在長 context 場景輸出明顯劣化。Unsloth 已發布修正版 GGUF。修正後模型穩定性提升，即便提示詞格式不當亦不易崩塌為亂碼。根本原因涉及 YaRN 位置編碼參數誤設（mscale_all_dim）。"
key_points:
  - "GGUF 量化版本長期故障：所有舊版本均受影響，致使長 context 推論品質嚴重下降"
  - "修正版已發布可直接替換：Unsloth 提供新 GGUF，穩定性顯著改善"
  - "修正細節與 YaRN 參數誤設同根本原因（mscale_all_dim：1→0）"
tags: [mistral-medium-3.5, gguf, 128b, quantization-bug, long-context]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Mistral Medium 3.5 128b ggufs are fixed

Mistral Medium 3.5 128B 的 GGUF 量化版本存在廣泛推論缺陷，特別在長 context 場景輸出明顯劣化。Unsloth 已發布修正版 GGUF。修正後模型穩定性提升，即便提示詞格式不當亦不易崩塌為亂碼。根本原因涉及 YaRN 位置編碼參數誤設（mscale_all_dim）。

### 重點
- GGUF 量化版本長期故障：所有舊版本均受影響，致使長 context 推論品質嚴重下降
- 修正版已發布可直接替換：Unsloth 提供新 GGUF，穩定性顯著改善
- 修正細節與 YaRN 參數誤設同根本原因（mscale_all_dim：1→0）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1ispj/mistral_medium_35_128b_ggufs_are_fixed/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>All ggufs were broken, resulting in bad outputs, especially at long context.</p> <p>Anyway, it is fixed now: <a href="https://huggingface.co/unsloth/Mistral-Medium-3.5-128B-GGUF/discussions/1">https://huggingface.co/unsloth/Mistral-Medium-3.5-128B-GGUF/discussions/1</a></p> <p>Edit: Unsloth Announcement: <a href="https://huggingface.co/unsloth/Mistral-Medium-3.5-128B-GGUF/discussions/5">https://huggingface.co/unsloth/Mistral-Medium-3.5-128B-GGUF/discussions/5</a></p> <p>Edit2: From my experience it is A LOT more stable, even at short context. I messed up the prompt format before and it quickly devolved into gibberish. The updated version doesn't really mind.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Sunija_Dev"> /u/Sunija_Dev </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1ispj/mistral_medium_35_128b_ggufs_are_fixed/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1ispj/mistral_medium_35_128b_ggufs_are_fixed/">[comments]</a></span>

</details>