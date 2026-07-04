---
id: inbox_693ec14b
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-ruflo-releases-v3-17-0-metaharness-learn-gepa-harness-p-4597]]"
title: "v3.17.0 — MetaHarness learn + GEPA: harness policies become measured, evolved artifacts"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.17.0
source: ruflo-releases
published_at: 2026-07-03T18:24:16+00:00
fetched_at: 2026-07-04T01:21:38.221966+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.17.0 閉合 harness 策略生命週期：從評分任務集合學習策略 → 審計編譯後行為 → 對基準進化 → 失敗分析。新命令 metaharness learn 包裝 @metaharness@0.3.0 ADR-235 GEPA 學習框架：變異 harness 基因、對 held-out SWE-bench 切片評分、僅推廣經測量驗證的候選；$0 乾執行模式（--run 顯式花費授權）。新命令 metaharness gepa 審計基因組編譯結果（--op genome/render/validate/analyze），基因組 → 系統提示映射，shipped cand-6 基因組首次 holdout 驗證提升（2/12 → 3/12，零迴歸）。版本釘升級：@metaharness/darwin ~0.3.1 → ~0.8.0（GEPA 引擎、多選擇模式）、metaharness ~0.2.6 → ~0.2.8。驗證：171/171 MCP 運行時、120/120 外掛煙霧、redblue 0.1.4 攻擊預覽驗證。"
key_points:
  - "metaharness learn：從任務集合進化 harness 策略基因組，$0 乾執行 + --run 花費授權"
  - "GEPA 基因組感知框架：基因組編譯至系統提示，可驗證、可進化、可審計行為"
  - "@metaharness/darwin 躍升 0.8.0：多選擇模式（pareto/clade/niche-steering/quality-diversity）+ 交叉/認識論/課程策略"
tags: [metaharness-learn, gepa, policy-evolution, genome-based-learning, measured-improvement]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.17.0 — MetaHarness learn + GEPA: harness policies become measured, evolved artifacts

ruflo v3.17.0 閉合 harness 策略生命週期：從評分任務集合學習策略 → 審計編譯後行為 → 對基準進化 → 失敗分析。新命令 metaharness learn 包裝 @metaharness@0.3.0 ADR-235 GEPA 學習框架：變異 harness 基因、對 held-out SWE-bench 切片評分、僅推廣經測量驗證的候選；$0 乾執行模式（--run 顯式花費授權）。新命令 metaharness gepa 審計基因組編譯結果（--op genome/render/validate/analyze），基因組 → 系統提示映射，shipped cand-6 基因組首次 holdout 驗證提升（2/12 → 3/12，零迴歸）。版本釘升級：@metaharness/darwin ~0.3.1 → ~0.8.0（GEPA 引擎、多選擇模式）、metaharness ~0.2.6 → ~0.2.8。驗證：171/171 MCP 運行時、120/120 外掛煙霧、redblue 0.1.4 攻擊預覽驗證。

### 重點
- metaharness learn：從任務集合進化 harness 策略基因組，$0 乾執行 + --run 花費授權
- GEPA 基因組感知框架：基因組編譯至系統提示，可驗證、可進化、可審計行為
- @metaharness/darwin 躍升 0.8.0：多選擇模式（pareto/clade/niche-steering/quality-diversity）+ 交叉/認識論/課程策略

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.17.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

