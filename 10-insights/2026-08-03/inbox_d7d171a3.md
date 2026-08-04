---
id: inbox_d7d171a3
date: 2026-08-03
source_ref: "[[00-inbox/.../inbox_d7d171a3]]"
title: "HashiCorp Ships Public Beta of Vault Kubernetes Key Management"
url: https://www.infoq.com/news/2026/08/vault-kubernetes-key-management/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-03T10:00:00+00:00
fetched_at: 2026-08-04T01:58:03.067373+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "HashiCorp 推出 Vault Kubernetes 金鑰管理公開測試版。該外掛實現 KMS v2 相容性，允許 Kubernetes API server 將 etcd 資料的信封加密委派給 Vault Enterprise。最關鍵改進是將保護 etcd 的金鑰加密金鑰(KEK)從 Kubernetes 集群內移出，置入由 Vault 單獨治理的信任域，達成訪問控制和審計隔離。這對高安全需求的企業環境特別重要。"
key_points:
  - "KMS v2 相容意味著 Kubernetes 原生支援，無需修改 kubelet 配置"
  - "KEK 外移到 Vault 實現信任域分離，支援細粒度訪問控制和稽核"
  - "適用於需要金鑰分層管理和合規隔離的企業環保"
tags: [vault, kubernetes, kms, encryption, key-management]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## HashiCorp Ships Public Beta of Vault Kubernetes Key Management

HashiCorp 推出 Vault Kubernetes 金鑰管理公開測試版。該外掛實現 KMS v2 相容性，允許 Kubernetes API server 將 etcd 資料的信封加密委派給 Vault Enterprise。最關鍵改進是將保護 etcd 的金鑰加密金鑰(KEK)從 Kubernetes 集群內移出，置入由 Vault 單獨治理的信任域，達成訪問控制和審計隔離。這對高安全需求的企業環境特別重要。

### 重點
- KMS v2 相容意味著 Kubernetes 原生支援，無需修改 kubelet 配置
- KEK 外移到 Vault 實現信任域分離，支援細粒度訪問控制和稽核
- 適用於需要金鑰分層管理和合規隔離的企業環保

**原文：** [infoq-main](https://www.infoq.com/news/2026/08/vault-kubernetes-key-management/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# HashiCorp Ships Public Beta of Vault Kubernetes Key Management

HashiCorp has released a public beta of Vault Kubernetes key management, a KMS v2-compatible plugin that lets the Kubernetes API server delegate envelope encryption to Vault Enterprise, moving the key encryption keys that protect etcd data out of the cluster and into a separately governed trust domain. By Mark Silvester

</details>