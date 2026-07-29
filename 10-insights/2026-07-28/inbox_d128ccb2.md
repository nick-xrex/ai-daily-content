---
id: inbox_d128ccb2
date: 2026-07-28
source_ref: "[[00-inbox/2026-07-28/2219-gitnexus-releases-rc-79ff44dfa9ac8f3d4436dc1db9a4e19979428-d621]]"
title: "rc/79ff44dfa9ac8f3d4436dc1db9a4e199794286ff: fix(config): honor parts negation on Windows (#2720)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F79ff44dfa9ac8f3d4436dc1db9a4e199794286ff
source: gitnexus-releases
published_at: 2026-07-28T19:04:34+00:00
fetched_at: 2026-07-29T01:05:58.340903+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "修復 GitNexus 在 Windows 上路徑規範化問題，使 .gitnexusignore 的否定規則（negation）能正確覆蓋硬編碼的 parts 排除規則。透過在應用忽略規則前對倉庫相對路徑進行規範化，解決了 Windows 檔案遍歷時配置規則無法生效的問題。"
key_points:
  - "Windows 路徑規範化修復使 .gitnexusignore 否定規則正確生效"
  - "倉庫相對路徑規範化可覆蓋硬編碼的 parts 排除規則"
tags: [gitnexus-releases, bug-fix, windows-compatibility]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/79ff44dfa9ac8f3d4436dc1db9a4e199794286ff: fix(config): honor parts negation on Windows (#2720)

修復 GitNexus 在 Windows 上路徑規範化問題，使 .gitnexusignore 的否定規則（negation）能正確覆蓋硬編碼的 parts 排除規則。透過在應用忽略規則前對倉庫相對路徑進行規範化，解決了 Windows 檔案遍歷時配置規則無法生效的問題。

### 重點
- Windows 路徑規範化修復使 .gitnexusignore 否定規則正確生效
- 倉庫相對路徑規範化可覆蓋硬編碼的 parts 排除規則

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F79ff44dfa9ac8f3d4436dc1db9a4e199794286ff)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Normalize repository-relative paths before applying ignore-package rules so .gitnexusignore negation can override hardcoded parts exclusions during Windows traversal. 
 Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>