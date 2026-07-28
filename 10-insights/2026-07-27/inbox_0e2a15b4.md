---
id: inbox_0e2a15b4
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_0e2a15b4]]"
title: "v3.32.18 — SCM query-intent classifier + routing hints (#2760 dream)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.18
source: ruflo-releases
published_at: 2026-07-27T02:56:19+00:00
fetched_at: 2026-07-28T01:16:18.458103+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.18 推出 SCM 查詢意圖分類器，新增 `ruflo memory classify -q` 獨立分類命令與 `ruflo memory search --intent` 路由功能，自動將記憶查詢分類為 episodic / semantic / procedural 三類並映射至 16 個子命名空間（episodic 包含 sessions、session-checkpoints 等；semantic 包含 patterns、reasoning-patterns 等；procedural 包含 skills、agents、playbooks 等）。系統通過 7/7 回歸測試與 E2E 驗證達 100% 準度（「when did we last touch auth」→ episodic、「how does JWT work」→ semantic、「how do I onboard a coder subagent」→ procedural）。v1 採安全優先設計，尚不改變搜尋後端，v2 待後端支援多命名空間 OR 過濾後才應用。"
key_points:
  - "新增 `ruflo memory classify -q` 獨立分類器，返回 intent + confidence + suggested namespaces，支持 --format json 用於管道處理"
  - "`ruflo memory search --intent` 支援五種意圖模式（auto/mixed/episodic/semantic/procedural），E2E 測試 100% 準度，advisory 提示尚未改變後端"
  - "三層命名空間設計：episodic → 6 子命名空間（session/checkpoint/trajectory）、semantic → 6 子命名空間（pattern/adr-pattern）、procedural → 6 子命名空間（skill/agent/workflow）"
tags: [query-intent-classifier, memory-routing, namespace-mapping, search-backend]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.18 — SCM query-intent classifier + routing hints (#2760 dream)

Ruflo v3.32.18 推出 SCM 查詢意圖分類器，新增 `ruflo memory classify -q` 獨立分類命令與 `ruflo memory search --intent` 路由功能，自動將記憶查詢分類為 episodic / semantic / procedural 三類並映射至 16 個子命名空間（episodic 包含 sessions、session-checkpoints 等；semantic 包含 patterns、reasoning-patterns 等；procedural 包含 skills、agents、playbooks 等）。系統通過 7/7 回歸測試與 E2E 驗證達 100% 準度（「when did we last touch auth」→ episodic、「how does JWT work」→ semantic、「how do I onboard a coder subagent」→ procedural）。v1 採安全優先設計，尚不改變搜尋後端，v2 待後端支援多命名空間 OR 過濾後才應用。

### 重點
- 新增 `ruflo memory classify -q` 獨立分類器，返回 intent + confidence + suggested namespaces，支持 --format json 用於管道處理
- `ruflo memory search --intent` 支援五種意圖模式（auto/mixed/episodic/semantic/procedural），E2E 測試 100% 準度，advisory 提示尚未改變後端
- 三層命名空間設計：episodic → 6 子命名空間（session/checkpoint/trajectory）、semantic → 6 子命名空間（pattern/adr-pattern）、procedural → 6 子命名空間（skill/agent/workflow）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.18)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.18 — SCM query-intent classifier + routing hints (#2760 dream)

First half of dream-cycle #2760 : query-intent classifier lands, search wires it as an advisory hint; multi-namespace search-backend routing lands in a follow-up when the backend interface exposes an OR filter. 
 Added 
 ruflo memory classify -q "..." — Standalone classifier. Returns intent + confidence + suggested namespaces. --format json for pipelines. 
 ruflo memory search --intent auto|mixed|episodic|semantic|procedural — When non-mixed, prints an SCM router hint with the suggested namespace. Does NOT mutate the search backend in v1 (safety-first — no baseline regression); v2 will apply when the backend adds a multi-namespace OR filter. 
 Namespace map (matches ruflo's actual write conventions): 
 
 episodic → sessions, session-checkpoints, trajectory, routing-outcomes, commands, feedback 
 semantic → patterns, learned-patterns, adr-patterns, adr-edges, reasoning-patterns, concepts 
 procedural → skills, agents, workflow-templates, playbooks, recipes 
 
 Verification 
 
 Regression tests: 7/7 pass (three canonical intents, mixed fallback, explicit override, auto delegation, mixed explicit) 
 E2E: "when did we last touch auth" → episodic (100%); "how does JWT work" → semantic (100%); "how do I onboard a new coder subagent" → procedural (100%); "auth" → mixed (0) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.18 
 Refs: dream-cycle #2760 (2026-07-22).

</details>