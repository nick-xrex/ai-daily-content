---
id: inbox_6f6d0808
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2208-infoq-main-how-pinterest-secures-aws-infrastructure-028d]]"
title: "How Pinterest Secures AWS Infrastructure at Scale with a Centralized Terraform Pipeline"
url: https://www.infoq.com/news/2026/08/pinterest-secures-aws-infra/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-10T10:00:00+00:00
fetched_at: 2026-08-11T00:47:34.310947+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pinterest 開發 Resource Provisioner Pipeline（RPP），一個自建的 Terraform 執行引擎。RPP 確保最小權限存取、要求雙人控制審核，並為 GitHub Actions 工作流增加嚴格的 guardrails，以安全管理 AWS 基礎設施規模部署。"
key_points:
  - "自建 RPP 集中管理 Terraform 執行，實施 least-privilege 存取控制"
  - "要求 dual-control reviews 保證 infrastructure 變更經多人核可"
  - "為 GitHub Actions workflows 增加安全 guardrails，嚴格控制 IAM 權限邊界"
tags: [terraform, aws, infrastructure-as-code, security, github-actions]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How Pinterest Secures AWS Infrastructure at Scale with a Centralized Terraform Pipeline

Pinterest 開發 Resource Provisioner Pipeline（RPP），一個自建的 Terraform 執行引擎。RPP 確保最小權限存取、要求雙人控制審核，並為 GitHub Actions 工作流增加嚴格的 guardrails，以安全管理 AWS 基礎設施規模部署。

### 重點
- 自建 RPP 集中管理 Terraform 執行，實施 least-privilege 存取控制
- 要求 dual-control reviews 保證 infrastructure 變更經多人核可
- 為 GitHub Actions workflows 增加安全 guardrails，嚴格控制 IAM 權限邊界

**原文：** [infoq-main](https://www.infoq.com/news/2026/08/pinterest-secures-aws-infra/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Pinterest has revealed the Resource Provisioner Pipeline (RPP), its own Terraform execution engine. It ensures least-privilege access and needs dual-control reviews. This is important for the company’s AWS infrastructure, as it adds strict guardrails to the GitHub Actions workflows. By Claudio Masolo

</details>