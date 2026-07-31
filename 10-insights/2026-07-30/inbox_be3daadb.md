---
id: inbox_be3daadb
date: 2026-07-30
source_ref: "[[00-inbox/.../inbox_be3daadb]]"
title: "AWS Lambda&#39;s Self-Managed Code Storage Lifts the Account Quota, Not the Function Size Limit"
url: https://www.infoq.com/news/2026/07/lambda-self-managed-storage/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-30T07:57:00+00:00
fetched_at: 2026-07-31T01:51:26.254815+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS Lambda 新增自管理代碼存儲功能，允許 Lambda 函式直接引用客戶自有 S3 bucket 中的部署包，移除了區域級別的代碼存儲配額限制，將托管賬戶預設配額從 75 GB 提升至 300 GB。但單函式包大小限制維持不變，且更換部署包後仍需手動執行 UpdateFunctionCode。Terraform provider 對此功能的支援仍為開放增強請求。此舉對大型部署包或帳戶級別代碼庫眾多的客戶有幫助。"
key_points:
  - "S3 反向引用移除區域級代碼存儲配額，賬戶預設配額 75 GB → 300 GB"
  - "單函式包大小限制未變，UpdateFunctionCode 調用仍需手動執行"
  - "Terraform 集成尚未支援，開發者需單獨跟進或使用 CloudFormation/SDK"
tags: [aws-lambda, deployment, s3-integration, infrastructure, serverless]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Lambda's Self-Managed Code Storage Lifts the Account Quota, Not the Function Size Limit

AWS Lambda 新增自管理代碼存儲功能，允許 Lambda 函式直接引用客戶自有 S3 bucket 中的部署包，移除了區域級別的代碼存儲配額限制，將托管賬戶預設配額從 75 GB 提升至 300 GB。但單函式包大小限制維持不變，且更換部署包後仍需手動執行 UpdateFunctionCode。Terraform provider 對此功能的支援仍為開放增強請求。此舉對大型部署包或帳戶級別代碼庫眾多的客戶有幫助。

### 重點
- S3 反向引用移除區域級代碼存儲配額，賬戶預設配額 75 GB → 300 GB
- 單函式包大小限制未變，UpdateFunctionCode 調用仍需手動執行
- Terraform 集成尚未支援，開發者需單獨跟進或使用 CloudFormation/SDK

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/lambda-self-managed-storage/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AWS Lambda's Self-Managed Code Storage Lifts the Account Quota, Not the Function Size Limit

AWS Lambda can now reference deployment packages directly in customer-owned S3 buckets, removing the per-Region code storage quota and raising the managed default from 75 GB to 300 GB. Per-function package limits are unchanged, and UpdateFunctionCode is still required after replacing an object. Terraform provider support remains an open enhancement request. By Steef-Jan Wiggers

</details>