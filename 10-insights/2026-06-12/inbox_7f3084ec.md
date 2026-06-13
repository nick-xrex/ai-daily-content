---
id: inbox_7f3084ec
date: 2026-06-12
source_ref: "[[00-inbox/.../inbox_7f3084ec]]"
title: "v3.10.45 — hive-mind --dangerously-skip-permissions deny clause"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.45
source: ruflo-releases
published_at: 2026-06-12T21:04:59+00:00
fetched_at: 2026-06-13T04:10:04.848947+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.45 修復 hive-mind 權限檢查缺陷。根本原因：參數解析器將 kebab-case 轉換為 camelCase，但權限檢查代碼同時期望兩種形式，且 --no-auto-permissions 使用 yargs 風格否定（autoPermissions: false）導致該選項被默默忽視。修復添加第三個 deny clause 檢查 autoPermissions: false，並增加 3 個回歸測試鎖定合約。完成 v3.10.44 未完成的 PR #2301。"
key_points:
  - "參數解析器的 yargs 風格否定陷阱：--no-auto-permissions 產生 autoPermissions: false 而非 noAutoPermissions: true"
  - "修復：添加第三個 deny clause 檢查 autoPermissions: false，確保 --no-auto-permissions 正確否認 --dangerously-skip-permissions"
  - "3 個新回歸測試確保：parser 產生 autoPermissions: false、謂詞否認 {dangerouslySkipPermissions: true, autoPermissions: false}、autoPermissions: true 不觸發否認"
tags: [ruflo, permissions, hive-mind, bug-fix, yargs-parser]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.45 — hive-mind --dangerously-skip-permissions deny clause

Ruflo v3.10.45 修復 hive-mind 權限檢查缺陷。根本原因：參數解析器將 kebab-case 轉換為 camelCase，但權限檢查代碼同時期望兩種形式，且 --no-auto-permissions 使用 yargs 風格否定（autoPermissions: false）導致該選項被默默忽視。修復添加第三個 deny clause 檢查 autoPermissions: false，並增加 3 個回歸測試鎖定合約。完成 v3.10.44 未完成的 PR #2301。

### 重點
- 參數解析器的 yargs 風格否定陷阱：--no-auto-permissions 產生 autoPermissions: false 而非 noAutoPermissions: true
- 修復：添加第三個 deny clause 檢查 autoPermissions: false，確保 --no-auto-permissions 正確否認 --dangerously-skip-permissions
- 3 個新回歸測試確保：parser 產生 autoPermissions: false、謂詞否認 {dangerouslySkipPermissions: true, autoPermissions: false}、autoPermissions: true 不觸發否認

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.45)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.10.45 — hive-mind --dangerously-skip-permissions deny clause

Patch release shipping the completion of the hive-mind permissions fix from v3.10.44's held PR. 
 Fix 
 #2301 — hive-mind --dangerously-skip-permissions now also honors --no-auto-permissions 
 Background: the arg parser converts kebab-case CLI flags to camelCase and stores only the normalized key. The original predicate in hive-mind.ts read only the kebab form for both the activation and deny halves, so: 
 
 --dangerously-skip-permissions silently no-op'd (closed #2269 originally) 
 --no-auto-permissions silently no-op'd (uncovered when validating the v3.10.44 batch) 
 
 The earlier patch (PR #2301 in JOhnsonKC201's branch) correctly fixed the activation half by accepting both kebab + camelCase keys, but the deny half still missed: the parser does NOT produce noAutoPermissions: true for --no-auto-permissions — it uses yargs-style negation and stores autoPermissions: false . 
 Net effect of the partial fix: after activation worked, --dangerously-skip-permissions --no-auto-permissions would have skipped permissions anyway — strictly more permissive than the pre-fix state where activation never even fired. 
 This release adds the third deny clause: 
 const skipPermissions = 
 ( flags [ 'dangerously-skip-permissions' ] === true || flags . dangerouslySkipPermissions === true ) &amp;&amp; 
 ! ( flags [ 'no-auto-permissions' ] || flags . noAutoPermissions || flags . autoPermissions === false ) ; 
 Three new regression tests pin the contract: 
 
 parser produces autoPermissions: false for --no-auto-permissions 
 predicate denies on the parser-produced shape { dangerouslySkipPermissions: true, autoPermissions: false } 
 autoPermissions: true is NOT a deny signal (only === false is) 
 
 Test suite: 9/9 pass. Closes #2269 . 
 Co-authored: @JOhnsonKC201 (original PR), @rvrheenen (reporter who supplied the patch). 
 Install / upgrade 
 npx ruflo@latest init # 3.10.45 
npx @claude-flow/cli@latest # 3.10.45 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.45. 
 Diff 
 main...v3.10.44 — PR #2301 plus the release bump. 
 🤖 Generated with RuFlo

</details>