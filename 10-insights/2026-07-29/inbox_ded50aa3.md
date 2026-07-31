---
id: inbox_ded50aa3
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_ded50aa3]]"
title: "Ruflo v3.32.37 — Complete Reports, Consistent Initialization"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.37
source: ruflo-releases
published_at: 2026-07-29T19:46:23+00:00
fetched_at: 2026-07-31T01:28:28.441987+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.37 修復驗證 v3.32.36 時發現的多個相容性 bugs。MetaHarness readiness verdicts 改為保持 machine-readable 格式，即使 repo blocked 時也保留完整 exit code（1 vs 2）。Memory init 現正確尊重 CLAUDE_FLOW_DB_PATH 環境變數，與後續所有操作共用同一 DB 路徑。Init --dual 標記同時執行 Claude Code 和 Codex native initializer，完整保留 Claude Code scaffold 同時添加 Codex assets，並移除百個以上無實裝的 placeholder skills。ADR metadata parsing 支援 bullet-prefixed Date/Tags 格式；ADR records 用 explicit upsert 和 deterministic keys；legacy NULL status rows 一致視為 live。Session-end 去重了 project/plugin post-edit side effects。修復解決 11 個 issues。驗證：12 CLI contract + 238 Codex + 559 security + 640 federation tests；22/22 ADR & hook smoke；23 V3 workspace packages 全部編譯成功。"
key_points:
  - "Memory init 與 dual-mode bootstrap、background workers 統一共享 CLAUDE_FLOW_DB_PATH，完成 portable init 的核心承諾"
  - "ADR metadata、記錄、去重用 deterministic semantic keys + explicit upsert，保留 legacy 相容性同時消除重複"
  - "Codex 完整初始化去掉 100+ placeholder skills，只安裝 canonical implementations，大幅降低初始化複雜度"
tags: [initialization, dual-mode, adr-management, database-portability]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruflo v3.32.37 — Complete Reports, Consistent Initialization

Ruflo v3.32.37 修復驗證 v3.32.36 時發現的多個相容性 bugs。MetaHarness readiness verdicts 改為保持 machine-readable 格式，即使 repo blocked 時也保留完整 exit code（1 vs 2）。Memory init 現正確尊重 CLAUDE_FLOW_DB_PATH 環境變數，與後續所有操作共用同一 DB 路徑。Init --dual 標記同時執行 Claude Code 和 Codex native initializer，完整保留 Claude Code scaffold 同時添加 Codex assets，並移除百個以上無實裝的 placeholder skills。ADR metadata parsing 支援 bullet-prefixed Date/Tags 格式；ADR records 用 explicit upsert 和 deterministic keys；legacy NULL status rows 一致視為 live。Session-end 去重了 project/plugin post-edit side effects。修復解決 11 個 issues。驗證：12 CLI contract + 238 Codex + 559 security + 640 federation tests；22/22 ADR & hook smoke；23 V3 workspace packages 全部編譯成功。

### 重點
- Memory init 與 dual-mode bootstrap、background workers 統一共享 CLAUDE_FLOW_DB_PATH，完成 portable init 的核心承諾
- ADR metadata、記錄、去重用 deterministic semantic keys + explicit upsert，保留 legacy 相容性同時消除重複
- Codex 完整初始化去掉 100+ placeholder skills，只安裝 canonical implementations，大幅降低初始化複雜度

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.37)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.37 — Complete Reports, Consistent Initialization

Ruflo v3.32.37: Complete Reports, Consistent Initialization 
 Ruflo v3.32.37 closes the follow-up defects found while verifying v3.32.36 
against older open bug reports. MetaHarness readiness verdicts remain 
machine-readable even when a repository is blocked, memory initialization 
uses the same configured database path as every later operation, and dual 
Claude Code/Codex initialization now installs both native surfaces. 
 The release also removes unbacked Codex skill placeholders, makes ADR indexing 
idempotent, repairs legacy live-memory row visibility, and bounds the 
quadratic work in session-end intelligence consolidation. 
 Install or upgrade 
 npm install --global ruflo@3.32.37
ruflo doctor 
 Existing projects remain compatible. The stable train still contains exactly 
the three supported packages: @claude-flow/cli , claude-flow , and ruflo . 
 MetaHarness readiness is data 
 ruflo metaharness genome --path . --format json 
 Upstream MetaHarness intentionally uses exit 1 for needs-work and exit 2 for 
 blocked . Ruflo now preserves those valid reports instead of replacing them 
with a generic subprocess error: 
 {
 "risk_score" : 0.72 ,
 "verdict" : " blocked " ,
 "verdictExitCode" : 2 
} 
 The Ruflo wrapper exits successfully for a valid report so CLI and MCP callers 
can consume it. --alert-on-risk-above still exits 1 when its policy threshold 
is crossed, and malformed or missing reports still fail with exit 2. 
 Initialization and portability 
 
 memory init honors CLAUDE_FLOW_DB_PATH , completing the shared-path 
contract used by dual-mode bootstrap and background workers. 
 init --dual runs both native initializers, preserving the full Claude Code 
scaffold while adding Codex assets. 
 Root .gitignore protection covers .env secrets in initialized projects. 
 Codex full init installs canonical skill implementations only; it no longer 
generates more than one hundred placeholder skills that appear usable but 
have no implementation. 
 Every tracked shell and Windows hook shim now resolves the same stable Ruflo 
dist-tag. 
 
 ADR and memory correctness 
 
 ADR metadata parsing accepts the bullet-prefixed Date, Tags, and relationship 
format emitted by adr-create . 
 ADR records use explicit upsert semantics and stable keys. 
 ADR relationships use deterministic semantic keys and are deduplicated 
within an import, while verification remains compatible with legacy keys. 
 ADR creation guidance uses the real AgentDB key / value contract. 
 Native memory CRUD treats legacy NULL status rows consistently as live. 
 Intelligence consolidation deduplicates by content before graph creation and 
caps similarity comparisons while preserving temporal edges. 
 
 Validation 
 
 Blocked-genome CLI and MCP fixtures preserve the complete verdict. 
 ADR smoke: 22/22; hook-shim smoke: 12/12. 
 Release gates: 12 CLI contract, 238 Codex, 559 security, and 640 
federation tests pass. 
 All 23 buildable V3 workspace packages compile successfully. 
 Focused MetaHarness, memory-path, dual-init, canonical-skill, ADR parser, 
ADR idempotency, memory visibility, and consolidation regressions pass. 
 The stable release workflow builds immutable archives, tests the bundled 
policy/Codex/federation runtimes, installs all three archives, publishes the 
same bytes, and installs them again from the npm registry. 
 
 This patch resolves 
 #2626 , 
 #2629 , 
 #2600 , 
 #2634 , 
 #2636 , 
 #2637 , 
 #2660 , 
 #2659 , 
 #2651 , 
 #2628 , and 
the remaining active-row visibility defect in 
 #2652 .

</details>