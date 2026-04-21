---
id: inbox_5357f42a
date: 2026-04-15
source_ref: "[[00-inbox/2026-04-15/0158-claude-code-releases-v2-1-110-41cc]]"
title: "v2.1.110"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.110
source: claude-code-releases
published_at: 2026-04-15T23:21:43+00:00
fetched_at: 2026-04-21T02:00:53.049803+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.110 於 2026 年 4 月 15 日發布，推出 /tui 指令與無閃爍全屏渲染模式。Ctrl+O 現僅切換逐字稿詳細度，焦點檢視由新 /focus 指令控制。新增推播通知工具支援 Remote Control 行動推播。autoScrollEnabled 設定停用全屏自動滾動。外部編輯器（Ctrl+G）可選顯示 Claude 最後回應作註解。/plugin Installed 分頁改進：待處理項目與最愛置頂，停用項目收折。/doctor 警告 MCP 伺服器定義重複。--resume/--continue 恢復未過期排程工作。/autocompact、/context、/exit、/reload-plugins 支援 Remote Control。修復 MCP 伺服器連線中斷導致無限掛起、API 不可達多分鐘等待、非同步輸出高 CPU、外掛依賴遺失等 25+ 項問題。"
key_points:
  - "/tui 指令啟用無閃爍全屏渲染同會話切換，改善終端顯示流暢度"
  - "推播通知工具整合，Remote Control 行動客戶端支援 Claude 主動通知"
  - "Remote Control 客戶端擴展支援 /autocompact、/context、/exit、/reload-plugins"
tags: [claude-code, ui, remote-control, notifications, mcp]
topics: [agents.mcp]
importance: 4
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.110

Claude Code v2.1.110 於 2026 年 4 月 15 日發布，推出 /tui 指令與無閃爍全屏渲染模式。Ctrl+O 現僅切換逐字稿詳細度，焦點檢視由新 /focus 指令控制。新增推播通知工具支援 Remote Control 行動推播。autoScrollEnabled 設定停用全屏自動滾動。外部編輯器（Ctrl+G）可選顯示 Claude 最後回應作註解。/plugin Installed 分頁改進：待處理項目與最愛置頂，停用項目收折。/doctor 警告 MCP 伺服器定義重複。--resume/--continue 恢復未過期排程工作。/autocompact、/context、/exit、/reload-plugins 支援 Remote Control。修復 MCP 伺服器連線中斷導致無限掛起、API 不可達多分鐘等待、非同步輸出高 CPU、外掛依賴遺失等 25+ 項問題。

### 重點
- /tui 指令啟用無閃爍全屏渲染同會話切換，改善終端顯示流暢度
- 推播通知工具整合，Remote Control 行動客戶端支援 Claude 主動通知
- Remote Control 客戶端擴展支援 /autocompact、/context、/exit、/reload-plugins

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.110)