---
id: inbox_3b1a2246
date: 2026-06-27
source_ref: "[[00-inbox/2026-06-27/2200-ruflo-releases-v3-14-4-darwin-core-systems-sweep-tarbal-f9f1]]"
title: "v3.14.4 — Darwin core-systems sweep + tarball-bloat fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.14.4
source: ruflo-releases
published_at: 2026-06-27T16:32:47+00:00
fetched_at: 2026-06-27T22:05:09.597407+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.14.4 發布，核心為 Darwin core-systems 最佳化與關鍵的打包體積修正。性能改進包括：skill-distillation 效能提升 133%（0.4286→1.0，達到基準天花板），causal-graph 熱路徑延遲從 115ms 大幅下降至 3ms（-97%），reasoning-bank 在 BEIR benchmark 累計達 +10.3% 相對改進。最關鍵的修復是解決發布阻礙：tarball 因掃入 .claude/worktrees 等目錄而膨脹至 276MB，已通過在 package.json 新增排除規則修正至 2.3MB（比 3.14.1 基線更緊湊）。此修正確保發布成功並減輕安裝體積。"
key_points:
  - "skill-distillation 在 SKILL-DISCO bench 達成 7/7 成功率（從 3/7），超越 arXiv 2026 +22% 目標"
  - "causal-graph 熱路徑延遲 -97%（115ms→3ms）：透過 EXISTS-probe 早期退出與 module-level 動態匯入快取最佳化"
  - "tarball 修正：從 276MB / 46k files 縮減至 2.3MB / 1096 files，新增 !.claude/worktrees/**、!.claude/sessions/** 排除規則"
tags: [ruflo, performance-optimization, darwin-loop, build-optimization]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.14.4 — Darwin core-systems sweep + tarball-bloat fix

Ruflo v3.14.4 發布，核心為 Darwin core-systems 最佳化與關鍵的打包體積修正。性能改進包括：skill-distillation 效能提升 133%（0.4286→1.0，達到基準天花板），causal-graph 熱路徑延遲從 115ms 大幅下降至 3ms（-97%），reasoning-bank 在 BEIR benchmark 累計達 +10.3% 相對改進。最關鍵的修復是解決發布阻礙：tarball 因掃入 .claude/worktrees 等目錄而膨脹至 276MB，已通過在 package.json 新增排除規則修正至 2.3MB（比 3.14.1 基線更緊湊）。此修正確保發布成功並減輕安裝體積。

### 重點
- skill-distillation 在 SKILL-DISCO bench 達成 7/7 成功率（從 3/7），超越 arXiv 2026 +22% 目標
- causal-graph 熱路徑延遲 -97%（115ms→3ms）：透過 EXISTS-probe 早期退出與 module-level 動態匯入快取最佳化
- tarball 修正：從 276MB / 46k files 縮減至 2.3MB / 1096 files，新增 !.claude/worktrees/**、!.claude/sessions/** 排除規則

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.14.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release shipping the darwin-core systems Darwin loop (PR #2481 ) and a critical tarball-bloat fix. 
 Darwin core-systems wins (PR #2481 ) 
 
 
 
 Dim 
 Δ 
 Detail 
 
 
 
 
 skill-distillation 
 0.4286 → 1.0 (+133% rel) 
 ADR-155 SKILL-DISCO bench: AND→OR predicate then promote-all. 3/7 → 7/7 successful traces promoted. Exceeds the SKILL-DISCO arXiv 2026 +22% target on this synthetic bench. 
 
 
 causal-graph hot path 
 115ms → 3ms (-97%) 
 Two optimizations in v3/@claude-flow/cli/src/mcp-tools/agentdb-tools.ts: (a) EXISTS-probe early-exit on missing seed; (b) module-level dynamic-import cache for graph-query/pathfinder handlers. All 21 smoke tests still pass. 
 
 
 reasoning-bank 
 +0.0024 
 scifact bm25 0.0→0.05 tie-breaker. Cumulative across this + prior BEIR Darwin loop: 0.5694 → 0.628 = +10.3% rel. 
 
 
 benchmark infra 
 new --only flag 
 `node scripts/benchmark-intelligence.mjs --only=` enables per-dimension measurement (saves multi-minute wall when only one dim needs scoring). 
 
 
 2 baselines confirmed at-target 
 — 
 sona-adapt 0.0041 &lt; 0.005 (WASM-opaque); moe-gate afterConfidence 0.88 &gt; 0.85 (WASM-opaque). 
 
 
 
 Tarball-bloat fix (critical) 
 The 3.14.4 publish initially failed with 413 Payload Too Large — the tarball had bloated from 77MB to 276MB / 46k files because the root `files` field swept in `.claude/worktrees/**` (3.3GB of Darwin workflow worktrees from this session). 
 Added explicit excludes in `package.json` files-pattern: 
 
 `!.claude/worktrees/**` 
 `!.claude/projects/**` 
 `!.claude/sessions/**` 
 `!.claude/scheduled_tasks.lock` 
 
 Result: 2.3 MB / 1096 files — slimmer than the 3.14.1 baseline (77MB / 14440 files). Published tarball now contains only what's actually needed (bin/, dist/, .claude-plugin/, .claude/agents/, .claude/commands/, etc.). 
 Install 
 ```bash 
npx ruflo@3.14.4 
 or 
 npx @claude-flow/cli@3.14.4 
``` 
 All three packages — @claude-flow/cli, claude-flow, ruflo — at 3.14.4 with consistent latest / alpha / v3alpha dist-tags. 
 Honest dimensions 
 
 skill-distillation hit the synthetic bench ceiling (1.0/1.0) — real ALFWorld/WebArena eval would be the next validation 
 HNSW recall@10 = 0.89 at N=5k vs documented 0.99 — flagged for separate investigation (NAPI doesn't honor efConstruction beyond cap) 
 reasoning-bank's BEIR bench doesn't exercise the actual ReasoningBank subsystem — proper bench needed for next leap

</details>