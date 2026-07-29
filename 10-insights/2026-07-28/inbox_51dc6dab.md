---
id: inbox_51dc6dab
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_51dc6dab]]"
title: "v3.32.24 — Codex plugin install (#2801) + metaharness hard dependency (ADR-321)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.24
source: ruflo-releases
published_at: 2026-07-28T03:59:45+00:00
fetched_at: 2026-07-29T03:36:50.938081+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.24 修復 Codex 外掛安裝流程並將 metaharness 升級為硬依賴。修復 #2801：ruflo init --codex/--dual 現在幂等執行 codex plugin marketplace add 和 codex plugin add，安裝 ruflo-core@ruflo 外掛（先前只安裝配置、skills 和 MCP 伺服器，缺少 Ruflo lifecycle hooks）。在 Codex CLI 缺失時優雅降級，並提示使用者在新會話中信任 hooks。根據 ADR-321，metaharness@^0.4.1 和 @metaharness/router@^0.3.2 從 optional 移至 dependencies，作為 cache-warm；MCP 工具通過子程序呼叫，零靜態匯入，保留 graceful degradation 回退。"
key_points:
  - "installRufloCorePlugin() 幂等執行 codex plugin add，安裝 ruflo-core@ruflo 官方上游外掛，避免 #2640 雙重觸發類問題"
  - "metaharness 從可選升級為硬依賴（ADR-321）：@claude-flow/cli 中 metaharness@^0.4.1 和 @metaharness/router@^0.3.2 納入 dependencies，為子程序呼叫的 cache-warm"
  - "Codex CLI 缺失時優雅降級並提示手動安裝；所有 Codex 會話須信任 Ruflo hooks（Codex 不自動信任命令 hooks），ACTION REQUIRED 訊息突出提示"
tags: [ruflo, codex-plugin, metaharness, dependency-management]
topics: []
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.24 — Codex plugin install (#2801) + metaharness hard dependency (ADR-321)

Ruflo v3.32.24 修復 Codex 外掛安裝流程並將 metaharness 升級為硬依賴。修復 #2801：ruflo init --codex/--dual 現在幂等執行 codex plugin marketplace add 和 codex plugin add，安裝 ruflo-core@ruflo 外掛（先前只安裝配置、skills 和 MCP 伺服器，缺少 Ruflo lifecycle hooks）。在 Codex CLI 缺失時優雅降級，並提示使用者在新會話中信任 hooks。根據 ADR-321，metaharness@^0.4.1 和 @metaharness/router@^0.3.2 從 optional 移至 dependencies，作為 cache-warm；MCP 工具通過子程序呼叫，零靜態匯入，保留 graceful degradation 回退。

### 重點
- installRufloCorePlugin() 幂等執行 codex plugin add，安裝 ruflo-core@ruflo 官方上游外掛，避免 #2640 雙重觸發類問題
- metaharness 從可選升級為硬依賴（ADR-321）：@claude-flow/cli 中 metaharness@^0.4.1 和 @metaharness/router@^0.3.2 納入 dependencies，為子程序呼叫的 cache-warm
- Codex CLI 缺失時優雅降級並提示手動安裝；所有 Codex 會話須信任 Ruflo hooks（Codex 不自動信任命令 hooks），ACTION REQUIRED 訊息突出提示

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.24)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.24 — Codex plugin install (#2801) + metaharness hard dependency (ADR-321)

Fixed 
 #2801 — ruflo init --codex/--dual now installs the ruflo-core@ruflo plugin. Before, Codex init set up AGENTS.md, skills, config, and the Ruflo MCP server — but no Ruflo lifecycle hooks. New installRufloCorePlugin() idempotently runs codex plugin marketplace add ruvnet/ruflo --ref main + codex plugin add ruflo-core@ruflo at user scope (canonical upstream plugin, avoiding the #2640 double-firing class), degrades gracefully with a manual-install hint if the Codex CLI is absent, and always emits a prominent ACTION REQUIRED message to trust the hooks in a new Codex session (Codex does not auto-trust command hooks). Ships in @claude-flow/codex@3.0.2 . 
 Changed 
 metaharness promoted to a hard dependency (ADR-321). metaharness@^0.4.1 and @metaharness/router@^0.3.2 moved from optional to dependencies on @claude-flow/cli , so they're always present. ADR-321 supersedes ADR-150's optional-only constraint for these two and records the tradeoff honestly: the MCP metaharness tools invoke via subprocess (zero static imports), so this is functionally a cache-warm for them; the one load-bearing consumer of a declared dep is neural-router.ts 's @metaharness/router import behind CLAUDE_FLOW_ROUTER_NEURAL=1 . Graceful-degradation fallbacks were kept (trivial reversibility). 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli / claude-flow / ruflo 
 3.32.24 
 
 
 @claude-flow/codex 
 3.0.2 
 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.24 
 Closes: #2801 . Refs: ADR-321, ADR-150.

</details>