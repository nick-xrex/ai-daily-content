---
id: inbox_e8878b34
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0014-rtk-releases-v0-42-0-873f]]"
title: "v0.42.0"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.42.0
source: rtk-releases
published_at: 2026-05-24T15:48:51+00:00
fetched_at: 2026-05-26T00:25:55.647818+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK（Rust Token Killer，token 最佳化命令列代理工具）發布 v0.42.0，主要功能為在 hook 層級新增對 pi agent 的支援。同時修複了一個重要 bug：git log 在處理合併提交時未能正確遵守明確指定的 -n 行數限制。此修複改進了開發者在查看提交日誌時的精確控制能力。RTK 通過降低 Claude 開發工作流程的 token 消耗（平均節省 60-90%）來加速開發效率。"
key_points:
  - "PI agent hook 支援：新增 hook 層級的 pi agent 代理類型（commit 805caf7）"
  - "Git log -n 限制修複：解決合併提交時忽視明確指定行數限制的問題（commit 26c8890）"
  - "RTK 版本號：v0.42.0，持續改進 token 最佳化工具鏈"
tags: [rtk, agent-support, cli-tool, token-optimization, bug-fix]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.42.0

RTK（Rust Token Killer，token 最佳化命令列代理工具）發布 v0.42.0，主要功能為在 hook 層級新增對 pi agent 的支援。同時修複了一個重要 bug：git log 在處理合併提交時未能正確遵守明確指定的 -n 行數限制。此修複改進了開發者在查看提交日誌時的精確控制能力。RTK 通過降低 Claude 開發工作流程的 token 消耗（平均節省 60-90%）來加速開發效率。

### 重點
- PI agent hook 支援：新增 hook 層級的 pi agent 代理類型（commit 805caf7）
- Git log -n 限制修複：解決合併提交時忽視明確指定行數限制的問題（commit 26c8890）
- RTK 版本號：v0.42.0，持續改進 token 最佳化工具鏈

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.42.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

0.42.0 (2026-05-24) 
 Features 
 
 hook: add pi agent support ( 805caf7 ) 
 
 Bug Fixes 
 
 honor explicit -n N limit for git log on merge commits ( 26c8890 )

</details>