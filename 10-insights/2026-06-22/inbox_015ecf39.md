---
id: inbox_015ecf39
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2203-ruflo-releases-v3-13-2-agentdb-3-0-0-alpha-17-memfs-saf-3cab]]"
title: "v3.13.2 — agentdb 3.0.0-alpha.17 MEMFS safety net (upstream-side #2432 fix)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.13.2
source: ruflo-releases
published_at: 2026-06-22T16:08:01+00:00
fetched_at: 2026-06-23T00:25:15.640011+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.13.2 採納上游 agentdb@3.0.0-alpha.17 修復，在 SqlJsRvfBackend 內部新增 FinalizationRegistry 安全網。sql.js 模組是程序單例；包裝器持有 Emscripten MEMFS 檔案（~11 MB）僅於顯式 .close() 時釋放，JS GC 無法回收。上游修復 + v3.13.1 下游修復形成雙層防禦：下游層（ControllerRegistry close-on-replace）和上游層（防禦性 FinalizationRegistry）。聯合效應：即使消費者忘記顯式關閉，洩漏類別也被堵死。所有套件一同釋出。"
key_points:
  - "單例資源洩漏需雙層防禦：(1) 下游變異site強制關閉舊實例，(2) 上游防禦性 Finalization Registry 捕捉遺漏的呼叫端"
  - "FinalizationRegistry 作為忘記清理的安全網：當明確 close() 不可靠時採用"
  - "上游修復：ruvnet/agentdb#10，與下游 PR #2444 組合"
tags: [memory-leak, finalization-registry, defensive-programming, resource-cleanup, singleton-pattern]
topics: []
importance: 3
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.13.2 — agentdb 3.0.0-alpha.17 MEMFS safety net (upstream-side #2432 fix)

ruflo v3.13.2 採納上游 agentdb@3.0.0-alpha.17 修復，在 SqlJsRvfBackend 內部新增 FinalizationRegistry 安全網。sql.js 模組是程序單例；包裝器持有 Emscripten MEMFS 檔案（~11 MB）僅於顯式 .close() 時釋放，JS GC 無法回收。上游修復 + v3.13.1 下游修復形成雙層防禦：下游層（ControllerRegistry close-on-replace）和上游層（防禦性 FinalizationRegistry）。聯合效應：即使消費者忘記顯式關閉，洩漏類別也被堵死。所有套件一同釋出。

### 重點
- 單例資源洩漏需雙層防禦：(1) 下游變異site強制關閉舊實例，(2) 上游防禦性 Finalization Registry 捕捉遺漏的呼叫端
- FinalizationRegistry 作為忘記清理的安全網：當明確 close() 不可靠時採用
- 上游修復：ruvnet/agentdb#10，與下游 PR #2444 組合

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.13.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

🔧 Picks up upstream agentdb fix 
 `agentdb@3.0.0-alpha.17` adds a `FinalizationRegistry` safety net inside `SqlJsRvfBackend` ( ruvnet/agentdb#10 ). This is the upstream-side fix for the MEMFS leak class that ruflo v3.13.1 already addressed downstream. 
 Combined effect on #2432 : the leak class is now closed at BOTH layers — downstream (close-on-replace in ControllerRegistry) and upstream (defensive FinalizationRegistry that catches consumers who forget). Belt + suspenders. 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `agentdb` 
 3.0.0-alpha.17 
 — 
 — 
 
 
 `@claude-flow/cli` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 `claude-flow` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 `ruflo` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 
 Upgrade 
 ```bash 
npx ruflo@latest # picks up 3.13.2 + agentdb 3.0.0-alpha.17 
``` 
 Cross-references 
 
 🔗 Upstream PR: ruvnet/agentdb#10 
 🔗 Upstream issue: ruvnet/agentdb#9 
 🔗 Downstream issue: #2432 (closed in v3.13.1) 
 🔗 Companion: v3.13.1 downstream-side fix (PR #2444 ) 
 
 
 🤖 Generated with RuFlo

</details>