v3.17.0 — MetaHarness learn + GEPA: harness policies become measured, evolved artifacts 
 This release closes the harness-policy lifecycle loop: learn a policy from a scored task corpus → audit what it compiles to → evolve it against fixed benchmarks → analyze why runs fail. Two new MCP tools (13 → 15), two new CLI subcommands (11 → 13), two new skills, and version-pin upgrades across the @metaharness/* family. 
 New: metaharness learn — learned policies instead of hand-tuned prompts 
 Wraps upstream metaharness@0.3.0 's ADR-235 GEPA learning harness. Instead of a human editing a system prompt and eyeballing the result, learn mutates the harness genome, scores candidates against held-out SWE-bench-style slices, and only promotes measured winners. 
 # $0 dry-run — resolves the slice and prices the run, no model calls 
npx ruflo metaharness learn --host claude-code --model haiku --slice slices/lite.json

 # real run — explicit spend opt-in at every layer 
npx ruflo metaharness learn --repo ~ /src/metaharness --host claude-code \
 --model haiku --slice slices/lite.json --run --timeout-ms 1800000 
 
 $0 by default — spending requires --run (CLI) / run: true (MCP tool metaharness_learn ) 
 Needs a metaharness repo checkout ( --repo or $METAHARNESS_REPO ); without one you get a structured {status: "checkout-required"} payload with clone instructions — a precondition report, not an error 
 
 New: metaharness gepa — genome inspection and auditing 
 Surfaces the @metaharness/darwin@0.8.0 GEPA library entry ( @metaharness/darwin/gepa ) — the first plugin surface with no CLI binary behind it. 
 npx ruflo metaharness gepa --op genome # load + validate the shipped cand-6 genome 
npx ruflo metaharness gepa --op render # genome → the system prompt it compiles to 
npx ruflo metaharness gepa --op validate --path my-genome.json --alert-on-invalid # CI gate 
npx ruflo metaharness gepa --op analyze --transcript run.json # failure-class breakdown 
 Why it matters: evolved policies ship as genome JSON, but the behavior lives in the system prompt the genome compiles to. --op render is the "what does this policy actually say?" view you want before adopting one. The shipped cand-6 genome is the first holdout-confirmed promotion (holdout gold 2/12 → 3/12, zero regressions, empty-patch rate 0.583 → 0.333). 
 Deliberately not surfaced: gepaOptimize — it takes an in-process bring-your-own-evaluator callback that can't cross a subprocess boundary. Import @metaharness/darwin/gepa directly, or use metaharness_evolve for sandbox-scored evolution. 
 Version pins refreshed 
 
 
 
 Package 
 Before 
 After 
 
 
 
 
 @metaharness/darwin 
 ~0.3.1 
 ~0.8.0 (GEPA engine, new evolve selection modes: pareto , clade , niche-steering , quality-diversity , behavioral-diversity , plus --crossover / --epistasis / --curriculum / --mutator ruvllm ) 
 
 
 metaharness 
 ~0.2.6 
 ~0.2.8 (learn arrives via @latest → 0.3.0) 
 
 
 @metaharness/redblue 
 ~0.1.1 
 ~0.1.4 
 
 
 @metaharness/kernel 
 ~0.1.0 
 ~0.1.2 
 
 
 
 Fixes 
 
 redblue stale-cache trap : the install cache dir is now versioned by the pin ( ~/.ruflo/redblue-cache-0.1.4 ), so pin bumps invalidate stale installs — previously a machine that cached 0.1.1 would serve it forever 
 gepa stale-install fallback : a pre-0.8.0 darwin in an ancestor node_modules throws ERR_PACKAGE_PATH_NOT_EXPORTED (no ./gepa subpath); gepa.mjs treats that as recoverable and falls back to its versioned cache 
 
 Validation 
 
 tsc clean build 
 MCP runtime contract: 171/171 assertions across all 15 tools 
 Plugin smoke suite: 120/120 steps 
 darwin 0.8.0 evolve / bench create|verify / security bench proven through the wrappers; redblue 0.1.4 attack preview proven via the new cache path 
 
 All ADR-150 constraints hold: @metaharness/* stays in optionalDependencies , every path degrades gracefully, ruflo remains fully operational with MetaHarness absent. 
 
 Deep-dive : full capabilities walkthrough (usage + rationale) → https://gist.github.com/ruvnet/cdc1bc2259cde127a418f861c3907e1e 
 PR : #2540

</details>