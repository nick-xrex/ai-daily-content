---
id: inbox_a7c9d37a
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_a7c9d37a]]"
title: "Accelerating Gemma 4: faster inference with multi-token prediction drafters"
url: https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/
source: hackernews
published_at: 2026-05-05T16:14:17+00:00
fetched_at: 2026-05-06T13:33:53.288796+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 发布 Gemma 4 多令牌预测（MTP）加速器，通过推测解码架构实现高达 3 倍推理速度提升，无输出质量劣化。MTP 通过轻量级草稿模型与重量级目标模型配对，利用闲置计算资源并行预测多个令牌，再由目标模型统一验证。在 NVIDIA RTX PRO 6000 上，Gemma 4 26B 模型从标准推理的每秒 N tokens 提升到 MTP 模式下的 2N tokens。适用于编码助手、自主规划 agents、离线应用等低延迟场景，尤其在消费级硬件和边设备上效果显著。"
key_points:
  - "推测解码（Speculative Decoding）技术：草稿模型在目标模型生成 1 个 token 的时间内预测多个 token，目标模型并行验证，实现 3 倍速度提升"
  - "Gemma 4 26B/31B Dense 和 E2B/E4B 边缘模型均支持 MTP；草稿模型复用目标模型激活值和 KV cache，避免重复计算上下文"
  - "零质量损失：由于最终验证由原始 Gemma 4 完成，推理结果与标准模式完全相同"
tags: [gemma-4, speculative-decoding, inference-optimization, mtp, latency-reduction]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Accelerating Gemma 4: faster inference with multi-token prediction drafters

Google 发布 Gemma 4 多令牌预测（MTP）加速器，通过推测解码架构实现高达 3 倍推理速度提升，无输出质量劣化。MTP 通过轻量级草稿模型与重量级目标模型配对，利用闲置计算资源并行预测多个令牌，再由目标模型统一验证。在 NVIDIA RTX PRO 6000 上，Gemma 4 26B 模型从标准推理的每秒 N tokens 提升到 MTP 模式下的 2N tokens。适用于编码助手、自主规划 agents、离线应用等低延迟场景，尤其在消费级硬件和边设备上效果显著。

### 重點
- 推测解码（Speculative Decoding）技术：草稿模型在目标模型生成 1 个 token 的时间内预测多个 token，目标模型并行验证，实现 3 倍速度提升
- Gemma 4 26B/31B Dense 和 E2B/E4B 边缘模型均支持 MTP；草稿模型复用目标模型激活值和 KV cache，避免重复计算上下文
- 零质量损失：由于最终验证由原始 Gemma 4 完成，推理结果与标准模式完全相同

**原文：** [hackernews](https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Accelerating Gemma 4: faster inference with multi-token prediction drafters

</details>