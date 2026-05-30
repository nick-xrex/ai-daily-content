---
id: inbox_3a6f7943
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-ruflo-releases-v3-10-8-routing-learning-correctness-fix-f645]]"
title: "v3.10.8 — routing-learning correctness fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.8
source: ruflo-releases
published_at: 2026-05-29T17:04:29+00:00
fetched_at: 2026-05-30T02:24:09.163582+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.8 修復智能審計清單中的兩個路由學習 bug。Bug B：QLearningRouter.update() 每 50 次更新才清全快取，導致新學習的 Q 更新被舊快取隱藏，反饋在進程內無效，現改為立即清快取（驗證：10 次更新內完成路由翻轉）。Bug C：--explore false 被忽略因為布爾值解析丟棄顯式空格值，現改為解析 true/false 字面量（--explore false、--explore=false、--no-explore 都支援，驗證：確定性開採）。延遲未修：SONA 預設路徑已透過 LocalSonaCoordinator 學習、WASM MicroLoRA 惰性在上游、Per-task bandit 需要 ADR + 遷移。三包鎖步 3.10.8，CI 31/31 綠。"
key_points:
  - "快取清除改為立即（而非每 50 updates），新學習路由在 10 次更新內生效"
  - "布爾旗標解析修復，--explore false 現確實強制開採"
  - "文檔化延遲項：SONA 已學習、WASM 限制、Schema 遷移待 ADR"
tags: [cache-invalidation, flag-parsing, routing-feedback]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.8 — routing-learning correctness fixes

Ruflo v3.10.8 修復智能審計清單中的兩個路由學習 bug。Bug B：QLearningRouter.update() 每 50 次更新才清全快取，導致新學習的 Q 更新被舊快取隱藏，反饋在進程內無效，現改為立即清快取（驗證：10 次更新內完成路由翻轉）。Bug C：--explore false 被忽略因為布爾值解析丟棄顯式空格值，現改為解析 true/false 字面量（--explore false、--explore=false、--no-explore 都支援，驗證：確定性開採）。延遲未修：SONA 預設路徑已透過 LocalSonaCoordinator 學習、WASM MicroLoRA 惰性在上游、Per-task bandit 需要 ADR + 遷移。三包鎖步 3.10.8，CI 31/31 綠。

### 重點
- 快取清除改為立即（而非每 50 updates），新學習路由在 10 次更新內生效
- 布爾旗標解析修復，--explore false 現確實強制開採
- 文檔化延遲項：SONA 已學習、WASM 限制、Schema 遷移待 ADR

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruflo v3.10.8 — routing-learning correctness fixes 
 Two follow-up fixes from the intelligence audit's remaining punch-list ( docs/reviews/intelligence-system-audit-2026-05-29.md ). 
 Bug B — stale route cache hid learning 
 QLearningRouter.update() only invalidated the whole route cache every 50 updates, so a freshly-learned Q-update stayed hidden behind a stale cached decision — feedback appeared to have no effect on routing in-process until 50 updates accumulated. Now the updated state's cache entry is invalidated immediately. Verified: learned route flips coder→researcher within 10 updates. 
 Bug C — --explore false was ignored 
 Boolean flags dropped an explicit space-form value, so a default-true boolean ( explore ) stayed true even with --explore false — exploitation could not be forced. The parser now consumes a true / false literal for boolean flags ( --explore false , -e false ); --explore=false and --no-explore keep working. Verified: deterministic exploitation with explore=false . 
 Deferred (documented in the audit, not patched) 
 
 SONA default-path: re-examined — the default path already learns via LocalSonaCoordinator ; the inert piece is a non-load-bearing supplementary forward. 
 WASM MicroLoRA apply() inert — lives in the @ruvector/ruvllm dependency (needs upstream fix). 
 Per-task bandit priors — changes a persisted schema (needs an ADR + migration). 
 
 All three packages published at 3.10.8 ( latest / alpha / v3alpha in lockstep). CI: 31/31 green. 
 🤖 Generated with RuFlo

</details>