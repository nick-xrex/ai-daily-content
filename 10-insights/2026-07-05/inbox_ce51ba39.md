---
id: inbox_ce51ba39
date: 2026-07-05
source_ref: "[[00-inbox/2026-07-05/2254-claude-mem-releases-v13-10-2-3ca1]]"
title: "v13.10.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.10.2
source: claude-mem-releases
published_at: 2026-07-05T22:47:23+00:00
fetched_at: 2026-07-07T00:38:26.159229+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Mem 13.10.2 著重跨平台穩定性和 worker/runtime 正確性修復。關鍵改進包括：Worker 主機正確解析 CLAUDE_MEM_WORKER_HOST 環境變數，IPv6 位址在健康檢查和顯示 URL 中正確加括號；統一 worker bundle 防止多個建置造成版本偏差；Windows 下移除 shell:true 漏洞，codex 鉤子改用 Windows 可執行命令；安裝修復恢復市場運行時根目錄和缺失的 plugin/sqlite 模組；SQLite 實現原子設定寫入加 busy_timeout 避免併發存取衝突；worktree 相對 gitdir 指標正確解析。新增發布分支指南（main / core-dev / community-edge）。"
key_points:
  - "Worker 主機 IPv6 支援：正確加括號處理 IPv6 文字標記，健康檢查與顯示 URL 一致"
  - "原子 SQLite 設定寫入 + busy_timeout：解決 worker 與 hook 併發存取的 SQLITE_BUSY 衝突"
  - "Windows 命令生成改進：移除 shell:true footgun，codex 鉤子改為 Windows 可執行命令"
tags: [cross-platform, worker-stability, sqlite-atomic-writes, windows-compat]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.10.2

Claude Mem 13.10.2 著重跨平台穩定性和 worker/runtime 正確性修復。關鍵改進包括：Worker 主機正確解析 CLAUDE_MEM_WORKER_HOST 環境變數，IPv6 位址在健康檢查和顯示 URL 中正確加括號；統一 worker bundle 防止多個建置造成版本偏差；Windows 下移除 shell:true 漏洞，codex 鉤子改用 Windows 可執行命令；安裝修復恢復市場運行時根目錄和缺失的 plugin/sqlite 模組；SQLite 實現原子設定寫入加 busy_timeout 避免併發存取衝突；worktree 相對 gitdir 指標正確解析。新增發布分支指南（main / core-dev / community-edge）。

### 重點
- Worker 主機 IPv6 支援：正確加括號處理 IPv6 文字標記，健康檢查與顯示 URL 一致
- 原子 SQLite 設定寫入 + busy_timeout：解決 worker 與 hook 併發存取的 SQLITE_BUSY 衝突
- Windows 命令生成改進：移除 shell:true footgun，codex 鉤子改為 Windows 可執行命令

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.10.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release focused on cross-platform stability and worker/runtime correctness. 
 Fixes 
 
 Worker host : clients now honor CLAUDE_MEM_WORKER_HOST (the address the server actually binds), with IPv6 literals bracketed correctly in health checks and display URLs. 
 Worker identity : cache/marketplace/MCP/CLI/restart launches converge on one worker bundle (stops version-skew from two builds on one port). 
 Windows : centralized spawn shims remove the shell:true footgun; codex hooks emit a Windows-executable command instead of a POSIX-only one. 
 Install : repair now restores the marketplace runtime root (not just the cache); ships the plugin/sqlite runtime modules that were causing MODULE_NOT_FOUND on clean installs. 
 SQLite/settings : atomic settings writes, busy_timeout to avoid SQLITE_BUSY under concurrent worker/hook access, a migration column re-check, and removal of an index create that could crash boot on legacy duplicate rows. 
 Supervisor : preserves HTTPS_PROXY and Bedrock/Vertex skip-auth env for the SDK subprocess. 
 Worktree : relative gitdir: pointers resolved correctly. 
 
 Docs 
 
 New Release Branches guide (main / core-dev / community-edge) with instructions for running the non-stable lines locally. 
 
 Deliberately excluded: client-side observer truncation (kept out per #3096 ) and project-identity re-keying (kept the #2663 repo-root key).

</details>