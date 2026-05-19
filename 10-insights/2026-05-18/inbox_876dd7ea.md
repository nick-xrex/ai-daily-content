---
id: inbox_876dd7ea
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0201-reddit-localllama-lemonade-v10-5-1-an-mtp-rocm-7-13-quick-fc8d]]"
title: "Lemonade v10.5.1: an MTP + ROCm 7.13 quick start for Strix Halo"
url: https://www.reddit.com/r/LocalLLaMA/comments/1th0z6k/lemonade_v1051_an_mtp_rocm_713_quick_start_for/
source: reddit-localllama
published_at: 2026-05-18T20:55:54+00:00
fetched_at: 2026-05-19T02:09:43.219068+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lemonade SDK 升級至 v10.5.1，整合 MTP 和 ROCm 7.13，為 AMD Strix Halo 提供快速啟動方案。用戶可通過三個簡單命令完成：lemonade pull Qwen3.6-27B-MTP-GGUF、lemonade backends install llamacpp:rocm、lemonade load 模型，MTP 參數自動應用無需手動調參。同時修復 Fedora 43 支持。"
key_points:
  - "Lemonade v10.5.1 整合 MTP + ROCm 7.13，簡化 Strix Halo 部署流程"
  - "三行命令完成模型拉取、後端安裝、模型加載，自動應用 MTP 參數"
  - "修復 Fedora 43 支持，擴大相容作業系統範圍"
tags: [lemonade-sdk, mtp, rocm, strix-halo, deployment-tool]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Lemonade v10.5.1: an MTP + ROCm 7.13 quick start for Strix Halo

Lemonade SDK 升級至 v10.5.1，整合 MTP 和 ROCm 7.13，為 AMD Strix Halo 提供快速啟動方案。用戶可通過三個簡單命令完成：lemonade pull Qwen3.6-27B-MTP-GGUF、lemonade backends install llamacpp:rocm、lemonade load 模型，MTP 參數自動應用無需手動調參。同時修復 Fedora 43 支持。

### 重點
- Lemonade v10.5.1 整合 MTP + ROCm 7.13，簡化 Strix Halo 部署流程
- 三行命令完成模型拉取、後端安裝、模型加載，自動應用 MTP 參數
- 修復 Fedora 43 支持，擴大相容作業系統範圍

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1th0z6k/lemonade_v1051_an_mtp_rocm_713_quick_start_for/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Update to Lemonade v10.5.1, then: ``` Get the model lemonade pull Qwen3.6-27B-MTP-GGUF Get ROCm 7.13 lemonade backends install llamacpp:rocm Load the model (MTP args auto-applied) lemonade load Qwen3.6-27B-MTP-GGUF --llamacpp rocm --ctx-size 0 ``` Shown in the video taking a look in the mirror with the help of Pi agent. Github: https://github.com/lemonade-sdk/lemonade Discord: https://discord.gg/5xXzkMu8Zk PS. u/lucifer-vali fixed Fedora 43 support in this release as well :) &#32; submitted by &#32; /u/jfowers_amd [link] &#32; [comments]

</details>