---
id: inbox_999d3b60
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0148-claude-mem-releases-v13-12-1-b308]]"
title: "v13.12.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.12.1
source: claude-mem-releases
published_at: 2026-07-23T06:21:49+00:00
fetched_at: 2026-07-24T01:58:32.645173+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.12.1 修復無限 worker 重啟迴圈。根本原因：worker-script resolver 按 mtime 排列 plugin cache dirs，當 Claude Code 在被淘汰版本目錄戳上 .orphaned_at（bump mtime）時，每次重啟都重新優先舊版本，同時新版本 hook 持續要求重啟 → 生成數百進程直到主機進程表耗盡。修復：四個 resolvers（worker successor、MCP launcher、Codex Windows launcher、POSIX hook prelude）現按版本排列 cache dirs（不按 mtime），跳過孤立標記 dirs，共享一個決定性版本 oracle（checkVersionMatch），使重啟迴圈結構上不可能。所有版本推薦升級；舊 resolver 在升級期間執行，下一次升級後機器受保護。"
key_points:
  - "mtime 作為版本決策真相來源不可靠：bump mtime 導致舊版本重新優先 → structural antipattern"
  - "四個獨立 resolvers 不共享版本邏輯造成功能發散（checkVersionMatch 統一後修復）"
  - "修復使迴圈在架構層級不可能：無法同時 rank 為新和舊版本，版本 oracle 是唯一真相"
tags: [claude-mem, plugin-cache, version-resolution, mtime-antipattern]
topics: [foundation_models.claude]
importance: 5
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## v13.12.1

claude-mem v13.12.1 修復無限 worker 重啟迴圈。根本原因：worker-script resolver 按 mtime 排列 plugin cache dirs，當 Claude Code 在被淘汰版本目錄戳上 .orphaned_at（bump mtime）時，每次重啟都重新優先舊版本，同時新版本 hook 持續要求重啟 → 生成數百進程直到主機進程表耗盡。修復：四個 resolvers（worker successor、MCP launcher、Codex Windows launcher、POSIX hook prelude）現按版本排列 cache dirs（不按 mtime），跳過孤立標記 dirs，共享一個決定性版本 oracle（checkVersionMatch），使重啟迴圈結構上不可能。所有版本推薦升級；舊 resolver 在升級期間執行，下一次升級後機器受保護。

### 重點
- mtime 作為版本決策真相來源不可靠：bump mtime 導致舊版本重新優先 → structural antipattern
- 四個獨立 resolvers 不共享版本邏輯造成功能發散（checkVersionMatch 統一後修復）
- 修復使迴圈在架構層級不可能：無法同時 rank 為新和舊版本，版本 oracle 是唯一真相

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.12.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fix: worker restart storm 
 Fixes an infinite worker restart loop triggered by plugin upgrades. The worker-script resolver ranked plugin cache directories by mtime , so when Claude Code stamped a superseded version dir with .orphaned_at (bumping its mtime), every restart respawned the old version while hooks on the new version kept demanding a restart — spawning hundreds of processes until the host machine exhausted its process table. 
 All four resolvers (worker successor, MCP launcher, Codex Windows launcher, POSIX hook prelude) now rank cache dirs by version — never mtime — skip orphan-stamped dirs, and share one deterministic version oracle with the staleness detector ( checkVersionMatch ), making the restart loop structurally impossible. 
 Recommended upgrade for all users. Note: the vulnerable resolver is the one running during an upgrade, so machines are protected from the next upgrade onward. 
 Details: #3371

</details>