---
id: inbox_a31c940e
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/1259-hackernews-we-need-a-federation-of-forges-6a40]]"
title: "We need a federation of forges"
url: https://blog.tangled.org/federation/
source: hackernews
published_at: 2026-04-29T14:00:59+00:00
fetched_at: 2026-05-01T13:50:39.287098+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "部落格文章倡議採用「鍛造聯邦」(federation of forges) 架構，反對開源軟體對 GitHub 單一平台的過度依賴。提議結合 AT protocol 處理認證事件和社交功能（issues、pull requests、timelines、stars），搭配 git 負責實際代碼轉移，實現跨伺服器協作。開發者可在任意伺服器上協作和跨伺服器 fork，無需被單一平台綁定，現代化了傳統的「email + git」工作流。此模式透過分散式基礎設施仿效郵件和 git 等時間驗證的協議。該方案降低廠商鎖定風險、減少對企業基礎設施的依賴，同時保持協作的易用性和社交功能。"
key_points:
  - "分層架構：AT protocol 處理 metadata、社交功能（issues、PRs、stars、timelines）；git 處理代碼轉移，實現關注點分離"
  - "跨伺服器協作：開發者可在任何伺服器上操作倉庫、跨伺服器 fork，無需被單一平台綁定，仿效電郵和 git 的去中心化模式"
  - "風險降低：分散式基礎設施避免單一廠商鎖定，提高開源生態韌性，同時保留社交和協作特性"
tags: [federation, decentralization, open-source, at-protocol, git]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## We need a federation of forges

部落格文章倡議採用「鍛造聯邦」(federation of forges) 架構，反對開源軟體對 GitHub 單一平台的過度依賴。提議結合 AT protocol 處理認證事件和社交功能（issues、pull requests、timelines、stars），搭配 git 負責實際代碼轉移，實現跨伺服器協作。開發者可在任意伺服器上協作和跨伺服器 fork，無需被單一平台綁定，現代化了傳統的「email + git」工作流。此模式透過分散式基礎設施仿效郵件和 git 等時間驗證的協議。該方案降低廠商鎖定風險、減少對企業基礎設施的依賴，同時保持協作的易用性和社交功能。

### 重點
- 分層架構：AT protocol 處理 metadata、社交功能（issues、PRs、stars、timelines）；git 處理代碼轉移，實現關注點分離
- 跨伺服器協作：開發者可在任何伺服器上操作倉庫、跨伺服器 fork，無需被單一平台綁定，仿效電郵和 git 的去中心化模式
- 風險降低：分散式基礎設施避免單一廠商鎖定，提高開源生態韌性，同時保留社交和協作特性

**原文：** [hackernews](https://blog.tangled.org/federation/)