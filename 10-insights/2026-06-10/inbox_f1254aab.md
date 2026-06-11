---
id: inbox_f1254aab
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_f1254aab]]"
title: "v3.10.41 — community bug fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.41
source: ruflo-releases
published_at: 2026-06-10T15:48:22+00:00
fetched_at: 2026-06-11T00:23:32.315890+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.10.41 發布三項社區 bug 修復及 ADR-147 嵌套子代理基礎設施。核心問題：statusline 每次渲染呼叫 `npx --yes @claude-flow/cli@latest`，強制 npm 重複解析，在 12 核心機器上導致負載平均 40-65、每進程 CPU 55-90%。修復：新增 resolveCliBin() 優先使用已安裝 bin/cli.js，快取 TTL 10s→60s。另修復子代理終端控制丟失（新增 await）及 current.json 原子寫入與自我修復。基礎設施面新增嵌套深度=5 支援及安全基準文件。"
key_points:
  - "statusline 性能最佳化：npm re-resolution 改為已安裝 bin + 快取 TTL 10s→60s，削減 12 核機器 40-65 負載"
  - "子代理終端修復：spawnClaudeCodeInstance() await 強制子進程在父進程返回前完成初始化，防止終端功能查詢漏到下一個 shell prompt"
  - "session.json 原子寫入 + 自我修復：所有 5 處寫入採 temp-file + rename() 模式，corrupt 檔案可自動復原"
tags: [performance-optimization, npm-caching, cli-reliability, atomic-writes]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.41 — community bug fixes

RuFlo v3.10.41 發布三項社區 bug 修復及 ADR-147 嵌套子代理基礎設施。核心問題：statusline 每次渲染呼叫 `npx --yes @claude-flow/cli@latest`，強制 npm 重複解析，在 12 核心機器上導致負載平均 40-65、每進程 CPU 55-90%。修復：新增 resolveCliBin() 優先使用已安裝 bin/cli.js，快取 TTL 10s→60s。另修復子代理終端控制丟失（新增 await）及 current.json 原子寫入與自我修復。基礎設施面新增嵌套深度=5 支援及安全基準文件。

### 重點
- statusline 性能最佳化：npm re-resolution 改為已安裝 bin + 快取 TTL 10s→60s，削減 12 核機器 40-65 負載
- 子代理終端修復：spawnClaudeCodeInstance() await 強制子進程在父進程返回前完成初始化，防止終端功能查詢漏到下一個 shell prompt
- session.json 原子寫入 + 自我修復：所有 5 處寫入採 temp-file + rename() 模式，corrupt 檔案可自動復原

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.41)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.10.41 — community bug fixes

Three community bug fixes plus the ADR-147 nested-subagent infrastructure landed since v3.10.40. PATCH bump — no API breaks. 
 Community bug fixes (PR #2346 ) 
 fix(statusline) : resolve installed CLI bin + bump cache TTL 10s→60s ( #2337 ) 
 Thanks @shaal for the detailed report with %CPU measurements. The statusline was calling npx --yes @claude-flow/cli@latest hooks statusline --json on every render — the @latest tag forced npm registry re-resolution per call. With ~6 concurrent sessions on a 12-core box: load average 40-65, each npm exec consuming 55-90% of a core. 
 Fix: new resolveCliBin() finds an installed bin/cli.js (project / monorepo / plugin marketplace / global node_modules — covers ~/.npm-global and similar custom-prefix layouts) and invokes it via process.execPath directly. Falls back to npx --prefer-offline @claude-flow/cli (no @latest ) when nothing's installed. Cache TTL 10s→60s. Applied to both the dogfood helper and the ruflo init generator template. 
 fix(hive-mind) : await spawned claude before returning ( #2297 ) 
 Thanks @clement-livdeo for the XTVERSION-on-prompt diagnostic — that single string nailed the root cause: the parent process exited immediately after spawn, the child claude lost its controlling terminal mid-init, and the terminal's capability-query response leaked onto the next shell prompt. 
 Fix: spawnClaudeCodeInstance() now awaits the child's exit (or error) before returning. The existing claudeProcess.on('exit', ...) log lines actually print now, and the non-interactive ( -p / --non-interactive ) path completes only after Claude Code does. 
 fix(session) : atomic writes to current.json + corrupted-file self-heal ( #2307 ) 
 Thanks @BIWizzard for the diff — same class as #1707 / #1637 which were fixed elsewhere with atomic writes; session.js was missed in that sweep. Per-fd-offset semantics in writeFileSync meant a shorter payload could overwrite the start of a longer one without shrinking the file, leaving the longer payload's tail dangling past the end (valid JSON + trailing garbage). 
 Fix: all 5 session-file writes go through a new atomicWrite() (temp file + rename() ). restore() wraps JSON.parse in try/catch so existing corrupt files self-heal by starting a fresh session instead of throwing. 
 Infrastructure 
 ADR-147 — nested subagent depth=5 integration (PR #2336 ) 
 Captures Boris Cherny's nested-subagent announcement with full empirical block, the ruflo agent files (8 new agents + 1 skill) that opt into nested spawning via tools: [Task, ...] , P2 stage 1 (CLI flags + MCP schema for capturing parent_agent_id in the post-task hook), and a regression probe in scripts/probe-nested-spawn-depth.mjs . 
 Empirically determined: declaring tools: [Task] in YAML is necessary but not sufficient in CLI 2.1.169 — the runtime applies a hardcoded denylist that strips Task at parent→child spawn time. Documented in the ADR with the spawn-tree the day the upstream denylist lifts. 
 Security baseline (PR #2340 ) 
 docs/security/socket-baseline.md documents every category in the Socket.dev alert page for claude-flow@3.10.40 — what's protected by root overrides , what's not cleanly fixable from inside claude-flow (consumer-side npm overrides only apply at the dep-tree root), what's inherent to a CLI agent platform (filesystem/network/shell access etc.), and the false positives (Socket's "did you mean z-schema?" suggestion against zod ). Also removes the broken pages.yml workflow that had failed 10+ consecutive runs. 
 Open follow-ups from the same triage pass 
 
 #2305 — embedding model/dimension ignored at runtime (architectural; awaiting reporter's config-chain design as PR) 
 #2296 — 7 controllers null from version skew between @claude-flow/memory@3.0.0-alpha.19 and agentdb@3.0.0-alpha.16 (needs coordinated package republish) 
 
 Install 
 npx ruflo@latest
 # or 
npx claude-flow@latest
 # or 
npm install @claude-flow/cli@latest 
 All three packages at 3.10.41 across all dist-tags (latest, alpha, v3alpha). 
 🤖 Generated with RuFlo

</details>