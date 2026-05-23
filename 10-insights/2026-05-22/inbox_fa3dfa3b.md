---
id: inbox_fa3dfa3b
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-claude-code-releases-v2-1-148-60b8]]"
title: "v2.1.148"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.148
source: claude-code-releases
published_at: 2026-05-22T01:16:52+00:00
fetched_at: 2026-05-22T18:04:55.044139+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.148 修復 v2.1.147 版本引入的迴歸 bug：Bash 工具在某些用戶上對每個命令都返回 exit code 127，導致工具失效。此修復恢復正常的 exit code 行為，所有依賴 Bash 工具執行命令的用戶應升級至此版本。"
key_points:
  - "Bash 工具 exit code 127 迴歸 bug（v2.1.147 引入）已修復"
  - "影響：某些用戶的所有 Bash 命令執行返回異常狀態碼"
  - "建議用戶立即升級至 v2.1.148"
tags: [bash-tool, bug-fix, claude-code, regression]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.148

Claude Code v2.1.148 修復 v2.1.147 版本引入的迴歸 bug：Bash 工具在某些用戶上對每個命令都返回 exit code 127，導致工具失效。此修復恢復正常的 exit code 行為，所有依賴 Bash 工具執行命令的用戶應升級至此版本。

### 重點
- Bash 工具 exit code 127 迴歸 bug（v2.1.147 引入）已修復
- 影響：某些用戶的所有 Bash 命令執行返回異常狀態碼
- 建議用戶立即升級至 v2.1.148

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.148)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed the Bash tool returning exit code 127 on every command for some users (a regression introduced in 2.1.147)

</details>