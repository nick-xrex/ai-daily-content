---
id: inbox_b1bf2f19
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_b1bf2f19]]"
title: "Ruflo v3.32.35 — Adaptive Swarms and Safer Learning Loops"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.35
source: ruflo-releases
published_at: 2026-07-29T18:02:33+00:00
fetched_at: 2026-07-31T01:28:28.445510+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.35 推出 pheromone-adaptive swarm topology，讓長期執行的 agent teams 根據 outcome、latency、consensus signals 自適應學習工作分配。新演算法結合 outcome-based scoring、exponential moving average、role protection（保護特定角色）、minimum quorum（最少活躍 agents）及 bounded exploration。先以 dry-run 校準模式啟動讓團隊檢查決策，再顯式啟用 --apsc-live 來影響排程（不終止 agents、不撤銷存取、不丟棄 context、不擴大權限）。Project flywheel 現要求 project-local hash-pinned benchmark （.claude/eval/flywheel-anchor.manifest.json），無 anchor 的非 Ruflo repo 改為 fail closed。Learned routing 立即在 live MCP process 更新並清除舊向量。Daemon auto-start 限制到含 .claude-flow/ 的真正 Ruflo projects，30 分鐘 idle timeout。合成 benchmark（12 agents 20k updates）：33.3% active-agent reduction、+0.2617 admitted mean score、0.0066ms update p95。驗證：93 changed-surface tests、20 concurrent outcome writers 全成功、smoke tests、CI/CD/CodeQL/CVE/verification workflows all pass。"
key_points:
  - "Pheromone-adaptive topology 用 EMA scoring、role-aware protection、quorum floor、atomic cross-process updates 實現受控 adaptive scheduling，dry-run 校準模式讓團隊先檢查"
  - "Project flywheel 加入 hash-pinned local anchor 機制 (sha256 binding)，prevent silent optimization against wrong benchmark；non-compliant projects fail closed"
  - "Adaptive scheduling 合成 benchmark 結果：33.3% agent reduction、+0.2617 mean score、p95 update latency 0.0066ms，保留 quorum 和 role 不變量"
tags: [pheromone-adaptive, swarm-topology, flywheel-anchor, dry-run-calibration]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Ruflo v3.32.35 — Adaptive Swarms and Safer Learning Loops

Ruflo v3.32.35 推出 pheromone-adaptive swarm topology，讓長期執行的 agent teams 根據 outcome、latency、consensus signals 自適應學習工作分配。新演算法結合 outcome-based scoring、exponential moving average、role protection（保護特定角色）、minimum quorum（最少活躍 agents）及 bounded exploration。先以 dry-run 校準模式啟動讓團隊檢查決策，再顯式啟用 --apsc-live 來影響排程（不終止 agents、不撤銷存取、不丟棄 context、不擴大權限）。Project flywheel 現要求 project-local hash-pinned benchmark （.claude/eval/flywheel-anchor.manifest.json），無 anchor 的非 Ruflo repo 改為 fail closed。Learned routing 立即在 live MCP process 更新並清除舊向量。Daemon auto-start 限制到含 .claude-flow/ 的真正 Ruflo projects，30 分鐘 idle timeout。合成 benchmark（12 agents 20k updates）：33.3% active-agent reduction、+0.2617 admitted mean score、0.0066ms update p95。驗證：93 changed-surface tests、20 concurrent outcome writers 全成功、smoke tests、CI/CD/CodeQL/CVE/verification workflows all pass。

### 重點
- Pheromone-adaptive topology 用 EMA scoring、role-aware protection、quorum floor、atomic cross-process updates 實現受控 adaptive scheduling，dry-run 校準模式讓團隊先檢查
- Project flywheel 加入 hash-pinned local anchor 機制 (sha256 binding)，prevent silent optimization against wrong benchmark；non-compliant projects fail closed
- Adaptive scheduling 合成 benchmark 結果：33.3% agent reduction、+0.2617 mean score、p95 update latency 0.0066ms，保留 quorum 和 role 不變量

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.35)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.35 — Adaptive Swarms and Safer Learning Loops

