---
id: inbox_840ae1ee
date: 2026-04-16
source_ref: "[[00-inbox/2026-04-16/0158-claude-code-releases-v2-1-111-91ae]]"
title: "v2.1.111"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.111
source: claude-code-releases
published_at: 2026-04-16T15:18:45+00:00
fetched_at: 2026-04-21T02:00:53.044171+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.111 於 2026 年 4 月 16 日發布，這是重大功能版本，主要推出 Claude Opus 4.7 xhigh 努力等級。Max 訂閱戶現可使用 Opus 4.7 auto mode，並透過 /effort 滑桿調整速度與智能平衡；xhigh 等級介於 high 與 max 之間。新增 /less-permission-prompts 技能掃描常見唯讀指令自動提議白名單，/ultrareview 啟用雲端並行多代理程式碼審查。/theme 增加「Auto (match terminal)」自動配對終端深淺模式。Windows 上 PowerShell 工具逐漸推出，Linux/macOS 可透過環境變數啟用。計畫檔名改為基於提示內容生成（如 fix-auth-race-snug-otter.md），提升可追蹤性。修復 /resume 大型會話、Tab 補全、MCP 逾時等 25+ 項問題。"
key_points:
  - "Claude Opus 4.7 xhigh 努力等級推出，Max 訂閱戶可用 auto mode 搭配 Opus 4.7"
  - "/ultrareview 支援雲端並行代理程式碼審查，可直接審查 GitHub PR"
  - "/less-permission-prompts 技能掃描安全白名單；計畫檔名由提示內容生成"
tags: [claude-code, opus-4-7, features, ultrareview, agents]
topics: [foundation_models.claude, agents.mcp]
importance: 5
novelty: 5
deep_dive_candidate: true
deep_dive_approved: false
---

## v2.1.111

Claude Code v2.1.111 於 2026 年 4 月 16 日發布，這是重大功能版本，主要推出 Claude Opus 4.7 xhigh 努力等級。Max 訂閱戶現可使用 Opus 4.7 auto mode，並透過 /effort 滑桿調整速度與智能平衡；xhigh 等級介於 high 與 max 之間。新增 /less-permission-prompts 技能掃描常見唯讀指令自動提議白名單，/ultrareview 啟用雲端並行多代理程式碼審查。/theme 增加「Auto (match terminal)」自動配對終端深淺模式。Windows 上 PowerShell 工具逐漸推出，Linux/macOS 可透過環境變數啟用。計畫檔名改為基於提示內容生成（如 fix-auth-race-snug-otter.md），提升可追蹤性。修復 /resume 大型會話、Tab 補全、MCP 逾時等 25+ 項問題。

### 重點
- Claude Opus 4.7 xhigh 努力等級推出，Max 訂閱戶可用 auto mode 搭配 Opus 4.7
- /ultrareview 支援雲端並行代理程式碼審查，可直接審查 GitHub PR
- /less-permission-prompts 技能掃描安全白名單；計畫檔名由提示內容生成

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.111)