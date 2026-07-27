---
id: inbox_2fbf5a67
date: 2026-07-26
source_ref: "[[00-inbox/2026-07-26/0123-infoq-main-amazon-eks-adds-kubernetes-version-rollb-5206]]"
title: "Amazon EKS Adds Kubernetes Version Rollback Within 7 Days of an Upgrade"
url: https://www.infoq.com/news/2026/07/eks-version-rollback/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-26T06:04:00+00:00
fetched_at: 2026-07-27T01:37:05.906945+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Amazon EKS 新增 Kubernetes 版本回滾功能，允許在升級後 7 天內將叢集控制平面恢復到先前的 K8s 版本。此功能為原地升級提供安全保障網絡，用戶可在升級後發現問題時快速回復，大幅降低叢集升級風險。此舉減少了運維團隊對升級失敗的顧慮。"
key_points:
  - "EKS 支援升級後 7 天內的 Kubernetes 版本回滾"
  - "可快速從有問題的升級中恢復控制平面"
  - "大幅降低原地升級風險，減少運維不確定性"
tags: [kubernetes, eks, aws, rollback, devops]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Amazon EKS Adds Kubernetes Version Rollback Within 7 Days of an Upgrade

Amazon EKS 新增 Kubernetes 版本回滾功能，允許在升級後 7 天內將叢集控制平面恢復到先前的 K8s 版本。此功能為原地升級提供安全保障網絡，用戶可在升級後發現問題時快速回復，大幅降低叢集升級風險。此舉減少了運維團隊對升級失敗的顧慮。

### 重點
- EKS 支援升級後 7 天內的 Kubernetes 版本回滾
- 可快速從有問題的升級中恢復控制平面
- 大幅降低原地升級風險，減少運維不確定性

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/eks-version-rollback/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Amazon EKS has recently introduced support for Kubernetes version rollbacks, letting practitioners revert a cluster's control plane to its previous Kubernetes version within 7 days of an upgrade if issues arise. The feature reduces the risk of in-place cluster upgrades by giving teams a safety net to recover quickly from problematic updates. By Renato Losio

</details>