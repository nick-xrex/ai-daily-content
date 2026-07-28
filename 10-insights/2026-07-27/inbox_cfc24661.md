---
id: inbox_cfc24661
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_cfc24661]]"
title: "v3.32.21 — fix(memory/embeddings): --type keyword|hybrid + --threshold 0 (#2790)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.21
source: ruflo-releases
published_at: 2026-07-27T03:27:40+00:00
fetched_at: 2026-07-28T01:14:09.835113+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.32.21 修複記憶搜尋功能的兩個關鍵缺陷。首先，--type keyword|hybrid 旗標被靜默忽視：使用者輸入被系統回傳但實際執行語義搜尋。修復後 --type keyword 執行子字串匹配（key 命中分數 1.0、內容 0.7），--type hybrid 融合語義與關鍵字搜尋並按 (namespace, key) 去重後重排。其次，--threshold 0 被預設值覆蓋（經典 0 || fallback 反模式）——修復涉及 memory.ts、embeddings.ts 3 處與 hooks.ts 4 處共 7 個位置改用 nullish coalescing。同時解決 memory.ts 中聲明預設值 (0.7) 與程式碼回落值 (0.3) 的不一致，統一為 0.7。4/4 E2E 迴歸測試驗證單調性：threshold 更低返回更多或等量結果，不會返回更少。"
key_points:
  - "旗標型選項（--type）必須顯式分支實現，不能靜默預設為某單一模式；被忽視導致所有搜尋都跑語義路徑而非鍵值匹配"
  - "對於數值閾值（--threshold 0），用 nullish coalescing 取代 || 反模式：0 || fallback 會誤判 0 為假值。正確做法：ctx.flags.threshold ?? process.env.DEFAULT_THRESHOLD"
  - "宣告預設值與程式碼回落必須一致：gap (0.7 vs 0.3) 造成不可預測行為；統一後單調性成立（lower threshold ≥ results）"
tags: [nullish-coalescing, config-bugs, search-semantics, numeric-thresholds]
topics: []
importance: 2
novelty: 1
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.21 — fix(memory/embeddings): --type keyword|hybrid + --threshold 0 (#2790)

ruflo v3.32.21 修複記憶搜尋功能的兩個關鍵缺陷。首先，--type keyword|hybrid 旗標被靜默忽視：使用者輸入被系統回傳但實際執行語義搜尋。修復後 --type keyword 執行子字串匹配（key 命中分數 1.0、內容 0.7），--type hybrid 融合語義與關鍵字搜尋並按 (namespace, key) 去重後重排。其次，--threshold 0 被預設值覆蓋（經典 0 || fallback 反模式）——修復涉及 memory.ts、embeddings.ts 3 處與 hooks.ts 4 處共 7 個位置改用 nullish coalescing。同時解決 memory.ts 中聲明預設值 (0.7) 與程式碼回落值 (0.3) 的不一致，統一為 0.7。4/4 E2E 迴歸測試驗證單調性：threshold 更低返回更多或等量結果，不會返回更少。

### 重點
- 旗標型選項（--type）必須顯式分支實現，不能靜默預設為某單一模式；被忽視導致所有搜尋都跑語義路徑而非鍵值匹配
- 對於數值閾值（--threshold 0），用 nullish coalescing 取代 || 反模式：0 || fallback 會誤判 0 為假值。正確做法：ctx.flags.threshold ?? process.env.DEFAULT_THRESHOLD
- 宣告預設值與程式碼回落必須一致：gap (0.7 vs 0.3) 造成不可預測行為；統一後單調性成立（lower threshold ≥ results）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.21)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.21 — fix(memory/embeddings): --type keyword|hybrid + --threshold 0 (#2790)

Two-defect fix filed by markt-heximal in #2790 . 
 Fixed 
 --type keyword|hybrid silently ignored . memory search accepted, echoed, and then discarded the type flag — every search ran semantic. Now: 
 
 --type keyword — listEntries + substring match on key+content, key hit scores 1.0, content hit 0.7 
 --type hybrid — semantic ∪ keyword, dedup by (namespace, key), rerank 
 
 --threshold 0 silently replaced by fallback . Classic 0 || fallback idiom. Fixed with nullish coalescing at 3 reporter-flagged sites (memory.ts, embeddings.ts twice) plus 4 same-class hooks.ts sites (per reporter's "worth grepping more broadly" note). Also reconciled the memory.ts declared-default (0.7) vs code-fallback (0.3) disagreement. 
 Reporter's diagnostic invariant now holds: lower threshold returns ≥ results , not fewer. 
 Regression tests 
 4/4 E2E via real execFileSync against bin/cli.js: 
 
 --type keyword hits substring 
 --type keyword returns 0 for absent substring 
 --type hybrid ≥ semantic set 
 --threshold 0 ≥ --threshold 0.01 (monotonic) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.21 
 Closes: #2790 .

</details>