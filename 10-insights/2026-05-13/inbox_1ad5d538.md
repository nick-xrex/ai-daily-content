---
id: inbox_1ad5d538
date: 2026-05-13
source_ref: "[[00-inbox/2026-05-13/1800-ruflo-releases-v3-7-0-alpha-33-14-critical-fixes-since-fd57]]"
title: "v3.7.0-alpha.33 — 14 critical fixes since alpha.27"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.33
source: ruflo-releases
published_at: 2026-05-13T17:34:12+00:00
fetched_at: 2026-05-22T18:11:11.705300+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.7.0-alpha.33 為綜合批次 release，累計 14 個 critical fix（alpha.28→.32 期間逐個發布但無 release notes）。Memory 層 8 fixes：#1947/#1952：vector_indexes dim 768→384 mismatch 導致 memory_search 返回 0（default model Xenova/all-MiniLM-L6-v2 為 384-dim）；#1945/#1946：memory-bridge hardcoded <cwd>/.swarm/memory.db 無視 CLAUDE_FLOW_MEMORY_PATH；#1941：非預設 namespace search 返回 0；#1940：memory_bridge_status 用分頁長度而非 .total；#1939：Win32 slug 邏輯遺漏 backslash/colon/whitespace。Hooks 層 2 fixes：#1944（pre-bash TypeError）、#1943（global-install module not found）。UI 層 2 fixes：#1953（statusline hook scan 擴大至 80 行）、#1951（版本 hard-code）。驗證 1 unblock：#1949（cookies@0.9.1 403 blocked，pin 0.9.0）。新增 2 個 CI guard 鎖定 vector-dim 與 hook-handler-prompt 不變量。"
key_points:
  - "Vector index dimension 768→384 mismatch 導致 memory_search 返回 0（default model 為 384-dim），影響 3 個相關 issue #1947/#1952"
  - "Memory store path hard-code 在 <cwd>/.swarm/memory.db，無視 CLAUDE_FLOW_MEMORY_PATH 環境變數與 claude-flow.config.json（#1945/#1946）"
  - "Pre-bash hook 在 global-install 時出現 MODULE_NOT_FOUND，改為先探測 project-local 再 fallback $HOME"
tags: [vector-dimension-mismatch, path-hardcoding, memory-subsystem]
topics: []
importance: 4
novelty: 1
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.33 — 14 critical fixes since alpha.27

RuFlo v3.7.0-alpha.33 為綜合批次 release，累計 14 個 critical fix（alpha.28→.32 期間逐個發布但無 release notes）。Memory 層 8 fixes：#1947/#1952：vector_indexes dim 768→384 mismatch 導致 memory_search 返回 0（default model Xenova/all-MiniLM-L6-v2 為 384-dim）；#1945/#1946：memory-bridge hardcoded <cwd>/.swarm/memory.db 無視 CLAUDE_FLOW_MEMORY_PATH；#1941：非預設 namespace search 返回 0；#1940：memory_bridge_status 用分頁長度而非 .total；#1939：Win32 slug 邏輯遺漏 backslash/colon/whitespace。Hooks 層 2 fixes：#1944（pre-bash TypeError）、#1943（global-install module not found）。UI 層 2 fixes：#1953（statusline hook scan 擴大至 80 行）、#1951（版本 hard-code）。驗證 1 unblock：#1949（cookies@0.9.1 403 blocked，pin 0.9.0）。新增 2 個 CI guard 鎖定 vector-dim 與 hook-handler-prompt 不變量。

### 重點
- Vector index dimension 768→384 mismatch 導致 memory_search 返回 0（default model 為 384-dim），影響 3 個相關 issue #1947/#1952
- Memory store path hard-code 在 <cwd>/.swarm/memory.db，無視 CLAUDE_FLOW_MEMORY_PATH 環境變數與 claude-flow.config.json（#1945/#1946）
- Pre-bash hook 在 global-install 時出現 MODULE_NOT_FOUND，改為先探測 project-local 再 fallback $HOME

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.33)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

