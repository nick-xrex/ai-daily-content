---
id: inbox_cb58e678
date: 2026-06-01
source_ref: "[[00-inbox/2026-06-01/2246-infoq-main-a-trailing-slash-bypassed-aws-api-gatewa-cb5a]]"
title: "A Trailing Slash Bypassed AWS API Gateway Authorization"
url: https://www.infoq.com/news/2026/06/aws-api-gateway-auth-bypass/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-01T09:55:00+00:00
fetched_at: 2026-06-01T22:54:44.490081+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS HTTP API 路徑規範化不匹配導致認證繞過：URL 末尾加 trailing slash 可繞過 Lambda authorizer，使無身份驗證請求通過（Fintech 應用曝露實際威脅）。根本原因為 HTTP API 貪心路由匹配與授權層路徑規範化差異。同型漏洞亦出現在 gRPC-Go（CVE-2026-33186），說明路徑規範化是跨框架的安全設計缺陷。"
key_points:
  - "AWS HTTP API 漏洞：trailing slash 繞過 Lambda authorizer 認證"
  - "根本原因：路徑規範化不一致（HTTP API 貪心匹配 vs 授權層規格）"
  - "跨框架風險：gRPC-Go 亦有相同漏洞型（CVE-2026-33186），路徑規範化是通用缺陷"
tags: [security, aws-api-gateway, path-normalization, authorization-bypass, cve]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## A Trailing Slash Bypassed AWS API Gateway Authorization

AWS HTTP API 路徑規範化不匹配導致認證繞過：URL 末尾加 trailing slash 可繞過 Lambda authorizer，使無身份驗證請求通過（Fintech 應用曝露實際威脅）。根本原因為 HTTP API 貪心路由匹配與授權層路徑規範化差異。同型漏洞亦出現在 gRPC-Go（CVE-2026-33186），說明路徑規範化是跨框架的安全設計缺陷。

### 重點
- AWS HTTP API 漏洞：trailing slash 繞過 Lambda authorizer 認證
- 根本原因：路徑規範化不一致（HTTP API 貪心匹配 vs 授權層規格）
- 跨框架風險：gRPC-Go 亦有相同漏洞型（CVE-2026-33186），路徑規範化是通用缺陷

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/aws-api-gateway-auth-bypass/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A security researcher found that adding a trailing slash to AWS HTTP API paths bypassed Lambda authorizer authentication entirely, enabling unauthenticated wire transfers at a fintech. The root cause is a path normalization mismatch between HTTP API's greedy route matching and its authorization layer. The same vulnerability class appeared in gRPC-Go via CVE-2026-33186. By Steef-Jan Wiggers

</details>