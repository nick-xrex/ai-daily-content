---
id: inbox_cc7bef6a
date: 2026-07-13
source_ref: "[[00-inbox/2026-07-13/2231-ruflo-releases-v3-26-1-windows-statusline-hotfix-9b3d]]"
title: "v3.26.1 — Windows statusline hotfix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.26.1
source: ruflo-releases
published_at: 2026-07-13T17:22:41+00:00
fetched_at: 2026-07-14T00:19:08.363893+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.26.1 緊急修復 Windows 用戶的 statusline 顯示問題——狀態列只顯示 2 行且 intelligence percentage 卡在 0%。根本原因：代碼重複加上 `2>/dev/null` 重定向，但 Node execSync 本身已透過 stdio: ['pipe','pipe','pipe'] 自動捕獲 stderr；在 Windows cmd.exe 上 /dev/null 不存在，導致每次委派都失敗且無聲消退，進而回退到硬編碼的 0% 預設值。此缺陷源自 PR #2337（2026-06-10 的委派快取修復），在 v3.26.0 被真實用戶發現。已移除冗餘重定向並新增迴歸測試。已發布 @claude-flow/cli@3.26.1、claude-flow@3.26.1、ruflo@3.26.1。"
key_points:
  - "Windows cmd.exe 無法理解 POSIX /dev/null，導致委派失敗無聲消退——跨平台兼容陷阱"
  - "Node execSync 已內建 stderr 捕獲，勿重複加重定向（stdio 設定優先）"
  - "已新增迴歸測試防止重發，已知後續：getGitInfo() 仍需修復 Windows git info 讀取"
tags: [ruflo, bug-fix, cross-platform, windows]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.26.1 — Windows statusline hotfix

Ruflo v3.26.1 緊急修復 Windows 用戶的 statusline 顯示問題——狀態列只顯示 2 行且 intelligence percentage 卡在 0%。根本原因：代碼重複加上 `2>/dev/null` 重定向，但 Node execSync 本身已透過 stdio: ['pipe','pipe','pipe'] 自動捕獲 stderr；在 Windows cmd.exe 上 /dev/null 不存在，導致每次委派都失敗且無聲消退，進而回退到硬編碼的 0% 預設值。此缺陷源自 PR #2337（2026-06-10 的委派快取修復），在 v3.26.0 被真實用戶發現。已移除冗餘重定向並新增迴歸測試。已發布 @claude-flow/cli@3.26.1、claude-flow@3.26.1、ruflo@3.26.1。

### 重點
- Windows cmd.exe 無法理解 POSIX /dev/null，導致委派失敗無聲消退——跨平台兼容陷阱
- Node execSync 已內建 stderr 捕獲，勿重複加重定向（stdio 設定優先）
- 已新增迴歸測試防止重發，已知後續：getGitInfo() 仍需修復 Windows git info 讀取

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.26.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fix 
 Fixes a real bug reported by a Windows user: the statusline was only showing 2 lines (missing the 
promo/insight row) with the intelligence percentage stuck at 0%. 
 Root cause: the statusline's CLI delegation command appended 2&gt;/dev/null to every candidate 
command. Node's execSync already captures/discards stderr via stdio: ['pipe','pipe','pipe'] 
regardless of shell, so the redirect was redundant on POSIX — and actively broken on Windows, where 
 cmd.exe (execSync's default shell) doesn't understand /dev/null . Every delegation attempt failed 
silently, so every render fell back to a hardcoded 0% intelligence value, and since the promo memo 
cache is only ever seeded by a successful delegation, the promo row could never populate either. 
 Pre-existing since the #2337 delegation-caching fix (2026-06-10) — not introduced in 3.26.0, just 
surfaced by a real user on that release. Fixed by removing the redundant redirect; added a regression 
test pinning it can't come back. 
 Known follow-up (not fixed here): getGitInfo() still uses a POSIX-only sh -c script to read 
the git username/branch shown in the header — will show generic "user" with no branch on native 
Windows. Separate, smaller-impact issue, left out of this hotfix to keep it minimal and reviewable. 
 Packages published 
 @claude-flow/cli@3.26.1 , claude-flow@3.26.1 , ruflo@3.26.1 — latest / alpha / v3alpha dist-tags 
all aligned.

</details>