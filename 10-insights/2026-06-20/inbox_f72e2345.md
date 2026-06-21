---
id: inbox_f72e2345
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_f72e2345]]"
title: "Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic"
url: https://www.infoq.com/news/2026/06/bedrock-fable-5-data-sharing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-20T09:03:00+00:00
fetched_at: 2026-06-21T02:31:17.628385+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Fable 5 和 Mythos 5 在 Amazon Bedrock 上運行需強制啟用 provider_data_share 設定，要求將所有 prompts 和推理結果 outputs 發送至 Anthropic 進行 30 天保留與人工審查。這項新政策打破了 Bedrock 以往的數據邊界保護慣例，過去模型的推理數據始終留在 AWS 內部邊界。發布僅三天後，Anthropic 突然基於美國出口管制合規理由要求 AWS 撤銷兩個模型的訪問權限。此事件暴露了雲廠商與基礎模型廠商間的數據治理衝突與潛在的地緣政治壓力。"
key_points:
  - "Fable 5/Mythos 5 強制要求 provider_data_share，prompt 和 output 發送 Anthropic 進行 30 天保留並人工審查"
  - "打破 Bedrock 先前的數據邊界保護，推理數據不再留在 AWS 內部，引發隱私和合規顧慮"
  - "發布 3 天後 Anthropic 以出口管制為由要求 AWS 撤銷兩模型訪問，暴露雲廠商-模型廠商間的政治和政策衝突"
tags: [claude-fable-5, bedrock, data-sharing, export-control, anthropic]
topics: [foundation_models.claude]
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic

Claude Fable 5 和 Mythos 5 在 Amazon Bedrock 上運行需強制啟用 provider_data_share 設定，要求將所有 prompts 和推理結果 outputs 發送至 Anthropic 進行 30 天保留與人工審查。這項新政策打破了 Bedrock 以往的數據邊界保護慣例，過去模型的推理數據始終留在 AWS 內部邊界。發布僅三天後，Anthropic 突然基於美國出口管制合規理由要求 AWS 撤銷兩個模型的訪問權限。此事件暴露了雲廠商與基礎模型廠商間的數據治理衝突與潛在的地緣政治壓力。

### 重點
- Fable 5/Mythos 5 強制要求 provider_data_share，prompt 和 output 發送 Anthropic 進行 30 天保留並人工審查
- 打破 Bedrock 先前的數據邊界保護，推理數據不再留在 AWS 內部，引發隱私和合規顧慮
- 發布 3 天後 Anthropic 以出口管制為由要求 AWS 撤銷兩模型訪問，暴露雲廠商-模型廠商間的政治和政策衝突

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/bedrock-fable-5-data-sharing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Fable 5 on Bedrock Requires Sharing Inference Data with Anthropic

Using Claude Fable 5 or Mythos 5 on Amazon Bedrock requires opting into provider_data_share, sending prompts and outputs to Anthropic for 30-day retention with human review. Previous Bedrock models kept inference data inside the AWS boundary. Three days after launch, Anthropic asked AWS to revoke access to both models citing US export control compliance. By Steef-Jan Wiggers

</details>