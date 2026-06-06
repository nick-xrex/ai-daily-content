---
id: inbox_8d1ed7ef
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-rtk-releases-dev-0-43-0-rc-263-b876]]"
title: "dev-0.43.0-rc.263"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.263
source: rtk-releases
published_at: 2026-06-05T15:14:21+00:00
fetched_at: 2026-06-05T18:06:27.758648+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.263 發布安全修復，將 master 分支的權限強化（permission hardening）移植至 develop 分支，並針對 Copilot CLI 進行相應適配。該修復確保 Copilot CLI 環境也能受益於最新的安全改進。"
key_points:
  - "權限強化從 master backport 至 develop"
  - "新增 Copilot CLI 適配層"
tags: [rtk, security, permissions, copilot-cli]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.263

RTK dev-0.43.0-rc.263 發布安全修復，將 master 分支的權限強化（permission hardening）移植至 develop 分支，並針對 Copilot CLI 進行相應適配。該修復確保 Copilot CLI 環境也能受益於最新的安全改進。

### 重點
- 權限強化從 master backport 至 develop
- 新增 Copilot CLI 適配層

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.263)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2286 from rtk-ai/fix/cve-permission-hardening-port 

 fix(security): port permission hardening from master + Copilot CLI adaptation

</details>