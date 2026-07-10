---
id: inbox_b63fbf52
date: 2026-07-09
source_ref: "[[00-inbox/.../inbox_b63fbf52]]"
title: "v3.25.6 — main-red unblock + Cursor hook + #2612 heal"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.25.6
source: ruflo-releases
published_at: 2026-07-09T14:19:46+00:00
fetched_at: 2026-07-10T00:44:43.353049+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.25.6 修復了 Cursor 第三方 hook import 導致 Bash/Edit 工具呼叫失敗的問題（#2613），hooks.json PreToolUse 命令現發出有效的 {\"permission\":\"allow\"} 判決供 Claude Code 和 Cursor 接納。修正 @claude-flow/plugin-agent-federation 的 TypeScript 類型同步（#2608），將可選依賴（@ruvector/learning-wasm、@ruvector/attention、@metaharness/router）通過字符串變量間接導入以避免 tsc 靜態解析。通過 ruflo doctor 實現 MCP 重複註冊自動檢測及修復（#2612），保留 claude-flow 作為規範 MCP key 以保護 ~166 個插件工具引用。消解 ADR-150 規則衝突（#2561），移除 RUFLO_MAX=0 guard 的互斥限制。所有 726 個 CLI 測試通過，114 個 CI 檢查全綠。"
key_points:
  - "Cursor/Claude Code 兼容性：ruflo-hook.sh 靜音 CLI stdout，PreToolUse hooks.json 發出規範的 permission 判決"
  - "可選依賴導入安全化：@ruvector/* 系列通過字符串變量間接導入，install-safety builds 在缺少可選依賴時編譯成功"
  - "MCP 重複註冊檢測修復：ruflo doctor 新增 \"Duplicate Ruflo MCP registrations found\" 警告，自動指引移除正確條目，保留 claude-flow 規範 key"
tags: [ruflo, mcp, cursor-compatibility, build-safety, optional-deps]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.25.6 — main-red unblock + Cursor hook + #2612 heal

Ruflo v3.25.6 修復了 Cursor 第三方 hook import 導致 Bash/Edit 工具呼叫失敗的問題（#2613），hooks.json PreToolUse 命令現發出有效的 {"permission":"allow"} 判決供 Claude Code 和 Cursor 接納。修正 @claude-flow/plugin-agent-federation 的 TypeScript 類型同步（#2608），將可選依賴（@ruvector/learning-wasm、@ruvector/attention、@metaharness/router）通過字符串變量間接導入以避免 tsc 靜態解析。通過 ruflo doctor 實現 MCP 重複註冊自動檢測及修復（#2612），保留 claude-flow 作為規範 MCP key 以保護 ~166 個插件工具引用。消解 ADR-150 規則衝突（#2561），移除 RUFLO_MAX=0 guard 的互斥限制。所有 726 個 CLI 測試通過，114 個 CI 檢查全綠。

### 重點
- Cursor/Claude Code 兼容性：ruflo-hook.sh 靜音 CLI stdout，PreToolUse hooks.json 發出規範的 permission 判決
- 可選依賴導入安全化：@ruvector/* 系列通過字符串變量間接導入，install-safety builds 在缺少可選依賴時編譯成功
- MCP 重複註冊檢測修復：ruflo doctor 新增 "Duplicate Ruflo MCP registrations found" 警告，自動指引移除正確條目，保留 claude-flow 規範 key

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.25.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.25.6 — main-red unblock + Cursor hook + #2612 heal

Highlights 
 Ships to @claude-flow/cli@3.25.6 , claude-flow@3.25.6 , ruflo@3.25.6 (all three of latest / alpha / v3alpha dist-tags pointed at 3.25.6). 
 Fixes 
 
 #2613 — Cursor's third-party hook import no longer fail-closes every Bash/Edit tool call. ruflo-hook.sh (and its .cjs sibling) now silence CLI stdout, and hooks.json PreToolUse commands emit a valid {"permission":"allow"} verdict that both Claude Code and Cursor accept. 
 #2608 — @claude-flow/plugin-agent-federation shim types synced to agentic-flow@2.0.12-fix.8 ; guard optional close() . Fixes Build V3 red on all 3 platforms. 
 #2608 (extension) — @claude-flow/cli optional-dep imports ( @ruvector/learning-wasm , @ruvector/attention , @metaharness/router ) indirected through string variables so tsc no longer resolves them statically. install-safety builds now compile clean when the optional deps are absent. 
 #2590 — resolved as a consequence of the plugin-agent-federation fix. 
 ADR-150 / #2561 reconciliation — ruflo-metaharness smoke #16 rewritten to enforce the correct ADR-150 rule #2 invariant (no metaharness in ruflo hard dependencies) rather than demanding metaharness presence. Removes the mutual-exclusion with the RUFLO_MAX=0 optional-deps budget guard. 
 #2612 — Duplicate MCP registrations ( claude-flow + ruflo for the same binary) are healed via ruflo doctor detection. The canonical MCP key stays claude-flow to preserve the ~166 plugin tool references to mcp__claude-flow__* ( #2206 ). Doctor now surfaces "Duplicate Ruflo MCP registrations found" with an actionable fix-message pointing operators at the correct entry to remove. 
 
 Release integrity 
 
 Helpers manifest re-signed with Ed25519 for 3.25.6 ; verify-helpers OK. 
 All 726 CLI tests pass locally. 
 CI green on the merged PR (0 failures across 114 checks). 
 
 🤖 Generated with RuFlo

</details>