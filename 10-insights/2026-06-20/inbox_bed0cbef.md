---
id: inbox_bed0cbef
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_bed0cbef]]"
title: "Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic"
url: https://www.infoq.com/news/2026/06/bedrock-fable-5-data-sharing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-20T09:03:00+00:00
fetched_at: 2026-06-21T02:30:07.559920+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Amazon Bedrock 上的 Claude Fable 5 和 Mythos 5 要求用戶主動同意 `provider_data_share` 機制，將提示和回應發送至 Anthropic 進行 30 天保留與人工審查，打破了前代 Bedrock 模型在 AWS 邊界內處理推理數據的慣例。更令人矚目的是，發布僅三天後，Anthropic 即請求 AWS 撤銷兩個模型的訪問權限，官方理由為美國出口管制合規。此事件揭示了監管環境對 AI 模型可用性的直接衝擊，以及廠商間的數據政策衝突如何影響產品戰略。"
key_points:
  - "Bedrock Fable 5/Mythos 5 新增強制 opt-in data-share：提示及回應送 Anthropic 30 天保留、人工審查，打破數據駐留邊界"
  - "發布 3 天後因美國出口管制合規，Anthropic 主動請求 AWS 撤銷訪問權，導致模型可用性中斷"
  - "事件展示出口管制政策和廠商數據政策衝突如何直接影響用戶訪問和多廠商信任決策"
tags: [claude, bedrock, data-sharing, export-control, privacy]
topics: [foundation_models.claude]
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic

Amazon Bedrock 上的 Claude Fable 5 和 Mythos 5 要求用戶主動同意 `provider_data_share` 機制，將提示和回應發送至 Anthropic 進行 30 天保留與人工審查，打破了前代 Bedrock 模型在 AWS 邊界內處理推理數據的慣例。更令人矚目的是，發布僅三天後，Anthropic 即請求 AWS 撤銷兩個模型的訪問權限，官方理由為美國出口管制合規。此事件揭示了監管環境對 AI 模型可用性的直接衝擊，以及廠商間的數據政策衝突如何影響產品戰略。

### 重點
- Bedrock Fable 5/Mythos 5 新增強制 opt-in data-share：提示及回應送 Anthropic 30 天保留、人工審查，打破數據駐留邊界
- 發布 3 天後因美國出口管制合規，Anthropic 主動請求 AWS 撤銷訪問權，導致模型可用性中斷
- 事件展示出口管制政策和廠商數據政策衝突如何直接影響用戶訪問和多廠商信任決策

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/bedrock-fable-5-data-sharing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic

Using Claude Fable 5 or Mythos 5 on Amazon Bedrock requires opting into provider_data_share, sending prompts and outputs to Anthropic for 30-day retention with human review. Previous Bedrock models kept inference data inside the AWS boundary. Three days after launch, Anthropic asked AWS to revoke access to both models citing US export control compliance. By Steef-Jan Wiggers

</details>