Ruflo v3.32.35: Adaptive Swarms and Safer Learning Loops 
 Ruflo v3.32.35 gives long-running agent teams a controlled way to learn which 
workers should receive future tasks. The new pheromone-adaptive topology 
combines outcome, latency, and consensus signals while preserving protected 
roles, a minimum active quorum, and existing permissions. It begins in dry-run 
mode so teams can inspect its decisions before enabling scheduling changes. 
 This release also makes the surrounding learning loop more trustworthy: 
project flywheels must evaluate against a project-local, hash-pinned benchmark; 
learned routing updates inside a live MCP process; AgentDB deletes and upserts 
remove stale vectors; and daemon auto-start is limited to actual Ruflo 
projects. 
 Install or upgrade 
 npm install --global ruflo@3.32.35
ruflo doctor 
 Existing installations remain compatible. The default topology is still 
 hierarchical , old swarm state remains readable, historical flywheel receipts 
remain verifiable, and the new adaptive scheduler is opt-in. 
 Try adaptive swarm scheduling 
 Start in the default calibration mode: 
 ruflo swarm init \
 --topology pheromone-adaptive \
 --max-agents 8

ruflo swarm pheromone
ruflo agent metrics --format json 
 When the observations look right, explicitly enable scheduling enforcement: 
 ruflo swarm init \
 --topology pheromone-adaptive \
 --max-agents 8 \
 --apsc-live 
 Live mode changes Ruflo dispatch eligibility only. It does not terminate 
agents, revoke access, discard context, or widen permissions. 
 Use a project-local flywheel anchor 
 Create .claude/eval/flywheel-anchor.manifest.json : 
 {
 "schemaVersion" : " ruflo.flywheel-anchor-manifest/v1 " ,
 "path" : " my-project-anchor.json " ,
 "sha256" : " sha256:&lt;canonical-task-hash&gt; " 
} 
 The referenced anchor contains at least four labelled tasks. Ruflo binds its 
canonical hash into new evaluation receipts. A non-Ruflo repository without a 
project anchor now fails closed instead of silently optimizing against Ruflo's 
built-in development benchmark. 
 What changed 
 
 Adds the opt-in pheromone-adaptive swarm topology with role-aware EMA 
scoring, dry-run calibration, protected roles, quorum floors, bounded 
exploration, atomic cross-process updates, CLI inspection, and MCP tools. 
 Connects hooks post-task outcomes to adaptive scheduling and exposes each 
agent's score, sample count, role, and eligibility through agent metrics . 
 Adds hash-pinned, project-local flywheel evaluation anchors and receipt 
binding while retaining historical receipt verification. 
 Makes learned routing use supported, discriminative evidence and immediately 
invalidates a warm router after labelled outcomes. 
 Makes AgentDB logical-key upserts, deletes, and cleanup reconcile every stale 
vector and report accurate lifecycle metrics. 
 Limits daemon auto-start to projects containing .claude-flow/ , reports the 
first start, and applies a 30-minute abandoned-daemon idle timeout. 
 
 Measured benchmark 
 On the declared synthetic benchmark (12 agents, 20,000 updates), adaptive 
scheduling produced: 
 
 33.3% active-agent reduction; 
 +0.2617 admitted mean score; 
 0.0066 ms update p95 in the release validation run; 
 preserved quorum and protected-role invariants. 
 
 These are Ruflo benchmark results for that workload, not a universal production 
performance claim. 
 Validation 
 
 TypeScript builds passed for @claude-flow/shared , @claude-flow/swarm , and 
 @claude-flow/cli . 
 The changed-surface suite passed 93 tests across nine files. 
 Twenty concurrent outcome writers persisted all twenty rounds with no 
residual lock. 
 Built CLI smoke tests covered initialization, automatic post-task learning, 
status, manual updates, and JSON metrics. 
 CI/CD, V3 CI/CD, CodeQL, cross-agent integration, CVE audit, and verification 
workflows passed on the merged commit. 
 
 This release ships #2848 and 
resolves 
 #2815 , 
 #2819 , 
 #2832 , 
 #2834 , 
 #2839 , and 
 #2840 .

</details>