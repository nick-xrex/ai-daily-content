---
id: inbox_fe6c68c6
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_fe6c68c6]]"
title: "Gemma 4 MTP released"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4jq6h/gemma_4_mtp_released/
source: reddit-localllama
published_at: 2026-05-05T16:01:17+00:00
fetched_at: 2026-05-06T13:38:45.246992+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 發布 Gemma 4 的 Multi-Token Prediction (MTP) draft models，包括 31B、26B A4B、E4B、E2B 等規格。MTP 通過部署較小、較快的 draft model 來預測多個 token，target model 再並行驗證，可達到最高 2 倍的解碼加速，同時保證輸出品質與標準生成完全相同。這項技術特別適合低延遲和設備上應用，使用者可直接從 Hugging Face 下載預訓練的 MTP draft 模型。該技術基於 Speculative Decoding 流程，為推理效能優化提供了實用的開源方案。"
key_points:
  - "Multi-Token Prediction (MTP) 透過 speculative decoding 達到最高 2 倍解碼加速"
  - "Gemma 4 MTP draft models 提供多個規格（31B、26B A4B、E4B、E2B）"
  - "品質保證：加速同時確保輸出與標準生成完全一致"
tags: [gemma, multi-token-prediction, speculative-decoding, inference-optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemma 4 MTP released

Google 發布 Gemma 4 的 Multi-Token Prediction (MTP) draft models，包括 31B、26B A4B、E4B、E2B 等規格。MTP 通過部署較小、較快的 draft model 來預測多個 token，target model 再並行驗證，可達到最高 2 倍的解碼加速，同時保證輸出品質與標準生成完全相同。這項技術特別適合低延遲和設備上應用，使用者可直接從 Hugging Face 下載預訓練的 MTP draft 模型。該技術基於 Speculative Decoding 流程，為推理效能優化提供了實用的開源方案。

### 重點
- Multi-Token Prediction (MTP) 透過 speculative decoding 達到最高 2 倍解碼加速
- Gemma 4 MTP draft models 提供多個規格（31B、26B A4B、E4B、E2B）
- 品質保證：加速同時確保輸出與標準生成完全一致

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4jq6h/gemma_4_mtp_released/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Gemma 4 MTP released

<!-- SC_OFF --><div class="md"><p>Blog post:</p> <p><a href="https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/">https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/</a></p> <p>MTP draft models:</p> <p><a href="https://huggingface.co/google/gemma-4-31B-it-assistant">https://huggingface.co/google/gemma-4-31B-it-assistant</a></p> <p><a href="https://huggingface.co/google/gemma-4-26B-A4B-it-assistant">https://huggingface.co/google/gemma-4-26B-A4B-it-assistant</a></p> <p><a href="https://huggingface.co/google/gemma-4-E4B-it-assistant">https://huggingface.co/google/gemma-4-E4B-it-assistant</a></p> <p><a href="https://huggingface.co/google/gemma-4-E2B-it-assistant">https://huggingface.co/google/gemma-4-E2B-it-assistant</a></p> <p><em>This model card is for the Multi-Token Prediction (MTP) drafters for the Gemma 4 models. MTP is implemented by extending the base model with a smaller, faster draft model. When used in a Speculative Decoding pipeline, the draft model predicts several tokens ahead, which the target model then verifies in parallel. This results in significant decoding speedups (up to 2x) while guaranteeing the exact same quality as standard generation, making these checkpoints perfect for low-latency and on-device applications.</em></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/rerri"> /u/rerri </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4jq6h/gemma_4_mtp_released/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4jq6h/gemma_4_mtp_released/">[comments]</a></span>

</details>