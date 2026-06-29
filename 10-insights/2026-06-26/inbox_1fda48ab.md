---
id: inbox_1fda48ab
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_1fda48ab]]"
title: "Argo CD 3.5 Tightens Supply Chain Security with Internal mTLS and Source Integrity"
url: https://www.infoq.com/news/2026/06/argocd-supply-chain-security/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-26T12:00:00+00:00
fetched_at: 2026-06-29T01:01:09.354477+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Argo CD 項目發布 v3.5 RC（Release Candidate）。此版本強化供應鏈安全，內部組件間強制使用 mTLS（Mutual TLS）加密，新增 Git commit 簽名驗證功能確保源碼完整性。用戶界面新增 native ApplicationSet 管理功能。同時，impersonation 和 Source Hydrator 兩項功能從 alpha 階段升級至 beta，表明其穩定性和就緒度提升。這些更新重點聚焦 CI/CD 管道的端到端安全性，涵蓋組件通訊加密和部署源碼驗證。"
key_points:
  - "強制內部組件使用 mTLS，提升 Argo CD 系統內部通訊的安全隔離級別"
  - "新增 Git commit 簽名驗證，確保部署的代碼來自可信源並未被篡改"
  - "ApplicationSet 進入 UI native 支持，impersonation 和 Source Hydrator 升級至 beta，提升開發效率和系統成熟度"
tags: [argo-cd, supply-chain-security, mtls, git-signature-verification, cd-pipeline]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Argo CD 3.5 Tightens Supply Chain Security with Internal mTLS and Source Integrity

Argo CD 項目發布 v3.5 RC（Release Candidate）。此版本強化供應鏈安全，內部組件間強制使用 mTLS（Mutual TLS）加密，新增 Git commit 簽名驗證功能確保源碼完整性。用戶界面新增 native ApplicationSet 管理功能。同時，impersonation 和 Source Hydrator 兩項功能從 alpha 階段升級至 beta，表明其穩定性和就緒度提升。這些更新重點聚焦 CI/CD 管道的端到端安全性，涵蓋組件通訊加密和部署源碼驗證。

### 重點
- 強制內部組件使用 mTLS，提升 Argo CD 系統內部通訊的安全隔離級別
- 新增 Git commit 簽名驗證，確保部署的代碼來自可信源並未被篡改
- ApplicationSet 進入 UI native 支持，impersonation 和 Source Hydrator 升級至 beta，提升開發效率和系統成熟度

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/argocd-supply-chain-security/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Argo CD 3.5 Tightens Supply Chain Security with Internal mTLS and Source Integrity

The Argo CD project released a v3.5 release candidate in June 2026. This version adds mutual TLS enforcement for internal components. It also includes Git commit signature verification for supply chain security and native ApplicationSet management in the UI. The release also graduates two significant features: impersonation and Source Hydrator, from alpha to beta. By Claudio Masolo

</details>