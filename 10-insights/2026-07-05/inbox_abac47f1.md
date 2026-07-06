---
id: inbox_abac47f1
date: 2026-07-05
source_ref: "[[00-inbox/2026-07-05/2200-infoq-main-claude-reaches-ga-on-microsoft-foundry-e-49b4]]"
title: "Claude Reaches GA on Microsoft Foundry: European Enterprises Cannot Deploy It"
url: https://www.infoq.com/news/2026/07/claude-foundry-ga-europe/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-05T08:13:00+00:00
fetched_at: 2026-07-05T22:10:52.151709+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude 模型在 Microsoft Foundry 上已達正式版本(GA)，提供 Azure 原生帳單和治理功能，但存在重大限制：缺乏歐洲資料區域。Anthropic 官方文件明確確認資料駐留保證僅適用於 Bedrock 和 Vertex AI，Foundry 不在此列。來自銀行和醫療保健等受規管產業的歐洲企業已報告該服務未經批准用於生產環境。這代表 Claude 在雲端平台的部署存在重要的地理和合規限制，對歐洲企業造成重大障礙，需要轉向 Bedrock 或 Vertex AI 以滿足資料駐留要求。"
key_points:
  - "Claude 在 Microsoft Foundry GA，但官方文件明確：Foundry 無資料駐留保證（Bedrock/Vertex AI 有）"
  - "歐洲銀行、醫療等受規管行業無法用於生產部署，違反 GDPR 等合規要求"
  - "企業若需歐洲資料駐留，必須改用 AWS Bedrock 或 Google Vertex AI"
tags: [claude, microsoft-foundry, data-residency, eu-compliance]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Reaches GA on Microsoft Foundry: European Enterprises Cannot Deploy It

Claude 模型在 Microsoft Foundry 上已達正式版本(GA)，提供 Azure 原生帳單和治理功能，但存在重大限制：缺乏歐洲資料區域。Anthropic 官方文件明確確認資料駐留保證僅適用於 Bedrock 和 Vertex AI，Foundry 不在此列。來自銀行和醫療保健等受規管產業的歐洲企業已報告該服務未經批准用於生產環境。這代表 Claude 在雲端平台的部署存在重要的地理和合規限制，對歐洲企業造成重大障礙，需要轉向 Bedrock 或 Vertex AI 以滿足資料駐留要求。

### 重點
- Claude 在 Microsoft Foundry GA，但官方文件明確：Foundry 無資料駐留保證（Bedrock/Vertex AI 有）
- 歐洲銀行、醫療等受規管行業無法用於生產部署，違反 GDPR 等合規要求
- 企業若需歐洲資料駐留，必須改用 AWS Bedrock 或 Google Vertex AI

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/claude-foundry-ga-europe/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Claude models reached GA on Microsoft Foundry with Azure-native billing and governance, but no European data zone exists. Anthropic's own documentation confirms data residency guarantees apply to Bedrock and Vertex AI but not Foundry. European practitioners from banking and healthcare report the offering is unapproved for production. By Steef-Jan Wiggers

</details>