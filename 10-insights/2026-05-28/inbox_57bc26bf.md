---
id: inbox_57bc26bf
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0000-gitnexus-releases-rc-11fc43b4250210fefb70e067e8798c39f4680-1165]]"
title: "rc/11fc43b4250210fefb70e067e8798c39f46803da: feat(impact): per-symbol processes field on byDepth items (#1867)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F11fc43b4250210fefb70e067e8798c39f46803da
source: gitnexus-releases
published_at: 2026-05-28T15:15:37+00:00
fetched_at: 2026-05-29T00:07:13.014424+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 影響分析工具新增 per-symbol processes 欄位，每個 byDepth 項目標記該符號參與的流程清單（日常 cron、webhook、使用者路由等），讓部署規劃者快速識別風險等級差異。舊設計需額外 Cypher 查詢才能得知單一呼叫者涉及哪些流程；新欄位透過二次分組查詢、MAX_CHUNKS 限制與加分頁後富化等機制實現。無涉及流程時為空陣列，降低無關訊息雜訊。scotjelinski 與 Gergő Magyar 聯合審視。"
key_points:
  - "byDepth 項目新增 processes 欄位，列出該符號涉及的流程型別（cron_daily、webhook、user-facing route 各自不同風險等級）"
  - "部署決策可視化：一次查詢即知該呼叫者涉及哪些流程，無需後續 follow-up cypher 查詢"
  - "MAX_CHUNKS 限制防止大頁面爆炸、加分頁後才執行符號級富化，工程上平衡查詢成本與完整性"
tags: [gitnexus, impact-analysis, deploy-planning, code-graph]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/11fc43b4250210fefb70e067e8798c39f46803da: feat(impact): per-symbol processes field on byDepth items (#1867)

GitNexus 影響分析工具新增 per-symbol processes 欄位，每個 byDepth 項目標記該符號參與的流程清單（日常 cron、webhook、使用者路由等），讓部署規劃者快速識別風險等級差異。舊設計需額外 Cypher 查詢才能得知單一呼叫者涉及哪些流程；新欄位透過二次分組查詢、MAX_CHUNKS 限制與加分頁後富化等機制實現。無涉及流程時為空陣列，降低無關訊息雜訊。scotjelinski 與 Gergő Magyar 聯合審視。

### 重點
- byDepth 項目新增 processes 欄位，列出該符號涉及的流程型別（cron_daily、webhook、user-facing route 各自不同風險等級）
- 部署決策可視化：一次查詢即知該呼叫者涉及哪些流程，無需後續 follow-up cypher 查詢
- MAX_CHUNKS 限制防止大頁面爆炸、加分頁後才執行符號級富化，工程上平衡查詢成本與完整性

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F11fc43b4250210fefb70e067e8798c39f46803da)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

feat(impact): per-symbol processes field on byDepth items 
 
 Today impact returns aggregated affected_processes at the top level 
but the per-symbol byDepth items don't say which processes each caller 
participates in. Consumers planning a deploy want to know if a given 
caller is hit by a daily cron, a webhook, or a user-facing route - each 
is a different deploy-risk profile - and that information requires a 
follow-up cypher query per symbol today. 
 This change attaches processes: [...] to every byDepth[depth][i] 
item, listing the processes that symbol participates in: 
 byDepth: { 
"1": [ 
{ 
depth: 1, 
id: "Function:src/foo.ts:doStuff", 
name: "doStuff", 
... 
processes: [ 
{ id: "proc:cron_daily", label: "Daily cron", 
processType: "cron", step: 12 } 
] 
} 
] 
} 
 The list is empty for symbols not in any process. Additive change, no 
breaking modifications to existing fields. 
 Implementation: 
 
 A second chunked Cypher pass runs after the existing per-process 
aggregation pass, returning per-(symbol, process) rows. Same chunk 
size and MAX_CHUNKS as the aggregation pass, so worst-case adds 10 
extra round-trips bounded by the same env var. 
 The enrichment pass is skipped entirely when affectedProcesses.length === 0 (nothing to enrich) or summaryOnly === true (byDepth not 
returned anyway). 
 The aggregation query is unchanged - the new query has a distinct 
RETURN shape ( RETURN s.id AS sid, ... ) so an existing unit test that 
counts STEP_IN_PROCESS chunks was narrowed to match only the 
aggregation pattern. 
 
 Tests: 
 
 New: byDepth items always have a processes field (default empty 
when no STEP_IN_PROCESS edges exist). 
 New: when STEP_IN_PROCESS rows exist, the matching byDepth item 
carries the right {id, label, processType, step} entry. 
 Updated: impact-batching-grouping test mock narrowed to count only 
aggregation chunks (the new per-symbol pass is covered separately). 
 
 
 style: apply prettier to gitnexus/src/mcp/local/local-backend.ts 
 
 Pure line-wrap fix flagged by quality / format CI on PR #1867 . Zero 
semantic change: prettier broke a chained .slice().map() across three 
lines instead of one. No test changes, no logic changes. 
 
 fix(impact): address PR review findings on per-symbol process enrichment 
 
 
 byDepth.processes doc now states each item carries processes (Finding 1) 
 move per-symbol STEP_IN_PROCESS enrichment post-pagination so symbols 
beyond the pre-pagination cap no longer get false-empty processes:[] 
(Finding 2); hoist CHUNK_SIZE/MAX_CHUNKS to function scope so the 
post-pagination pass can reference them 
 dedup per-symbol query with DISTINCT + MIN(r.step) per (symbol,process) 
pair (Finding 3) 
 suppress the per-symbol pass under summaryOnly, incl. impactByUid group 
fan-out, plus a test asserting the query never fires (Findings 4, 6) 
 
 
 fix(impact): address second-round review findings A-E 
 
 Finding A (blocker): impactByUid passed summaryOnly:true, which drops the 
entire byDepth field. cross-impact.ts reads fan.byDepth to build the group 
by_depth output, so cross-repo by_depth was always {}. Replace with a new 
skipPerSymbolEnrichment option on _runImpactBFS that suppresses only the 
per-symbol STEP_IN_PROCESS pass while preserving byDepth. 
 Finding B+D (blocker): rewrite the byDepth.processes tool description. Drop 
the stale "enrichment cap" wording (no longer true post-pagination), document 
the {id,label,processType,step} entry shape, and tell agents to cross-check 
affected_processes when partial:true. 
 Finding C: bound the post-pagination per-symbol enrichment loop to 
MAX_CHUNKS*CHUNK_SIZE page IDs and surface partial:true when capped, so a 
large page cannot trigger unbounded DB round-trips (DoD 2.6). 
 Finding E: add a test exercising the real impactByUid -&gt; _runImpactBFS path 
asserting byDepth survives and the per-symbol query never fires. 
 
 Co-authored-by: scotjelinski 58397194+scotjelinski@users.noreply.github.com 
Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>