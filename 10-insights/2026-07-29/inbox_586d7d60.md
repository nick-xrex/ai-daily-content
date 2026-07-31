---
id: inbox_586d7d60
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_586d7d60]]"
title: "Ruflo v3.32.36 — Trustworthy Signals, Portable Codex Workflows"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.36
source: ruflo-releases
published_at: 2026-07-29T19:13:55+00:00
fetched_at: 2026-07-31T01:28:28.443306+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.36 讓 agent 觀察到的資訊與 runtime 實際執行一致。Embedding 命令現顯示是否使用 deterministic mock fallback；routing metrics 區分 confidence 和 measured outcome 成兩個獨立信號；swarm status 改讀 canonical agent state；learned patterns 保留觸發的 task description 便於追蹤。Codex 新增 native read-only ruflo-status skill；dual-mode memory workers 統一使用 CLAUDE_FLOW_DB_PATH；大型 MCP catalog 可用 --tools 過濾（memory,swarm,hooks）以適配小 context 模型；project/plugin hook overlap 用 atomic event claim 去重。新命令包括 `ruflo embeddings status`、`ruflo hooks metrics`、`ruflo swarm status`、`ruflo memory distill`。Witness 驗證用 Node 內建 Ed25519；MCP images 用 Node 24 LTS。驗證：171 CLI changed-surface tests + 235 Codex + 559 security + 640 federation；22/22 hook integration（exactly-once behavior）；20 個並行 outcome writer；37 個 release invariants pass。"
key_points:
  - "信任信號三部曲：(1) embedding 顯示是否 grounded（真實 vs mock fallback），(2) routing metrics 分離 confidence 和 measured outcome，(3) learned patterns 保留 task description 便於審計"
  - "MCP catalog 可用 --tools memory,swarm,hooks 等選擇器過濾，減少 schema overhead；ruflo doctor 量化 catalog/schema 成本"
  - "Dual-mode (Claude Code + Codex) 初始化統一 DB path；Codex skill set 含 swarm orchestration、memory management、SPARC methodology、security audit、GitHub automation、performance analysis"
tags: [signal-grounding, embedding-transparency, routing-confidence, learned-patterns]
topics: [agents.mcp]
importance: 5
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Ruflo v3.32.36 — Trustworthy Signals, Portable Codex Workflows

Ruflo v3.32.36 讓 agent 觀察到的資訊與 runtime 實際執行一致。Embedding 命令現顯示是否使用 deterministic mock fallback；routing metrics 區分 confidence 和 measured outcome 成兩個獨立信號；swarm status 改讀 canonical agent state；learned patterns 保留觸發的 task description 便於追蹤。Codex 新增 native read-only ruflo-status skill；dual-mode memory workers 統一使用 CLAUDE_FLOW_DB_PATH；大型 MCP catalog 可用 --tools 過濾（memory,swarm,hooks）以適配小 context 模型；project/plugin hook overlap 用 atomic event claim 去重。新命令包括 `ruflo embeddings status`、`ruflo hooks metrics`、`ruflo swarm status`、`ruflo memory distill`。Witness 驗證用 Node 內建 Ed25519；MCP images 用 Node 24 LTS。驗證：171 CLI changed-surface tests + 235 Codex + 559 security + 640 federation；22/22 hook integration（exactly-once behavior）；20 個並行 outcome writer；37 個 release invariants pass。

### 重點
- 信任信號三部曲：(1) embedding 顯示是否 grounded（真實 vs mock fallback），(2) routing metrics 分離 confidence 和 measured outcome，(3) learned patterns 保留 task description 便於審計
- MCP catalog 可用 --tools memory,swarm,hooks 等選擇器過濾，減少 schema overhead；ruflo doctor 量化 catalog/schema 成本
- Dual-mode (Claude Code + Codex) 初始化統一 DB path；Codex skill set 含 swarm orchestration、memory management、SPARC methodology、security audit、GitHub automation、performance analysis

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.36)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.36 — Trustworthy Signals, Portable Codex Workflows

Ruflo v3.32.36: Trustworthy Signals, Portable Codex Workflows 
 Ruflo v3.32.36 makes the information an agent sees line up with what the 
runtime is actually doing. Embedding commands now disclose when they are using 
the deterministic mock fallback, routing metrics distinguish confidence from 
measured outcomes, swarm status reads canonical agent state, and learned 
patterns preserve the task description that caused them. 
 The release also makes mixed Claude Code and Codex installations easier to 
operate. Codex receives a native read-only Ruflo status skill, dual-mode memory 
workers share one database path, large MCP catalogs can be filtered for 
small-context models, and project/plugin hook overlap is claimed exactly once. 
Hermetic witness verification and Node 24 MCP images strengthen the release 
path without adding a runtime dependency. 
 Install or upgrade 
 npm install --global ruflo@3.32.36
