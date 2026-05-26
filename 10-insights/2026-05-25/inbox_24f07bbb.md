---
id: inbox_24f07bbb
date: 2026-05-25
source_ref: "[[00-inbox/2026-05-25/0014-ecc-releases-v2-0-0-rc-1-cd3b]]"
title: "v2.0.0-rc.1"
url: https://github.com/affaan-m/ECC/releases/tag/v2.0.0-rc.1
source: ecc-releases
published_at: 2026-05-25T19:36:47+00:00
fetched_at: 2026-05-26T00:19:14.418625+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ECC 2.0.0-rc.1 首次將技能包平台從 Claude Code 專用工具升級為跨多 IDE 統一層（支援 Codex、OpenCode、Cursor、Gemini、Zed、終端工作流）。涵蓋 243 項公開技能、5 項新優化技能包（平行執行優化、基準優化迴圈、資料吞吐加速、延遲關鍵系統分析、遞迴決策帳冊）。統一 MCP 慣例、Hooks、釋出把關（含供應鏈檢查、簽署驗證）。核心價值：將可重複代理行為轉化為可移植跨平台基礎設施，終止碎片化提示工程與本地習慣依賴。2568 項測試全數通過，243 項技能驗證完成。"
key_points:
  - "跨 IDE 統一基礎設施：243 項技能在 Claude Code、Codex、OpenCode、Cursor、Gemini、Zed、終端間共享 MCP 慣例、Hooks、釋出把關"
  - "5 項代理優化技能：parallel-execution-optimizer（安全平行分片、併發讀取）、benchmark-optimization-loop（測量變體、推廣把關）、data-throughput-accelerator（索引化檢查點）、latency-critical-systems（p50/p95/快取命中率/冷啟動分析）、recursive-decision-ledger（歷史勝者複用）"
  - "驗證通過：2568 項測試、243 項技能驗證、31 模組 75 元件、供應鏈檢查無密鑰洩漏"
tags: [ecc, cross-harness-portability, agent-skills, mcp-conventions, optimization-framework]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v2.0.0-rc.1

ECC 2.0.0-rc.1 首次將技能包平台從 Claude Code 專用工具升級為跨多 IDE 統一層（支援 Codex、OpenCode、Cursor、Gemini、Zed、終端工作流）。涵蓋 243 項公開技能、5 項新優化技能包（平行執行優化、基準優化迴圈、資料吞吐加速、延遲關鍵系統分析、遞迴決策帳冊）。統一 MCP 慣例、Hooks、釋出把關（含供應鏈檢查、簽署驗證）。核心價值：將可重複代理行為轉化為可移植跨平台基礎設施，終止碎片化提示工程與本地習慣依賴。2568 項測試全數通過，243 項技能驗證完成。

### 重點
- 跨 IDE 統一基礎設施：243 項技能在 Claude Code、Codex、OpenCode、Cursor、Gemini、Zed、終端間共享 MCP 慣例、Hooks、釋出把關
- 5 項代理優化技能：parallel-execution-optimizer（安全平行分片、併發讀取）、benchmark-optimization-loop（測量變體、推廣把關）、data-throughput-accelerator（索引化檢查點）、latency-critical-systems（p50/p95/快取命中率/冷啟動分析）、recursive-decision-ledger（歷史勝者複用）
- 驗證通過：2568 項測試、243 項技能驗證、31 模組 75 元件、供應鏈檢查無密鑰洩漏

**原文：** [ecc-releases](https://github.com/affaan-m/ECC/releases/tag/v2.0.0-rc.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ECC 2.0.0-rc.1 
 ECC 2.0.0-rc.1 is the first release-candidate surface for ECC as a cross-harness operating system for agentic work. 
 Claude Code remains a first-class target. Codex, OpenCode, Cursor, Gemini, Zed, and terminal-only workflows are now treated as execution surfaces that can share the same skills, rules, hooks, MCP conventions, release gates, and operator workflows. 
 What is new 
 
 243 public skills packaged across coding, research, security, media, enterprise ops, and agent workflows. 
 A rollout-derived optimization pack for agents that need measured speedups instead of one-shot prompting. 
 A public teaser Itô prediction-market skill pack for read-only research, basket comparison, oracle-style market intelligence, and risk review. Itô API access stays gated and separate from ECC Tools billing. 
 AgentShield and supply-chain follow-up surfaces after the Mini Shai-Hulud/TanStack campaign work. 
 Cross-harness package surfaces for Claude Code, Codex, OpenCode, Cursor, Gemini, Zed, and terminal workflows. 
 Release-readiness gates for preview packs, public-action approvals, release URL ledgers, operator readiness, discussion state, Linear roadmap coverage, and supply-chain checks. 
 
 New optimization skills 
 
 parallel-execution-optimizer : splits work into safe parallel lanes, separate worktrees, concurrent reads, and mergeable outputs. 
 benchmark-optimization-loop : turns vague speed goals into measured variants, baselines, promotion gates, and rollback notes. 
 data-throughput-accelerator : pushes large scans and corpus work into indexed, checkpointed, manifest-driven pipelines. 
 latency-critical-systems : profiles p50, p95, queue time, cache hit rate, cold starts, and freshness before changing runtime paths. 
 recursive-decision-ledger : converts repetitive rollout prompting into reusable decision ledgers with prior winners and explicit promotion criteria. 
 
 Why this matters 
 ECC is no longer just a Claude Code config pack. The release candidate packages the reusable layer underneath agent work: skills, hooks, rules, MCP conventions, command surfaces, test gates, and operator discipline that can move across harnesses. 
 The goal is simple: stop rewriting the same prompts, stop relying on fragile local habits, and turn working agent behavior into portable infrastructure. 
 Download 
 
 Release tarball: https://github.com/affaan-m/ECC/releases/download/v2.0.0-rc.1/ecc-universal-2.0.0-rc.1.tgz 
 Full changelog: v1.10.0...v2.0.0-rc.1 
 
 Additional registry and directory surfaces will follow the remaining publication gates. For this RC, the GitHub prerelease and tarball are the public packaged artifact. 
 Verification 
 This release candidate passed the local validation gate used for the final packaging work: 
 
 npm test : 2568 passing 
 npm run lint : passing 
 node scripts/ci/validate-skills.js : 243 skills 
 node scripts/ci/validate-install-manifests.js : 31 modules, 75 components, 6 profiles 
 node scripts/ci/validate-no-personal-paths.js : passing 
 npm run preview-pack:smoke -- --format json : passing 
 npm pack --dry-run : includes the new optimization and Itô skill packs 
 
 RC boundary 
 This is a release candidate, not the final GA claim. Secrets, private operator state, OAuth tokens, personal datasets, and unsanitized local automations are not part of the public package.

</details>