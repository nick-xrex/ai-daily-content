---
id: inbox_d3010c29
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/0011-simon-willison-quoting-github-changeling-7ea9]]"
title: "Quoting GitHub Changeling"
url: https://simonwillison.net/2026/Jul/14/github-changeling/#atom-everything
source: simon-willison
published_at: 2026-07-14T22:43:35+00:00
fetched_at: 2026-07-15T00:16:29.416560+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 已將 Dependabot 依賴更新冷卻期設置為新預設行為，無需額外配置。該冷卻期規則要求新版本在發布後至少等待 3 天，方可自動開啟版本更新 PR。此策略旨在給開源社群充分時間測試新版本、發現並回報潛在問題，從而降低採用包含隱藏 bug 或安全漏洞新版本的風險。對依賴管理工作流的影響是推遲定期更新時間，但提高了選定版本的穩定性。對使用 Dependabot 的開發團隊而言，此預設行為無需干預將自動生效。該決策反映了依賴管理中「等待冷卻期以降低風險」的最佳實踐。"
key_points:
  - "新版本發布後等待 3 天方可開 PR，成為預設無需配置的行為"
  - "策略目的：讓社群充分測試新版本、發現隱藏問題，降低採用不穩定版本的風險"
  - "冷卻期策略為依賴安全性與穩定性的權衡方案"
tags: [dependabot, dependency-management, cooldown, security]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting GitHub Changeling

GitHub 已將 Dependabot 依賴更新冷卻期設置為新預設行為，無需額外配置。該冷卻期規則要求新版本在發布後至少等待 3 天，方可自動開啟版本更新 PR。此策略旨在給開源社群充分時間測試新版本、發現並回報潛在問題，從而降低採用包含隱藏 bug 或安全漏洞新版本的風險。對依賴管理工作流的影響是推遲定期更新時間，但提高了選定版本的穩定性。對使用 Dependabot 的開發團隊而言，此預設行為無需干預將自動生效。該決策反映了依賴管理中「等待冷卻期以降低風險」的最佳實踐。

### 重點
- 新版本發布後等待 3 天方可開 PR，成為預設無需配置的行為
- 策略目的：讓社群充分測試新版本、發現隱藏問題，降低採用不穩定版本的風險
- 冷卻期策略為依賴安全性與穩定性的權衡方案

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/14/github-changeling/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Dependabot now waits until a new release has been available on its registry for at least three days before opening a version update pull request. This cooldown is now the default and requires no configuration. 
 &mdash; GitHub Changeling , embracing dependency cooldowns 

 Tags: dependency-cooldowns , packaging , security , github

</details>