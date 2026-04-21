---
id: inbox_c5fda427
date: 2026-04-17
source_ref: "[[00-inbox/2026-04-17/0158-claude-code-releases-v2-1-113-8037]]"
title: "v2.1.113"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.113
source: claude-code-releases
published_at: 2026-04-17T19:34:41+00:00
fetched_at: 2026-04-21T02:00:53.040307+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.113 於 2026 年 4 月 17 日發布，包含架構優化與安全加固。CLI 改為生成原生二進位檔（平臺特定可選依賴）而非捆綁 JavaScript，新增 sandbox.network.deniedDomains 設定可阻擋特定域名，全屏模式新增 Shift+↑/↓ 選擇並滾動，Ctrl+A/E 調和 readline 行為。Subagent 卡死現在 10 分鐘後明確失敗，安全機制強化包括 macOS /private/* 危險移除目標、exec 包裹指令檢偵、find -exec -delete 停用。修復 MCP 併發呼叫逾時處理漏洞、多行表格渲染破損。"
key_points:
  - "CLI 改用原生二進位執行（取代 JavaScript 打包），改善啟動效率"
  - "新增 sandbox.network.deniedDomains 設定，允許黑名單域名突破白名單通配"
  - "Subagent 10 分鐘卡死判定改為明確錯誤；安全規則加強對 sudo/env/watch 等 exec 包裹的偵測"
tags: [claude-code, security, performance, mcp, architecture]
topics: [agents.mcp]
importance: 3
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.113

Claude Code v2.1.113 於 2026 年 4 月 17 日發布，包含架構優化與安全加固。CLI 改為生成原生二進位檔（平臺特定可選依賴）而非捆綁 JavaScript，新增 sandbox.network.deniedDomains 設定可阻擋特定域名，全屏模式新增 Shift+↑/↓ 選擇並滾動，Ctrl+A/E 調和 readline 行為。Subagent 卡死現在 10 分鐘後明確失敗，安全機制強化包括 macOS /private/* 危險移除目標、exec 包裹指令檢偵、find -exec -delete 停用。修復 MCP 併發呼叫逾時處理漏洞、多行表格渲染破損。

### 重點
- CLI 改用原生二進位執行（取代 JavaScript 打包），改善啟動效率
- 新增 sandbox.network.deniedDomains 設定，允許黑名單域名突破白名單通配
- Subagent 10 分鐘卡死判定改為明確錯誤；安全規則加強對 sudo/env/watch 等 exec 包裹的偵測

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.113)