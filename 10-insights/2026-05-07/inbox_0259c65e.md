---
id: inbox_0259c65e
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-feat-add-mimo-v2-5-model-support-by-aess-7994]]"
title: "feat: Add Mimo v2.5 model support by AesSedai · Pull Request #22493 · ggml-org/llama.cpp"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t67lvx/feat_add_mimo_v25_model_support_by_aessedai_pull/
source: reddit-localllama
published_at: 2026-05-07T11:23:28+00:00
fetched_at: 2026-05-08T08:04:23.165159+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Xiaomi Mimo v2.5 模型已支援 llama.cpp。該模型採用稀疏混合專家（Sparse MoE）架構，具 310B 總參數（15B 激活），最大上下文 1M tokens，支援文本、圖像、視頻和音頻多模態。視覺編碼器為 729M 參數的 ViT（28 層：24 SWA + 4 Full），音頻編碼器為 261M 參數的 Transformer（24 層），多 token 預測層 329M 參數（3 層）。此集成使本地推理工具 llama.cpp 具有高效多模態處理能力。"
key_points:
  - "Sparse MoE 架構：310B 總參數 / 15B 激活，最大支援 1M token 上下文"
  - "多模態編碼器：729M ViT 視覺編碼（28 層）+ 261M 音頻 Transformer（24 層）+ 329M 多 token 預測"
  - "llama.cpp 集成使本地推理引擎支援高效多模態模型"
tags: [mimo-v2.5, sparse-moe, multimodal, llama.cpp]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## feat: Add Mimo v2.5 model support by AesSedai · Pull Request #22493 · ggml-org/llama.cpp

Xiaomi Mimo v2.5 模型已支援 llama.cpp。該模型採用稀疏混合專家（Sparse MoE）架構，具 310B 總參數（15B 激活），最大上下文 1M tokens，支援文本、圖像、視頻和音頻多模態。視覺編碼器為 729M 參數的 ViT（28 層：24 SWA + 4 Full），音頻編碼器為 261M 參數的 Transformer（24 層），多 token 預測層 329M 參數（3 層）。此集成使本地推理工具 llama.cpp 具有高效多模態處理能力。

### 重點
- Sparse MoE 架構：310B 總參數 / 15B 激活，最大支援 1M token 上下文
- 多模態編碼器：729M ViT 視覺編碼（28 層）+ 261M 音頻 Transformer（24 層）+ 329M 多 token 預測
- llama.cpp 集成使本地推理引擎支援高效多模態模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t67lvx/feat_add_mimo_v25_model_support_by_aessedai_pull/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

https://huggingface.co/XiaomiMiMo/MiMo-V2.5 Model Summary Architecture : Sparse MoE (Mixture of Experts), 310B total / 15B activated parameters Context Length : Up to 1M tokens Modalities : Text, Image, Video, Audio Vision Encoder : 729M-param ViT (28 layers: 24 SWA + 4 Full) Audio Encoder : 261M-param Audio Transformer (24 layers: 12 SWA + 12 Full) Multi-Token Prediction (MTP) : 329M parameters, 3 layers &#32; submitted by &#32; /u/jacek2023 [link] &#32; [comments]

</details>