ruflo doctor 
 Existing projects remain compatible. The default MCP tool set is unchanged, 
legacy memory state remains readable, explicit database-path overrides are 
preserved, and mock embeddings remain available. The difference is that 
degraded or unmeasured states are now reported honestly instead of being 
presented as grounded semantic results or routing accuracy. 
 Use a smaller MCP catalog 
 Keep the default full catalog: 
 ruflo mcp start 
 Or select only the capabilities a constrained model needs: 
 ruflo mcp start --tools memory,swarm,hooks 
 The equivalent environment form is useful in MCP host configuration: 
 CLAUDE_FLOW_MCP_TOOLS=memory,swarm,hooks ruflo mcp start 
 Selectors accept categories, tool-name prefixes, and exact tool names. Ruflo 
doctor now reports catalog/schema overhead so the selection can be measured. 
 Inspect grounded learning state 
 ruflo embeddings status
ruflo hooks metrics
ruflo swarm status
ruflo doctor --component memory 
 embeddings status identifies the active backend and whether semantic claims 
are grounded. Hook metrics expose average confidence and observed outcome 
success separately. The memory doctor checks structural integrity, content and 
embedding coverage, Reflexion episode coverage, and feedback critiques. 
 To populate or repair the derived reasoning tables from existing memory: 
 ruflo memory distill run
ruflo memory distill status 
 Raw memory_entries and the SONA feed remain the operational write path. 
 reasoning_patterns , episodes, embeddings, critiques, and causal edges are 
derived intelligence populated by distillation or the consolidate worker. 
 Codex and dual-mode projects 
 After initialization, Codex can invoke the native ruflo-status skill without 
receiving Cursor-specific permission JSON. Dual-mode workers now use a shared 
 CLAUDE_FLOW_DB_PATH , including worker subprocesses and relative configuration 
files, so bootstrap, writes, reads, policy checks, and background work observe 
the same database. 
 The packaged Codex skill set now includes: 
 
 swarm orchestration; 
 memory management; 
 SPARC methodology; 
 security audit; 
 GitHub automation; 
 performance analysis. 
 
 Security and verification 
 
 Witness signature verification uses Node's built-in Ed25519 support in a 
source-only checkout and preserves the legacy exit-2 precondition for an 
unbuilt full-tree verification. 
 Helper signing has one public-key source, supports a piped stdin key, uses 
 gcloud.cmd on Windows, validates Ed25519 keys, and redacts failures. 
 MCP bridge images use the supported Node 24 LTS line. 
 MetaHarness wrappers preserve structured HIGH findings when the upstream 
scanner exits non-zero. 
 Root and packaged hook helpers are byte-identical and covered by a signed 
four-helper manifest. 
 
 What changed 
 
 Reports the actual embedding backend and suppresses unsupported semantic 
interpretations while the mock fallback is active. 
 Replaces misleading “Routing Accuracy” output with average confidence and 
measured outcome-success signals. 
 Fixes learned-pattern success/failure counts and retains task descriptions in 
the learning write. 
 Reads canonical per-agent IDs and statuses for agent list and 
 swarm status . 
 Fixes statusline install discovery, numeric version comparison, project-root 
resolution, and legacy nested-intelligence migration. 
 Keeps non-TTY spinner output clean and erases TTY spinner lines correctly. 
 Deduplicates overlapping project/plugin post-edit and session-end side 
effects using an atomic event claim. 
 Adds MCP tool filtering and schema-overhead diagnostics. 
 Repairs dual-mode Codex memory-path consistency and packaged skill assets. 
 Adds memory distillation episode embeddings, historical backfill, critique 
preservation, and strict doctor coverage checks. 
 
 Validation 
 
 All 23 V3 workspace packages built successfully. 
 171 changed-surface CLI tests passed. 
 Codex passed 235 tests, security passed 559, and federation passed 640. 
 Ruflo core hook integration passed 22/22, including duplicate-event 
exactly-once behavior. 
 MetaHarness passed its complete plugin regression matrix, including 
structured finding preservation. 
 Helper signing security, hermetic witness, MCP security lock, scan-format, 
and 37 release invariants passed. 
 The stable release workflow additionally installs and tests immutable tarball 
archives for @claude-flow/cli , claude-flow , and ruflo before publishing 
those exact bytes. 
 
 This release resolves the current runtime and verification defects tracked in 
 #2847 , 
 #2821 , 
 #2818 , 
 #2816 , 
 #2814 , 
 #2812 , 
 #2811 , 
 #2810 , 
 #2809 , 
 #2808 , 
 #2807 , 
 #2805 , 
 #2766 , 
 #2765 , 
 #2750 , 
 #2729 , 
 #2726 , 
 #2677 , 
 #2675 , and 
 #2674 .

</details>