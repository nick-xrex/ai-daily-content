---
id: inbox_961f1c9d
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-mistral-medium-3-5-128b-mlx-4bit-70-gb-ee3a]]"
title: "Mistral medium 3.5 128B, MLX 4bit, ~70 GB"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/
source: reddit-localllama
published_at: 2026-04-30T21:15:54+00:00
fetched_at: 2026-05-01T13:33:00.692661+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者發佈 Mistral Medium 3.5 128B 的 MLX 4bit 量化版本（約 70GB），包含視覺編碼器與推理模式（reasoning_effort 參數支持）、工具調用功能與 256K 上下文。但該轉換當前存在穩定性問題，官方明確不建議使用。在 M2 Max 96GB 機器上推理速度僅 5 token/s，後續可能需要進一步除錯。"
key_points:
  - "Mistral Medium 3.5 128B MLX 4bit 轉換，檔案大小 ~70GB"
  - "支援視覺編碼器（BF16 未量化）、推理模式、工具調用、256K 上下文"
  - "已知問題：模型本身穩定性差，M2 Max 推理僅 5 token/s，官方不建議使用"
tags: [mistral-medium-3.5, mlx-quantization, local-inference]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Mistral medium 3.5 128B, MLX 4bit, ~70 GB

開發者發佈 Mistral Medium 3.5 128B 的 MLX 4bit 量化版本（約 70GB），包含視覺編碼器與推理模式（reasoning_effort 參數支持）、工具調用功能與 256K 上下文。但該轉換當前存在穩定性問題，官方明確不建議使用。在 M2 Max 96GB 機器上推理速度僅 5 token/s，後續可能需要進一步除錯。

### 重點
- Mistral Medium 3.5 128B MLX 4bit 轉換，檔案大小 ~70GB
- 支援視覺編碼器（BF16 未量化）、推理模式、工具調用、256K 上下文
- 已知問題：模型本身穩定性差，M2 Max 推理僅 5 token/s，官方不建議使用

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/"> <img alt="Mistral medium 3.5 128B, MLX 4bit, ~70 GB" src="https://external-preview.redd.it/s66l-6BlBjHQa3FfpvWdfNprX1CbsTPe5-J06qg7rnI.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=51db278921d9c711f6c893c348b04c54c8371fff" title="Mistral medium 3.5 128B, MLX 4bit, ~70 GB" /> </a> </td><td> <!-- SC_OFF --><div class="md"><blockquote> <p>This model seems utterly broken for now. I do not recommend downloading or using it, unless you are planning to help troubleshoot it. This is not a problem with the conversion, but with the model itself.</p> </blockquote> <p>I converted Mistral medium 3.5 128B to MLX 4bit. Eagle model for speculative decoding is not yet supported by MLX.</p> <p>Vision encoder included (full BF16 unquantized. Thinking mode works (reasoning_effort=&quot;high&quot; gives you the [THINK]...[/THINK] chain), tool calling works, 256K context.</p> <p>There was a bug in mlx-vlm's mistral3 sanitize function: it wasn't stripping the model. prefix from vision tower and projector keys. This caused 438 parameters to be skipped. I patched it locally before converting. Details in the HF readme.</p> <p>I am getting ~5 tok/s on a 96 GB M2 Max. For sampling I recommend using temp 0.7 / top_p 0.95 / top_k 20 in reasoning mode, or temp 0.0–0.7 / top_p 0.8 for quick replies. Mistral recommends leaving repeat penalty disabled, but I am getting too many loops; I am not sure what the best value should be.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/ex-arman68"> /u/ex-arman68 </a> <br /> <span><a href="https://huggingface.co/froggeric/Mistral-Medium-3.5-128B-MLX-4bit">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/">[comments]</a></span> </td></tr></table>

</details>