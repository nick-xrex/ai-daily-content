---
id: inbox_a3e447ab
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-claude-code-releases-v2-1-201-183c]]"
title: "v2.1.201"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.201
source: claude-code-releases
published_at: 2026-07-03T23:50:35+00:00
fetched_at: 2026-07-04T01:20:23.282234+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.201 修復了 Claude Sonnet 5 會話中的系統角色處理問題。此前，在中間對話中（mid-conversation），系統角色會包含 harness reminders，可能導致提示詞污染。新版本改變了此行為，Claude Sonnet 5 會話不再在 mid-conversation system role 中使用 harness reminders。此修復簡化了系統指令處理，可改善對話上下文清潔度，特別是在長對話場景中。"
key_points:
  - "Claude Sonnet 5 sessions 不再在 mid-conversation system role 中使用 harness reminders，減少上下文污染"
tags: [claude-code, claude-sonnet-5, system-role]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.201

Claude Code v2.1.201 修復了 Claude Sonnet 5 會話中的系統角色處理問題。此前，在中間對話中（mid-conversation），系統角色會包含 harness reminders，可能導致提示詞污染。新版本改變了此行為，Claude Sonnet 5 會話不再在 mid-conversation system role 中使用 harness reminders。此修復簡化了系統指令處理，可改善對話上下文清潔度，特別是在長對話場景中。

### 重點
- Claude Sonnet 5 sessions 不再在 mid-conversation system role 中使用 harness reminders，減少上下文污染

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.201)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Claude Sonnet 5 sessions no longer use the mid-conversation system role for harness reminders

</details>