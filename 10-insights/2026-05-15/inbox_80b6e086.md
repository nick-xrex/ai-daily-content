---
id: inbox_80b6e086
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_80b6e086]]"
title: "Why My Coding Assistant Started Replying in Korean When I Typed Chinese"
url: https://towardsdatascience.com/why-my-coding-assistant-started-replying-in-korean-when-i-typed-chinese/
source: medium-towards-data-science
published_at: 2026-05-15T13:30:00+00:00
fetched_at: 2026-05-18T03:50:53.759529+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Medium 文章分析编码助手的一个跨语言现象：输入中文 prompt 却收到韩文回复。通过嵌入空间调查，揭示代码词汇对语言输出的影响机制。代码相关的词汇在嵌入空间中与特定语言（如韩文）的接近度，导致预期之外的语言转换。这一现象说明代码词汇会重塑语言模型的多语言响应倾向，多语言编码助手应防范此类边界情况。"
key_points:
  - "现象：中文输入 → 韩文输出，揭示编码助手在多语言场景中的隐藏行为边界"
  - "根本机制：代码词汇在嵌入空间中的分布与自然语言关联存在偏差，导致语言预测方向改变"
  - "设计启示：多语言编码助手需要正视代码词汇对嵌入空间的重塑效应，在设计多语言支持时需要额外的约束机制"
tags: [embedding-space, multilingual, language-bias, coding-assistant, interpretability]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Why My Coding Assistant Started Replying in Korean When I Typed Chinese

Medium 文章分析编码助手的一个跨语言现象：输入中文 prompt 却收到韩文回复。通过嵌入空间调查，揭示代码词汇对语言输出的影响机制。代码相关的词汇在嵌入空间中与特定语言（如韩文）的接近度，导致预期之外的语言转换。这一现象说明代码词汇会重塑语言模型的多语言响应倾向，多语言编码助手应防范此类边界情况。

### 重點
- 现象：中文输入 → 韩文输出，揭示编码助手在多语言场景中的隐藏行为边界
- 根本机制：代码词汇在嵌入空间中的分布与自然语言关联存在偏差，导致语言预测方向改变
- 设计启示：多语言编码助手需要正视代码词汇对嵌入空间的重塑效应，在设计多语言支持时需要额外的约束机制

**原文：** [medium-towards-data-science](https://towardsdatascience.com/why-my-coding-assistant-started-replying-in-korean-when-i-typed-chinese/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Why My Coding Assistant Started Replying in Korean When I Typed Chinese

From a Chinese prompt to a Korean response: an embedding-space investigation into how code vocabulary reshapes language 
 The post Why My Coding Assistant Started Replying in Korean When I Typed Chinese appeared first on Towards Data Science .

</details>