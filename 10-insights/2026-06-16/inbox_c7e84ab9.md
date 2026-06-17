---
id: inbox_c7e84ab9
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-claude-code-releases-v2-1-179-94f5]]"
title: "v2.1.179"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.179
source: claude-code-releases
published_at: 2026-06-16T20:22:14+00:00
fetched_at: 2026-06-16T22:04:45.476140+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.179 修復多項 bug 以提升穩定性與使用體驗。修復連線中斷時保留部分回應而非顯示原始錯誤（spinner 不再卡住），解決 WSL2 + Windows Terminal / VS Code 下的滑鼠滾輪迴歸問題（源於 2.1.172），修復大目錄樹沙箱 denyRead/allowRead glob 導致 Bash 工具描述過長使 Linux 無法使用，修復反饋調查誤將個位數回答作為工作階段評分，修復歡迎頁面堆疊多個推廣橫幅（現限制每工作階段一個），修復 Ctrl+O 不顯示 subagent 轉錄及點擊提示輸入焦點無法返回，修復遠端工作階段背景任務卡在『仍在執行』狀態，並改進遠端段外掛載入效能。"
key_points:
  - "修復連線中斷時保留部分回應，避免顯示原始錯誤且 spinner 卡住（提升網路穩定性）"
  - "解決 WSL2 + Windows Terminal 的滑鼠滾輪迴歸，修復大目錄沙箱配置導致的 Linux 段無法使用"
  - "改進遠端工作階段：修復背景任務卡頓狀態、外掛載入速度提升、焦點管理改善"
tags: [claude-code, bug-fixes, ux-stability, remote-session, regression-fix]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.179

Claude Code v2.1.179 修復多項 bug 以提升穩定性與使用體驗。修復連線中斷時保留部分回應而非顯示原始錯誤（spinner 不再卡住），解決 WSL2 + Windows Terminal / VS Code 下的滑鼠滾輪迴歸問題（源於 2.1.172），修復大目錄樹沙箱 denyRead/allowRead glob 導致 Bash 工具描述過長使 Linux 無法使用，修復反饋調查誤將個位數回答作為工作階段評分，修復歡迎頁面堆疊多個推廣橫幅（現限制每工作階段一個），修復 Ctrl+O 不顯示 subagent 轉錄及點擊提示輸入焦點無法返回，修復遠端工作階段背景任務卡在『仍在執行』狀態，並改進遠端段外掛載入效能。

### 重點
- 修復連線中斷時保留部分回應，避免顯示原始錯誤且 spinner 卡住（提升網路穩定性）
- 解決 WSL2 + Windows Terminal 的滑鼠滾輪迴歸，修復大目錄沙箱配置導致的 Linux 段無法使用
- 改進遠端工作階段：修復背景任務卡頓狀態、外掛載入速度提升、焦點管理改善

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.179)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed mid-stream connection drops: partial responses are now preserved instead of showing a raw error, and the spinner no longer gets stuck at "running tool" 
 Fixed mouse-wheel scrolling in WSL2 under Windows Terminal and VS Code (regression in 2.1.172) 
 Fixed a sandbox denyRead / allowRead glob over a large directory tree making the Bash tool description enormous and the session unusable on Linux 
 Fixed the feedback survey capturing a single-digit reply as a session rating immediately after a turn completes 
 Fixed the welcome screen stacking multiple promotional banners — at most one promo now shows per session 
 Fixed Ctrl+O not showing the subagent's transcript when viewing a subagent 
 Fixed clicking the prompt input not returning focus from the subagent/footer panel 
 Fixed remote session background tasks appearing stuck as "still running" between turns 
 Improved plugin loading performance in remote sessions

</details>