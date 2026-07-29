---
id: inbox_f8d562d2
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_f8d562d2]]"
title: "v3.32.25 — metaharness pin-drift guard"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.25
source: ruflo-releases
published_at: 2026-07-28T15:10:10+00:00
fetched_at: 2026-07-29T03:36:50.936356+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.25 修復 @metaharness/darwin 版本飄移問題。distill-oracle.ts 中三個呼叫點使用 npx --yes @metaharness/darwin 而未指定版本，可能浮動到 npm latest，導致 darwin breaking release 在評估中途改變行為。新版引入 MH_DARWIN_PIN = '0.8.0' 單一常數，在 optionalDependencies 中聲明 @metaharness/darwin: ^0.8.0 作唯一真源，並添加 scripts/check-metaharness-pins.mjs 和 .github/workflows/metaharness-pin-drift.yml 工作流進行週期與 PR 檢查，偵測漂移時開啟追蹤 issue 並硬止相關 PR。"
key_points:
  - "三個呼叫點統一使用 MH_DARWIN_PIN='0.8.0'，避免浮動升級導致中途 breaking changes（類似 agent-harness-generator#142）"
  - "添加 pin-drift guard 工作流：週期運行 + PR 檢查，網路失敗警告但不誤報，硬止引入漂移的 PR"
  - "向上游 metaharness 專案提交配套 PR #150、#151，同步 darwin pin 範圍和 META_PROXY_VERSION，移植 pin-drift 監視機制"
tags: [ruflo, dependency-management, version-pinning, darwin, ci-cd]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.25 — metaharness pin-drift guard

Ruflo v3.32.25 修復 @metaharness/darwin 版本飄移問題。distill-oracle.ts 中三個呼叫點使用 npx --yes @metaharness/darwin 而未指定版本，可能浮動到 npm latest，導致 darwin breaking release 在評估中途改變行為。新版引入 MH_DARWIN_PIN = '0.8.0' 單一常數，在 optionalDependencies 中聲明 @metaharness/darwin: ^0.8.0 作唯一真源，並添加 scripts/check-metaharness-pins.mjs 和 .github/workflows/metaharness-pin-drift.yml 工作流進行週期與 PR 檢查，偵測漂移時開啟追蹤 issue 並硬止相關 PR。

### 重點
- 三個呼叫點統一使用 MH_DARWIN_PIN='0.8.0'，避免浮動升級導致中途 breaking changes（類似 agent-harness-generator#142）
- 添加 pin-drift guard 工作流：週期運行 + PR 檢查，網路失敗警告但不誤報，硬止引入漂移的 PR
- 向上游 metaharness 專案提交配套 PR #150、#151，同步 darwin pin 範圍和 META_PROXY_VERSION，移植 pin-drift 監視機制

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.25)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.25 — metaharness pin-drift guard

Fixed 
 Floating @metaharness/darwin pin. distill-oracle.ts invoked npx --yes @metaharness/darwin with no version at three call sites (Tier-1 mechanical oracle), floating to npm latest — a breaking darwin release could change eval behavior mid-run. Now pinned via a single MH_DARWIN_PIN = '0.8.0' constant, declared @metaharness/darwin: ^0.8.0 in optionalDependencies as the single source of truth, and a stale ~0.3.1 doc comment corrected. Ruflo's analog of upstream agent-harness-generator#142 . 
 Added 
 metaharness pin-drift guard (the #149 analog ruflo lacked): 
 
 scripts/check-metaharness-pins.mjs — diffs each declared range ( metaharness , @metaharness/router , @metaharness/darwin ) against npm latest + a lock-step check that MH_DARWIN_PIN satisfies the darwin range. Network flakes warn, never false-positive. 
 .github/workflows/metaharness-pin-drift.yml — runs weekly + on PRs touching the pins; opens/updates a tracking issue on drift, hard-fails PRs that introduce it. 
 
 Upstream companion PRs 
 Filed against the metaharness repo: #150 (darwin pin ^0.2.2→^0.8.0, #142 ) and #151 (META_PROXY_VERSION→0.7.0 + ported pin-drift watcher, #149 ). 
 Upgrade 
 npx ruflo@latest --version # → 3.32.25 
 Refs: ADR-150, ADR-321.

</details>