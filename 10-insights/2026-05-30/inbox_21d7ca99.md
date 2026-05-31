---
id: inbox_21d7ca99
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/1800-ruflo-releases-v3-10-17-pretrain-self-learning-from-rep-be33]]"
title: "v3.10.17 — pretrain self-learning from repo history (ADR-077)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.17
source: ruflo-releases
published_at: 2026-05-30T16:59:00+00:00
fetched_at: 2026-05-30T18:05:10.274415+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.17 新增從 repository 歷史自動進行預訓練的功能，透過一行指令掃描 50 次提交和 30 個 issue，自動生成 80 個學習軌跡和 85 個訓練模式。平均預訓練延遲僅 3.36 毫秒/項，檢索匹配率達 100% (10 個樣本查詢全部命中)。此功能解決了新 Ruflo 安裝時的「0 模式、0 軌跡」冷啟動問題。預訓練流程使用與實時學習相同的代碼路徑 (distillAndSerialise → recordTrajectory → neural store)，確保一致性。對已有代碼歷史的專案，此功能消除從零開始累積學習信號的需求，大幅加速系統初始化。"
key_points:
  - "單行指令 `node pretrain-from-github.mjs` 從 50 commits + 30 issues 生成 80 軌跡、85 模式"
  - "預訓練延遲 3.36 ms/項，檢索匹配率 100%，查詢延遲 7.67 ms"
  - "復用實時學習管線 (distillAndSerialise + recordTrajectory)，確保預訓練與後續學習的一致性"
tags: [ruflo, self-learning, repo-history, bootstrapping, cold-start]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.17 — pretrain self-learning from repo history (ADR-077)

Ruflo v3.10.17 新增從 repository 歷史自動進行預訓練的功能，透過一行指令掃描 50 次提交和 30 個 issue，自動生成 80 個學習軌跡和 85 個訓練模式。平均預訓練延遲僅 3.36 毫秒/項，檢索匹配率達 100% (10 個樣本查詢全部命中)。此功能解決了新 Ruflo 安裝時的「0 模式、0 軌跡」冷啟動問題。預訓練流程使用與實時學習相同的代碼路徑 (distillAndSerialise → recordTrajectory → neural store)，確保一致性。對已有代碼歷史的專案，此功能消除從零開始累積學習信號的需求，大幅加速系統初始化。

### 重點
- 單行指令 `node pretrain-from-github.mjs` 從 50 commits + 30 issues 生成 80 軌跡、85 模式
- 預訓練延遲 3.36 ms/項，檢索匹配率 100%，查詢延遲 7.67 ms
- 復用實時學習管線 (distillAndSerialise + recordTrajectory)，確保預訓練與後續學習的一致性

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 Pretrain self-learning from a repo's GitHub history (ADR-077). One script, 
zero config, ~3 ms per trajectory. Turns the day-one "0 patterns, 0 
trajectories" problem into a one-liner. 
 node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs
 # → 80 trajectories trained from 50 commits + 30 issues 
 # → +95 trajectoriesRecorded, +85 patternsLearned, +80 neuralPatternCount 
 # → 100% retrieval match rate across 10 sample queries 
 Why 
 ADR-074–076 (3.10.14–3.10.16) fixed honesty , coherence , and retrieval 
quality . But a fresh ruflo install still started empty — every "did learning 
happen?" call legitimately returned 0 until many real sessions had run. This 
release closes that gap by seeding from a signal source every repo already has: 
its own commits and issues. 
 Each item flows through the same code paths real-time learning uses (no 
shortcuts) — distillAndSerialise (ADR-076) → recordTrajectory (ADR-074) → 
neural store seed. That also closes the ADR-075 consistency note 
"globalStats moved but neural_patterns stayed empty" by writing to both 
stores from the same script. 
 Measured proof 
 
 
 
 
 Before 
 After 
 Δ 
 
 
 
 
 trajectoriesRecorded 
 0 
 95 
 +95 
 
 
 patternsLearned 
 0 
 85 
 +85 
 
 
 neuralPatternCount 
 15 
 95 
 +80 
 
 
 Trained / harvested 
 — 
 — 
 80/80 
 
 
 Avg pretrain latency 
 — 
 — 
 3.36 ms/item 
 
 
 Retrieval match rate (N=95) 
 — 
 — 
 100% (10/10) 
 
 
 Avg query latency 
 — 
 — 
 7.67 ms 
 
 
 
 Run JSONs: 
 
 docs/benchmarks/runs/pretrain-from-github-latest.json 
 docs/benchmarks/runs/pretrained-retrieval-latest.json 
 
 What's in the box 
 
 scripts/pretrain-from-github.mjs — env-configurable harvester 
( COMMITS , ISSUES , SOURCE , BENCH_JSON ) 
 scripts/benchmark-pretrained-retrieval.mjs — after-pretrain validator 
 __tests__/pretrain-from-github.test.ts — CI guard with embedded fixture 
(no live git/gh in tests; auto-picked-up by v3-ci.yml) 
 v3/docs/adr/ADR-077-pretrain-from-history.md 
 v3/docs/learning/self-learning-usage.md — copy-paste guide covering all 
three learning paths plus pretrain 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc -b )
node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs
node v3/@claude-flow/cli/scripts/benchmark-pretrained-retrieval.mjs
( cd v3/@claude-flow/cli &amp;&amp; npx vitest run __tests__/pretrain-from-github.test.ts ) 
 Honest limits 
 
 Standalone-process drift: when the script runs outside the live MCP daemon, 
 sonaCoordinator and memory-bridge start empty. The script's consistency 
block flags this explicitly. From inside the daemon both stores are warm. 
 100% match-rate ≠ semantic relevance. Pretrain proves the wiring; ADR-076's 
MRR benchmark is the right gauge for relevance quality. 
 Commits are all recorded as success (no outcome signal). A "was this commit 
reverted?" verdict refinement is tracked for follow-up. 
 
 Install 
 npx ruflo@3.10.17 # or @latest 
npx ruflo@alpha # legacy compat 
npx ruflo@v3alpha # legacy compat 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) are at 
3.10.17 on latest , alpha , and v3alpha .

</details>