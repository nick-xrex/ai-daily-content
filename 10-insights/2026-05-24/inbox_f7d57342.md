---
id: inbox_f7d57342
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-ruflo-releases-v3-7-0-first-stable-2120-memory-stats-le-ba68]]"
title: "v3.7.0 — first stable + #2120 memory-stats legacy-DB fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0
source: ruflo-releases
published_at: 2026-05-24T15:17:02+00:00
fetched_at: 2026-05-25T00:15:58.870747+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.7.0 正式發布首個穩定版本，結束 alpha 系列（alpha.1 → alpha.81），宣佈版本控制政策轉向 semver-stable (3.7.0 → 3.7.1 patch、3.8.0 minor、4.0.0 breaking)。關鍵修復解決 legacy 資料庫記憶統計問題：支持 status IS NULL 狀態、背景 UPDATE 活躍標記、強化 isInitialized() 檢查邏輯。新增 6 項迴歸防護機制：memory-stats-legacy-db、agent-execute-providers、github-safe-injection、deprecated-actions、attribution-opt-in、init-bundle-invariants。"
key_points:
  - "首個穩定版本發布；終止 alpha 發行，npm latest tag 預設為穩定版；legacy alpha/v3alpha dist-tags 維持向後相容"
  - "Legacy 資料庫 NULL status 修復：status IS NULL 支持、背景 UPDATE backfill、isInitialized() 強化邏輯；修復 WSL2 daemon 三項錯誤"
  - "新增 6 項迴歸防護機制：memory-stats-legacy-db (此版)、agent-execute-providers (#2042)、github-safe-injection + deprecated-actions (ADR-127)、attribution-opt-in、init-bundle-invariants (ADR-128)"
tags: [ruflo, stable-release, versioning-policy, database-fix, legacy-support]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0 — first stable + #2120 memory-stats legacy-DB fix

RuFlo v3.7.0 正式發布首個穩定版本，結束 alpha 系列（alpha.1 → alpha.81），宣佈版本控制政策轉向 semver-stable (3.7.0 → 3.7.1 patch、3.8.0 minor、4.0.0 breaking)。關鍵修復解決 legacy 資料庫記憶統計問題：支持 status IS NULL 狀態、背景 UPDATE 活躍標記、強化 isInitialized() 檢查邏輯。新增 6 項迴歸防護機制：memory-stats-legacy-db、agent-execute-providers、github-safe-injection、deprecated-actions、attribution-opt-in、init-bundle-invariants。

### 重點
- 首個穩定版本發布；終止 alpha 發行，npm latest tag 預設為穩定版；legacy alpha/v3alpha dist-tags 維持向後相容
- Legacy 資料庫 NULL status 修復：status IS NULL 支持、背景 UPDATE backfill、isInitialized() 強化邏輯；修復 WSL2 daemon 三項錯誤
- 新增 6 項迴歸防護機制：memory-stats-legacy-db (此版)、agent-execute-providers (#2042)、github-safe-injection + deprecated-actions (ADR-127)、attribution-opt-in、init-bundle-invariants (ADR-128)

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

First stable release — the alpha series (3.7.0-alpha.1 → 3.7.0-alpha.81) is now closed. From here on we ship semver-stable: 3.7.0 → 3.7.1 (patch), 3.8.0 (minor), 4.0.0 (breaking). 
 Highlights 
 #2120 — memory stats / status fixed for legacy DBs 
 Reporter @alexandrelealbess on WSL2: ruflo memory stats reported Total Entries: 0 against a 251-row .swarm/memory.db , and ruflo status falsely reported "not initialized". 
 
 
 
 Fix 
 Where 
 
 
 
 
 Accept status IS NULL alongside 'active' 
 memory-bridge.ts bridgeListEntries 
 
 
 Same in raw sql.js fallback 
 memory-initializer.ts listEntries (4 prepares) 
 
 
 Backfill UPDATE ... SET status='active' WHERE status IS NULL 
 memory-initializer.ts ensureSchemaColumns 
 
 
 isInitialized() now accepts any of .claude-flow/config.{yaml,json} , .swarm/memory.db , .claude/settings.json 
 status.ts 
 
 
 New CI smoke smoke-memory-stats-legacy-db.mjs 
 .github/workflows/v3-ci.yml 
 
 
 
 Versioning policy change 
 
 No more -alpha.N releases. Default npm publish tag is latest . 
 Legacy alpha and v3alpha dist-tags continue to point at the latest stable for backward compat — so npx ruflo@alpha and npx claude-flow@v3alpha still work. 
 
 CI surface (all guards added on alphas, still active) 
 5 new regression smokes from the alpha series: 
 
 smoke-agent-execute-providers.mjs ( #2042 ) 
 smoke-github-safe-injection.mjs + smoke-github-actions-pins.mjs + smoke-deprecated-actions.mjs ( #2089 ADR-127) 
 smoke-attribution-opt-in.mjs ( #2089 ADR-127) 
 smoke-init-bundle-invariants.mjs ( #2095 ADR-128) 
 smoke-ruvllm-wasm-auto-init.mjs ( #2086 ) 
 smoke-memory-stats-legacy-db.mjs ( #2120 , this release) 
 
 Try it 
 npx ruflo@latest init # → 3.7.0 
 # or upgrade in place 
npm i -g ruflo@latest 
 Changelog 
 See git log v3.7.0-alpha.71...v3.7.0 for the full alpha series. Key fixes that culminated in this release: 
 
 #2120 (alpha.81 → 3.7.0) — memory stats legacy DB NULL status 
 #2110 (alpha.80 → alpha.81) — WSL2 daemon triple bug 
 #2112 (alpha.79 → alpha.80) — opentelemetry overrides on ruflo wrapper 
 #2086 (alpha.71 → alpha.72) — ruvllm WASM auto-init 
 #2042 (alpha.77 → alpha.78) — agent_execute provider routing 
 #2078 (alpha.78) — opt-in Co-Authored-By trailer 
 #2089 / ADR-127 — GitHub stack modernization 
 #2095 / ADR-128 — init bundle reduce 
 #2068 / ADR-126 — neural-trader substrate integration 
 #2061 / ADR-125 — memory consolidation, 2.70x retrieval speedup via RaBitQ quantization 
 
 Co-Authored-By: rUv

</details>