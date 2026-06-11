---
id: inbox_273cb7c5
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-claude-mem-releases-v13-5-6-4829]]"
title: "v13.5.6"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.6
source: claude-mem-releases
published_at: 2026-06-11T03:07:33+00:00
fetched_at: 2026-06-11T22:06:45.740583+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Mem v13.5.6 大幅重構 worker 生命週期管理，解決重啟競態、EADDRINUSE 失敗與「健康 worker 誤判為不運行」問題。核心創新是自我更替 worker——舊 worker 在港口釋放時立即生成後繼者，新舊決不共存，避免外部程序競搶生成；同時透過 spawn.lock（60 秒逾期策略）序列化 hook、MCP server 和 CLI 的所有生成路徑。重啟驗證改進——重啟後輪詢 /api/health 直到 pid 和版本同時更新，失敗則退出代碼 1。PID 檔案降級為診斷用途，活性真值改由 port + /api/health 決定，防止舊 worker 覆寫後繼者的 PID 檔案。驗證包括三次連續重啟無重複 /EADDRINUSE 事件，以及模擬原始競態下 16 秒內收斂歸零，共 2,247 項測試通過。"
key_points:
  - "自我更替 worker 模式：舊 worker 生成後繼者，避免新舊共存與外部競態"
  - "spawn.lock 單一生成閘門：序列化所有生成路徑，防止 hook、MCP server、CLI 碰撞重複生成"
  - "活性真值改由 port + /api/health 決定而非 PID 檔案，防止舊 worker 污染後繼者診斷資訊"
tags: [worker-lifecycle, reliability, mcp-server, service-restart]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.6

Claude Mem v13.5.6 大幅重構 worker 生命週期管理，解決重啟競態、EADDRINUSE 失敗與「健康 worker 誤判為不運行」問題。核心創新是自我更替 worker——舊 worker 在港口釋放時立即生成後繼者，新舊決不共存，避免外部程序競搶生成；同時透過 spawn.lock（60 秒逾期策略）序列化 hook、MCP server 和 CLI 的所有生成路徑。重啟驗證改進——重啟後輪詢 /api/health 直到 pid 和版本同時更新，失敗則退出代碼 1。PID 檔案降級為診斷用途，活性真值改由 port + /api/health 決定，防止舊 worker 覆寫後繼者的 PID 檔案。驗證包括三次連續重啟無重複 /EADDRINUSE 事件，以及模擬原始競態下 16 秒內收斂歸零，共 2,247 項測試通過。

### 重點
- 自我更替 worker 模式：舊 worker 生成後繼者，避免新舊共存與外部競態
- spawn.lock 單一生成閘門：序列化所有生成路徑，防止 hook、MCP server、CLI 碰撞重複生成
- 活性真值改由 port + /api/health 決定而非 PID 檔案，防止舊 worker 污染後繼者診斷資訊

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Worker restart: single source of truth ( #2894 ) 
 This release rearchitects worker lifecycle management to eliminate the restart races behind version-recycle ping-pong storms, EADDRINUSE failures, and "healthy worker reports as not running" lies. 
 Highlights 
 
 Self-replacing worker — on restart, the dying worker spawns its own successor the moment its port frees. Old and new workers never coexist, and nothing external races to spawn into the gap. Hooks wait for the successor and lazy-spawn only as a fallback, at most one recycle per hook event. 
 Restarts prove themselves — worker-service restart now polls /api/health until the pid changes AND the version matches the new build, prints Worker restart verified (pid, version) , and exits 1 on failure instead of reporting success over a dead or stale worker. The daemon's generic start-failure path also exits 1 now. 
 One spawn gate — a wx -flag lockfile ( spawn.lock , 60s mtime staleness, owner-checked release) serializes every external spawn path: hook lazy-spawn, MCP server, and the CLI restart fallback. Lock losers wait for the winner's worker instead of colliding. The two divergent Bun resolvers are unified (closing the kill-then-can't-respawn path), and the MCP server now prefers the marketplace worker script over stale plugin-cache copies. 
 PID file demoted to diagnostics — liveness truth is the port + /api/health . Every PID-file deletion is owner-guarded, so a dying worker can never clobber its successor's file; status reports pid/version/uptime/workerPath from health alone and survives PID-file deletion. 
 First-run fix — settings bootstrap notices now go to stderr, never stdout: the very first hook invocation on a fresh install no longer emits corrupted JSON to the hook framework. 
 Build chain hardened — the dev sync-script's installed-version cache mirror (which wrote new code into old version dirs, manufacturing permanent version disagreement) and its duplicate HTTP restart trigger are deleted; build-and-sync restarts through one verified CLI path. 
 Test hygiene — the test suite can no longer touch the real ~/.claude-mem (a preload tripwire isolates every run), ending sentinel-PID and corrupt-JSON pollution of production state. 
 
 Validation 
 Triple-restart soak (3× consecutive verified restarts, zero duplicate/EADDRINUSE events), plus a live re-creation of the original stale-launcher bug under concurrent session crossfire: one recycle per stale instance, convergence in 16 seconds, zero ping-pong over an 8.5-minute watch. 2,247 tests pass. 
 🤖 Generated with Claude Code

</details>