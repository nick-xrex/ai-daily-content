---
id: inbox_d1f2b931
date: 2026-06-08
source_ref: "[[00-inbox/2026-06-08/1801-infoq-main-terraform-1-15-closes-gap-to-opentofu-on-8aa8]]"
title: "Terraform 1.15 Closes Gap to OpenTofu on Dynamic Sources and Deprecation"
url: https://www.infoq.com/news/2026/06/terraform-1-15/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-08T08:00:00+00:00
fetched_at: 2026-06-08T18:12:31.629298+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "HashiCorp 發布 Terraform 1.15，解決了 Terraform 社區多個長期待解決的問題。新版本引入 dynamic module sources，允許更靈活的模組來源配置。此外，增加了 variables 和 outputs 的正式棄用機制，為漸進式遷移提供了框架。新增 inline type conversion 函數和 output 區塊的型別約束，提升型別安全性。本地 Windows ARM64 支持解決了多平台開發的需求。"
key_points:
  - "Dynamic module sources 支持動態配置模組來源"
  - "Variables 和 outputs 的正式棄用機制用於漸進式遷移"
  - "新增 inline type conversion 函數與 output 型別約束、Windows ARM64 原生支持"
tags: [terraform, infrastructure-as-code, dynamic-sources, deprecation]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Terraform 1.15 Closes Gap to OpenTofu on Dynamic Sources and Deprecation

HashiCorp 發布 Terraform 1.15，解決了 Terraform 社區多個長期待解決的問題。新版本引入 dynamic module sources，允許更靈活的模組來源配置。此外，增加了 variables 和 outputs 的正式棄用機制，為漸進式遷移提供了框架。新增 inline type conversion 函數和 output 區塊的型別約束，提升型別安全性。本地 Windows ARM64 支持解決了多平台開發的需求。

### 重點
- Dynamic module sources 支持動態配置模組來源
- Variables 和 outputs 的正式棄用機制用於漸進式遷移
- 新增 inline type conversion 函數與 output 型別約束、Windows ARM64 原生支持

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/terraform-1-15/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

HashiCorp has released Terraform 1.15, introducing dynamic module sources, a formal deprecation mechanism for variables and outputs, a new inline type conversion function, type constraints for output blocks, and native Windows ARM64 support. The release addresses several long-standing requests from the Terraform community. By Matt Saunders

</details>