---
id: inbox_3efd2495
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-hermes-agent-releases-backup-opentui-prestrip-20260616-1950-da2c]]"
title: "backup/opentui-prestrip-20260616-1950"
url: https://github.com/NousResearch/hermes-agent/releases/tag/backup%2Fopentui-prestrip-20260616-1950
source: hermes-agent-releases
published_at: 2026-06-16T13:42:21+00:00
fetched_at: 2026-06-16T22:06:44.940616+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 備份分支 backup/opentui-prestrip-20260616-1950 發布，涉及 TUI（終端用戶界面）模塊重構，將 tree-sitter 語法文法從 vendored（內嵌）方式改為運行時動態載入。此為備份快照發布，完整改動內容未提供。"
key_points:
  - "重構目標：TUI 模塊"
  - "優化方向：tree-sitter 文法動態取得（移除 vendored 依賴）"
tags: [hermes-agent, tui-refactor, tree-sitter]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## backup/opentui-prestrip-20260616-1950

Hermes Agent 備份分支 backup/opentui-prestrip-20260616-1950 發布，涉及 TUI（終端用戶界面）模塊重構，將 tree-sitter 語法文法從 vendored（內嵌）方式改為運行時動態載入。此為備份快照發布，完整改動內容未提供。

### 重點
- 重構目標：TUI 模塊
- 優化方向：tree-sitter 文法動態取得（移除 vendored 依賴）

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/backup%2Fopentui-prestrip-20260616-1950)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

refactor(tui): fetch tree-sitter grammars at runtime instead of vendo...

</details>