---
id: inbox_e7345bd0
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_e7345bd0]]"
title: "NVFP4 Kimi2.6 and Kimi 2.5 released by Nvidia"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcxb77/nvfp4_kimi26_and_kimi_25_released_by_nvidia/
source: reddit-localllama
published_at: 2026-05-14T12:53:45+00:00
fetched_at: 2026-05-19T02:40:36.983784+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "NVIDIA 發布 Kimi-K2.6-NVFP4 和 Kimi-K2.5-NVFP4 量化版本（Moonshot AI 模型），使用 NVIDIA Model Optimizer 進行新格式量化。基準測試顯示 NVFP4 相比 INT4 基線在多數任務性能相當或略有提升（SciCode 52.6→54.4、Telecom 75.6→76.5）。測試參數：temperature=1.0、top_p=0.95、max tokens 128000。商用及非商用許可皆可。"
key_points:
  - "NVIDIA Model Optimizer 推出 NVFP4 量化格式，Kimi-K2.6 及 K2.5 均有發行"
  - "SciCode 基準從 INT4 的 52.6 提升至 NVFP4 的 54.4；Telecom 75.6→76.5"
  - "其他任務基準保持平穩或小幅改進（GPQA、τ2-Bench、MMMU Pro、IFBench）"
tags: [nvidia, kimi, nvfp4, quantization, model-optimizer]
topics: []
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## NVFP4 Kimi2.6 and Kimi 2.5 released by Nvidia

NVIDIA 發布 Kimi-K2.6-NVFP4 和 Kimi-K2.5-NVFP4 量化版本（Moonshot AI 模型），使用 NVIDIA Model Optimizer 進行新格式量化。基準測試顯示 NVFP4 相比 INT4 基線在多數任務性能相當或略有提升（SciCode 52.6→54.4、Telecom 75.6→76.5）。測試參數：temperature=1.0、top_p=0.95、max tokens 128000。商用及非商用許可皆可。

### 重點
- NVIDIA Model Optimizer 推出 NVFP4 量化格式，Kimi-K2.6 及 K2.5 均有發行
- SciCode 基準從 INT4 的 52.6 提升至 NVFP4 的 54.4；Telecom 75.6→76.5
- 其他任務基準保持平穩或小幅改進（GPQA、τ2-Bench、MMMU Pro、IFBench）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcxb77/nvfp4_kimi26_and_kimi_25_released_by_nvidia/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# NVFP4 Kimi2.6 and Kimi 2.5 released by Nvidia

The NVIDIA Kimi-K2.6-NVFP4 model is the quantized version of the Moonshot AI's Kimi-K2.6 model, which is an auto-regressive language model that uses an optimized transformer architecture. For more information, please check here . The NVIDIA Kimi-K2.6 NVFP4 model is quantized with Model Optimizer . This model is ready for commercial/non-commercial use. The accuracy benchmark results are presented in the table below: Precision GPQA Diamond SciCode τ2-Bench Telecom MMMU Pro AA-LCR IFBench Baseline (INT4) 90.9 52.6 98.2 75.6 71.0 73.9 NVFP4 90.4 54.4 98.0 76.5 71.8 73.9 Baseline: Kimi-K2.6 in its native INT4 format. Benchmarked with temperature=1.0, top_p=0.95, max num tokens 128000. Links: https://huggingface.co/nvidia/Kimi-K2.6-NVFP4 https://huggingface.co/nvidia/Kimi-K2.5-NVFP4 &#32; submitted by &#32; /u/Opening-Broccoli9190 [link] &#32; [comments]

</details>