14 critical fixes since 3.7.0-alpha.27 
 Cumulative batch release closing out an issue-triage cycle. The prior bumps ( .28 → .32 ) shipped their fix-sets to npm immediately but had no GitHub Release writeup; this is the consolidated changelog. 
 Memory layer (8 fixes) 
 
 
 
 Issue 
 Fix 
 
 
 
 
 #1947 
 vector_indexes schema dim 768→384 (default model Xenova/all-MiniLM-L6-v2 is 384-dim — schema mismatch silently made every memory_search return 0). 
 
 
 #1942 
 Bridge search index 768 vs imported 384-dim — same root cause as #1947 , observed via the Bridge import path. 
 
 
 #1952 
 Windows: memory store ok, search returns 0 — same root cause as #1947 , observed on a Windows install. 
 
 
 #1945 
 CLI memory store reported success but didn't persist on non-default memory paths — memory-bridge.ts::getDbPath() hard-coded &lt;cwd&gt;/.swarm/memory.db and ignored CLAUDE_FLOW_MEMORY_PATH / claude-flow.config.json#memory.persistPath . 
 
 
 #1946 
 ruflo doctor reported DB "Not initialized" on a valid DB at data/memory/memory.db — same hard-coded-path family as #1945 . 
 
 
 #1941 
 memory_search returned 0 for non-default namespaces — every store path now INSERT OR IGNORE s a per-namespace vector_indexes row before the entry insert. 
 
 
 #1940 
 memory_bridge_status reported totalEntries: 0 on DBs with hundreds of rows — used listEntries({}).entries.length (page-size capped at 20) instead of .total . 
 
 
 #1939 
 Win32 memory_import_claude({allProjects:false}) returned 0 — slug logic only replaced forward slashes, never drive-colon / backslash / whitespace. 
 
 
 #1947 RC #2 
 embeddings index -a build required -c (the HNSW index is global; the flag was always informational). Now optional. 
 
 
 
 Hooks layer (2 fixes) 
 
 
 
 Issue 
 Fix 
 
 
 
 
 #1944 
 pre-bash printed `TypeError: (hookInput.command 
 
 
 #1943 
 Every Bash / Edit / Session hook fired MODULE_NOT_FOUND on a global-install layout — paths were anchored at ${CLAUDE_PROJECT_DIR} only. Now probes project-local first, falls back to $HOME . 
 
 
 
 UI / statusline (2 fixes) 
 
 
 
 Issue 
 Fix 
 
 
 
 
 #1953 
 hooks_pretrain reported patternsExtracted: 0 on Markdown-heavy repos — used a separate codeFilesScanned budget, sorts readdir code-likely dirs first, widened scan window 30→80 lines, added .tsx / .jsx / .mjs / .cjs . 
 
 
 #1951 
 Statusline showed hard-coded RuFlo V3.5 regardless of installed version — now probes ~/.claude/plugins/marketplaces/ruflo/package.json first. 
 
 
 
 Verification (1 unblock) 
 
 
 
 Issue 
 Fix 
 
 
 
 
 #1949 
 Federation plugin install 403 on cookies@0.9.1 (the latest published version, but blocked by registry security policy). Added scripts/verify-federation-plugin.sh that pins cookies@0.9.0 at the verification harness root — both Check 2 (exports) and Check 3 (breaker wire-up) pass. Workaround until upstream pipenet → koa → cookies ships a non-blocked release. 
 
 
 
 CI regression guards baked in 
 
 scripts/audit-vector-dim.mjs — fails the build if any vector_indexes row's dim ≠ 384 ( #1947 guard). 
 scripts/audit-hook-handler-prompt.mjs — fails the build if any handler / template falls back to a bare toolInput (object) instead of toolInput.command (string) ( #1944 guard). 
 
 Both wired into the existing witness-verify and hook-command-audit jobs in .github/workflows/v3-ci.yml . 
 Install 
 npx @claude-flow/cli@latest --version # 3.7.0-alpha.33 
npx ruflo@latest --version # 3.7.0-alpha.33 
npx claude-flow@latest --version # 3.7.0-alpha.33 
 All three packages on alpha , latest , and v3alpha tags (where applicable). 
 Still open (not in this release) 
 
 #1948 — Win32 random temp files in repo root ( 0) , toastr.error(... ). Vague repro; needs reporter to narrow which tool path creates them. 
 #1937 — Feature request: per-file exclusion for memory_import_claude . Design work, not a bug. 
 
 
 PRs in this release: #1956 · #1957 · #1959 · #1960 · #1961 · #1962 · #1963 · #1964 · #1965

</details>