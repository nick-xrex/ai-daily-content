---
id: inbox_57a0e57c
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_57a0e57c]]"
title: "Introducing cyankiwi AWQ 4-bit Quantization — 26.05 update"
url: https://www.reddit.com/r/LocalLLaMA/comments/1td7gp8/introducing_cyankiwi_awq_4bit_quantization_2605/
source: reddit-localllama
published_at: 2026-05-14T18:49:21+00:00
fetched_at: 2026-05-18T03:59:24.989410+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "cyankiwi 發佈 AWQ 26.05 新版本，引入聯合優化方法：同時擬合 per-channel 尺度與量化範圍（傳統 AWQ 分步進行，造成品質缺口）。在 Llama-3 系列模型（3B、8B、70B）上與其他主流 4-bit 方法比較，cyankiwi AWQ 在所有三個模型上達成最低 KL Divergence（與 BF16 baseline 比較），品質領先 30–40%。Llama-3.1-8B-Instruct 上，cyankiwi AWQ KLD 0.00478 優於 GPTQ (0.00729) 與 BNB NF4 (0.00769)；Llama-3.3-70B 上優勢更明顯 (0.02826 vs 0.04444–0.09272)。聯合優化方法揭示量化尺度與範圍並非獨立，同時優化可顯著降低重建誤差。"
key_points:
  - "聯合優化：同時擬合 scales + quantization ranges 針對重建誤差目標，克服分步優化的品質缺口"
  - "Llama-3.1-8B 上 KLD 0.00478 (cyankiwi AWQ) vs 0.00729 (GPTQ) vs 0.00769 (BNB NF4)，領先 34–36%；70B 上領先幅度達 42%"
  - "所有測試模型 (3B/8B/70B) 上均為最低 KLD，顯示方法通用性和 4-bit 量化品質的新天花板"
tags: [quantization, awq, llama-3, compression, optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Introducing cyankiwi AWQ 4-bit Quantization — 26.05 update

cyankiwi 發佈 AWQ 26.05 新版本，引入聯合優化方法：同時擬合 per-channel 尺度與量化範圍（傳統 AWQ 分步進行，造成品質缺口）。在 Llama-3 系列模型（3B、8B、70B）上與其他主流 4-bit 方法比較，cyankiwi AWQ 在所有三個模型上達成最低 KL Divergence（與 BF16 baseline 比較），品質領先 30–40%。Llama-3.1-8B-Instruct 上，cyankiwi AWQ KLD 0.00478 優於 GPTQ (0.00729) 與 BNB NF4 (0.00769)；Llama-3.3-70B 上優勢更明顯 (0.02826 vs 0.04444–0.09272)。聯合優化方法揭示量化尺度與範圍並非獨立，同時優化可顯著降低重建誤差。

### 重點
- 聯合優化：同時擬合 scales + quantization ranges 針對重建誤差目標，克服分步優化的品質缺口
- Llama-3.1-8B 上 KLD 0.00478 (cyankiwi AWQ) vs 0.00729 (GPTQ) vs 0.00769 (BNB NF4)，領先 34–36%；70B 上領先幅度達 42%
- 所有測試模型 (3B/8B/70B) 上均為最低 KLD，顯示方法通用性和 4-bit 量化品質的新天花板

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1td7gp8/introducing_cyankiwi_awq_4bit_quantization_2605/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Introducing cyankiwi AWQ 4-bit Quantization — 26.05 update

In standard AWQ, per-channel scales and quantization ranges are picked in separate steps: scales first, then the quantization parameters. But they're not independent, i.e., the rounding error from one depends on the choice of the other, so optimizing them in sequence leaves quality on the table. Our cyankiwi AWQ 26.05 update jointly fits scales and quantization ranges against a reconstruction objective. We benchmarked cyankiwi AWQ 26.05 update against every major 4-bit method on Llama-3 as examples, measuring KL Divergence vs the BF16 baseline on GPQA Diamond responses. Result: cyankiwi posts the lowest KLD on all three base models. Lower is better. Llama-3.2-3B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.2-3B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.00510 unsloth/Llama-3.2-3B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.00785 unsloth/Llama-3.2-3B-Instruct-bnb-4bit BNB NF4 0.00896 nvidia/Meta-Llama-3.2-3B-Instruct-ONNX-INT4 AWQ INT4 0.01494 casperhansen/llama-3.2-3b-instruct-awq AWQ INT4 0.02437 Llama-3.1-8B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.1-8B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.00478 RedHatAI/Meta-Llama-3.1-8B-Instruct-quantized.w4a16 GPTQ INT4 0.00729 unsloth/Meta-Llama-3.1-8B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.00769 unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit BNB NF4 0.00835 RedHatAI/Llama-3.1-8B-Instruct-NVFP4 SmoothQuant NVFP4 0.01059 nvidia/Llama-3.1-8B-Instruct-NVFP4 NVFP4 0.01190 Llama-3.3-70B-Instruct Quantized Model Method KLD cyankiwi/Llama-3.3-70B-Instruct-AWQ-INT4 cyankiwi AWQ INT4 0.02826 unsloth/Llama-3.3-70B-Instruct-unsloth-bnb-4bit unsloth BNB NF4 0.04444 casperhansen/llama-3.3-70b-instruct-awq AWQ INT4 0.04859 unsloth/Llama-3.3-70B-Instruct-bnb-4bit BNB NF4 0.06879 nvidia/Llama-3.3-70B-Instruct-NVFP4 NVFP4 0.08307 RedHatAI/Llama-3.3-70B-Instruct-quantized.w4a16 GPTQ INT4 0.09272 https://preview.redd.it/uicubbg6951h1.png?width=6400&amp;format=png&amp;auto=webp&amp;s=2f7f1d4e46c9953f00c68518b3c2aa058fc34e32 &#32; submitted by &#32; /u/_cpatonn [link] &#32; [comments]

</details>