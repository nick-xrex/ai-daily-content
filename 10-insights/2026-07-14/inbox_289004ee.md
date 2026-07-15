---
id: inbox_289004ee
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-ruflo-releases-v3-30-1-fix-2679-statusline-generator-dr-5d93]]"
title: "v3.30.1 — fix #2679 statusline generator drift"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.30.1
source: ruflo-releases
published_at: 2026-07-14T20:14:05+00:00
fetched_at: 2026-07-14T22:10:02.238833+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.30.1 修復 #2679 statusline 產生器漂移問題。`generateStatuslineScript()` 不再內聯 1000 行範本字串，改為將 `.claude/helpers/statusline.cjs` 作為唯一信源，僅替換 `maxAgents` 和 `bakedVersion` 兩個已知值。此改變使所有未來對 helper 的編輯自動傳播到 `ruflo init` 輸出，無需手動同步。新安裝將獲得 v3.29.0 era 的 helper 版本，含完整 OSC 8 點擊、domain 後綴、截斷省略號、亮白加粗命令樣式、300s 快取 TTL、每個子進程 `windowsHide`。三個 CI 靜態迴歸守衛已更新以捕捉信源同步漂移。"
key_points:
  - "generateStatuslineScript() 改為讀取 .claude/helpers/statusline.cjs 作為單一信源，而非內聯 1000 行模板"
  - "未來 helper 編輯自動傳播至新安裝，無需手動同步"
  - "CI 工作流（statusline-generator smoke 驗證、#2196 delegation invariant、#2679 sync invariant）皆改為 grep helper 驗證信源一致"
tags: [bug-fix, ruflo, statusline, single-source-of-truth, cli]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.30.1 — fix #2679 statusline generator drift

Ruflo v3.30.1 修復 #2679 statusline 產生器漂移問題。`generateStatuslineScript()` 不再內聯 1000 行範本字串，改為將 `.claude/helpers/statusline.cjs` 作為唯一信源，僅替換 `maxAgents` 和 `bakedVersion` 兩個已知值。此改變使所有未來對 helper 的編輯自動傳播到 `ruflo init` 輸出，無需手動同步。新安裝將獲得 v3.29.0 era 的 helper 版本，含完整 OSC 8 點擊、domain 後綴、截斷省略號、亮白加粗命令樣式、300s 快取 TTL、每個子進程 `windowsHide`。三個 CI 靜態迴歸守衛已更新以捕捉信源同步漂移。

### 重點
- generateStatuslineScript() 改為讀取 .claude/helpers/statusline.cjs 作為單一信源，而非內聯 1000 行模板
- 未來 helper 編輯自動傳播至新安裝，無需手動同步
- CI 工作流（statusline-generator smoke 驗證、#2196 delegation invariant、#2679 sync invariant）皆改為 grep helper 驗證信源一致

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.30.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What 
 PATCH release closing #2679 — the statusline generator drift discovered during the v3.30.0 release flow. 
 Fix 
 `generateStatuslineScript()` in `v3/@claude-flow/cli/src/init/statusline-generator.ts` no longer inlines a 1000-line template string. It now READS `.claude/helpers/statusline.cjs` as its single source of truth and substitutes two known values (`maxAgents`, `bakedVersion`). Every future edit to the helper propagates to `ruflo init` output automatically — no manual sync required. 
 Impact 
 
 Fresh installs / re-inits : get the current v3.29.0-era helper (whole-row-clickable OSC 8, `(domain)` suffix, ellipsis on truncation, bright-white bold command styling, 300s cache TTL, `windowsHide` on every subprocess spawn) instead of the pre- #2195 non-delegation shape that the generator had frozen at. 
 Existing installs : unchanged. The deployed helper is already correct; this fix only affects new `ruflo init` writes. 
 
 CI 
 Three static-regression guards updated for the read-and-substitute pattern: 
 
 `.github/workflows/v3-ci.yml` — statusline generator delegation smoke 
 `scripts/audit-fix-invariants.mjs` — #2196 delegation invariant + NEW #2679 sync invariant 
 `scripts/smoke-statusline-generator-delegation.mjs` — Layer 1 static contract 
 
 Each now greps the HELPER for the delegation content (where it now lives) with a paired assertion that the generator still reads it. Drift on either side of the sync is caught. 
 Related 
 
 PR #2680 — the fix 
 Issue #2679 — closed 
 v3.30.0 release (`74bc81f8e` / `fea1d9e95`) — where this drift was first surfaced 
 
 Install 
 ```bash 
npx ruflo@latest init 
 or 
 npm install -g @claude-flow/cli@3.30.1 
```

</details>