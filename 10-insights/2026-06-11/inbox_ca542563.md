---
id: inbox_ca542563
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-claude-code-releases-v2-1-173-8f66]]"
title: "v2.1.173"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.173
source: claude-code-releases
published_at: 2026-06-11T05:41:54+00:00
fetched_at: 2026-06-11T22:04:44.919974+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.173 發佈，主要包含兩項 bug 修復。首先，修復 Fable 5 模型名稱帶有 [1M] 後綴的規範化問題，該後綴會自動被剝離，避免模型識別錯誤。其次，修復 Windows 環境下啟用 sandbox 時出現的虛假「sandbox 依賴缺失」警告。這些修正改善了工具在跨平台環境下的穩定性和用戶體驗。"
key_points:
  - "Fable 5 模型 [1M] 後綴自動剝離，改進模型識別準確性"
  - "Windows sandbox 虛假警告消除，改善 Windows 用戶體驗"
  - "v2.1.173 增強工具跨平台穩定性"
tags: [claude-code, bug-fix, fable-5, sandbox]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.173

Claude Code v2.1.173 發佈，主要包含兩項 bug 修復。首先，修復 Fable 5 模型名稱帶有 [1M] 後綴的規範化問題，該後綴會自動被剝離，避免模型識別錯誤。其次，修復 Windows 環境下啟用 sandbox 時出現的虛假「sandbox 依賴缺失」警告。這些修正改善了工具在跨平台環境下的穩定性和用戶體驗。

### 重點
- Fable 5 模型 [1M] 後綴自動剝離，改進模型識別準確性
- Windows sandbox 虛假警告消除，改善 Windows 用戶體驗
- v2.1.173 增強工具跨平台穩定性

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.173)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed Fable 5 model names with a [1m] suffix not being normalized — Fable 5 includes 1M context by default, so the suffix is now stripped automatically 
 Fixed a spurious "sandbox dependencies missing" startup warning on Windows when sandbox was enabled in settings

</details>