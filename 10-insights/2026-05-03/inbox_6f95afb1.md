---
id: inbox_6f95afb1
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_6f95afb1]]"
title: "Mistral Medium 3.5 on AMD Strix Halo"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/
source: reddit-localllama
published_at: 2026-05-03T18:49:14+00:00
fetched_at: 2026-05-04T14:25:08.690086+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在 AMD Strix Halo 上運行 Mistral-Medium-3.5-128B 時遭遇嚴重性能瓶頸。針對 48K token 上下文 + 4K thinking token 的完整推理任務，耗時約 2 小時；詳細指標顯示提示詞評估速度為 9.76 tokens/秒，生成階段僅 2.1 tokens/秒。數據明確表明該硬體配置（整合顯卡）不適於該級別模型推理，驗證了消費級 APU 與高參數密集模型的不匹配。"
key_points:
  - "Mistral-Medium-3.5-128B 在 AMD Strix Halo 生成速度僅 2.1 tokens/秒，48K+4K token 任務耗時 ~2 小時"
  - "提示詞評估階段 9.76 tokens/秒，生成階段 2.1 tokens/秒，顯示顯卡頻寬為主要瓶頸"
  - "驗證結論：消費級 APU 不適合 128B 級模型推理，建議搭配獨立 GPU 或選擇小型模型"
tags: [mistral, amd-strix-halo, benchmark, performance-bottleneck]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Mistral Medium 3.5 on AMD Strix Halo

使用者在 AMD Strix Halo 上運行 Mistral-Medium-3.5-128B 時遭遇嚴重性能瓶頸。針對 48K token 上下文 + 4K thinking token 的完整推理任務，耗時約 2 小時；詳細指標顯示提示詞評估速度為 9.76 tokens/秒，生成階段僅 2.1 tokens/秒。數據明確表明該硬體配置（整合顯卡）不適於該級別模型推理，驗證了消費級 APU 與高參數密集模型的不匹配。

### 重點
- Mistral-Medium-3.5-128B 在 AMD Strix Halo 生成速度僅 2.1 tokens/秒，48K+4K token 任務耗時 ~2 小時
- 提示詞評估階段 9.76 tokens/秒，生成階段 2.1 tokens/秒，顯示顯卡頻寬為主要瓶頸
- 驗證結論：消費級 APU 不適合 128B 級模型推理，建議搭配獨立 GPU 或選擇小型模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Mistral Medium 3.5 on AMD Strix Halo

<!-- SC_OFF --><div class="md"><p>TLDR; it's slow as heck. Run overnight.</p> <p>I asked it a question about codebase architecture.</p> <p>For an end-to-end prompt of 48k tokens + 4k thinking tokens, it took about 2 hours.</p> <pre><code>llama-server -hf unsloth/Mistral-Medium-3. 5-128B-GGUF:UD-Q5_K_XL --temp 0.7 --host 0.0.0.0 --port 8080 -c 80000 -fa on -ngl 999 --no-context-shift -fit off --no-mmap -np 1 --mlock --cache-reuse 256 --chat-template-kwargs '{&quot;reasoning_effort&quot;:&quot;high&quot;}' --no-mmproj May 03 13:27:09 llama-server[6051]: prompt eval time = 4955501.32 ms / 48349 tokens ( 102.49 ms per token, 9.76 tokens per second) May 03 13:27:09 llama-server[6051]: eval time = 2652689.61 ms / 5583 tokens ( 475.14 ms per token, 2.10 tokens per second) </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Zc5Gwu"> /u/Zc5Gwu </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/">[comments]</a></span>

</details>