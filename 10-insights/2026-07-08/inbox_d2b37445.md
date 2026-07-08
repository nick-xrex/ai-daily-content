---
id: inbox_d2b37445
date: 2026-07-08
source_ref: "[[00-inbox/2026-07-08/0032-claude-code-releases-v2-1-204-a0c4]]"
title: "v2.1.204"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.204
source: claude-code-releases
published_at: 2026-07-08T00:27:50+00:00
fetched_at: 2026-07-08T00:36:30.293276+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.204 發布，修復 SessionStart hooks 在 headless sessions 中無法正常串流 hook events 的問題。該缺陷會導致遠端工作者在 hook 初始化執行途中被閒置回收（idle-reaped），中斷工作流程。此修正對依賴遠端執行環境進行長時間初始化操作的場景至關重要，增強了系統的穩定性與可靠性。"
key_points:
  - "修復 headless sessions 中 SessionStart hooks 的事件串流中斷問題"
  - "防止遠端工作者在 hook 執行中途被 idle-reaped（閒置回收）"
  - "提升遠端執行環境的穩定性與可靠性"
tags: [claude-code, bug-fix, headless-execution, hook-events, remote-workers]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.204

Claude Code v2.1.204 發布，修復 SessionStart hooks 在 headless sessions 中無法正常串流 hook events 的問題。該缺陷會導致遠端工作者在 hook 初始化執行途中被閒置回收（idle-reaped），中斷工作流程。此修正對依賴遠端執行環境進行長時間初始化操作的場景至關重要，增強了系統的穩定性與可靠性。

### 重點
- 修復 headless sessions 中 SessionStart hooks 的事件串流中斷問題
- 防止遠端工作者在 hook 執行中途被 idle-reaped（閒置回收）
- 提升遠端執行環境的穩定性與可靠性

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.204)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed hook events not streaming during SessionStart hooks in headless sessions, which could cause remote workers to be idle-reaped mid-hook

</details>