---
id: inbox_903cb64b
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-ruflo-releases-v3-7-0-alpha-23-task-status-crash-fix-6bae]]"
title: "v3.7.0-alpha.23 — task-status crash fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.23
source: ruflo-releases
published_at: 2026-05-11T13:14:03+00:00
fetched_at: 2026-05-22T18:11:11.708465+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.7.0-alpha.23 patch release 修復 2 個 bug。#1863：task status <id> 在 task 無 dependencies/dependents/tags 時 crash（TypeError Cannot read properties of undefined reading 'join'），因命令格式器假設這些欄位總是陣列但 MCP server 可能省略；修正用 ?.join() || 'None'，並添加 cli-no-crash smoke test（task create → task status/list、agent list、memory list、swarm status）防止此類 unhandled exception 再發生。#1899：ruflo-core hooks 引用錯誤的包（npx claude-flow@alpha vs npx ruflo@alpha），導致短暫網路中斷時 ETIMEDOUT；修正但須等 ruflo-core@0.2.2 重新發布至 marketplace IPFS 分佈。"
key_points:
  - "Task status 命令在缺少 dependencies/dependents/tags 時 crash，改用安全導航 ?.join() 或預設 'None'"
  - "Ruflo-core hooks 錯誤引用 claude-flow@alpha 而非 ruflo@alpha，導致網路中斷時 ETIMEDOUT"
  - "新增 cli-no-crash smoke test 驅動 task create → task status/list、agent list、memory list、swarm status，防止 unhandled exception"
tags: [crash-fix, task-management, hooks-configuration]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.23 — task-status crash fix

RuFlo v3.7.0-alpha.23 patch release 修復 2 個 bug。#1863：task status <id> 在 task 無 dependencies/dependents/tags 時 crash（TypeError Cannot read properties of undefined reading 'join'），因命令格式器假設這些欄位總是陣列但 MCP server 可能省略；修正用 ?.join() || 'None'，並添加 cli-no-crash smoke test（task create → task status/list、agent list、memory list、swarm status）防止此類 unhandled exception 再發生。#1899：ruflo-core hooks 引用錯誤的包（npx claude-flow@alpha vs npx ruflo@alpha），導致短暫網路中斷時 ETIMEDOUT；修正但須等 ruflo-core@0.2.2 重新發布至 marketplace IPFS 分佈。

### 重點
- Task status 命令在缺少 dependencies/dependents/tags 時 crash，改用安全導航 ?.join() 或預設 'None'
- Ruflo-core hooks 錯誤引用 claude-flow@alpha 而非 ruflo@alpha，導致網路中斷時 ETIMEDOUT
- 新增 cli-no-crash smoke test 驅動 task create → task status/list、agent list、memory list、swarm status，防止 unhandled exception

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.23)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release — bug fixes 
 #1863 — task status no longer crashes 
 task status &lt;id&gt; threw TypeError: Cannot read properties of undefined (reading 'join') when a task had no dependencies/dependents/tags (created via task create , or loaded from an older store schema). The command formatter assumed those fields were always arrays; the MCP server legitimately omits them. Now guarded with ?.join() || 'None' at all five sites. 
 Also added a cli-no-crash CI smoke ( task create → task status + task list / agent list / memory list / swarm status ) that fails the build on any unhandled-exception crash — so this class doesn't recur. 
 #1899 — ruflo-core hooks call the right package 
 The ruflo-core plugin's hooks.json referenced npx claude-flow@alpha in all 5 hook commands, causing ETIMEDOUT errors on every session-end during brief network blips. Now uses npx ruflo@alpha . Note: the marketplace plugin distributes via IPFS — update ruflo-core ( /plugin update ruflo-core ) once ruflo-core@0.2.2 is republished to get this. The npm-CLI side is fixed in this release. 
 Still open / explained 
 
 #1863 (execution half) — task assign → autonomous daemon pickup → execution is the part not wired end-to-end yet (ADR-095 G1). The crash is fixed; the daemon worker-pool wire is the remaining tracker. The working path today is agent_spawn → agent_execute (the latter calls the Anthropic API). 
 Branding sweep ( #1858 , #1861 ) — display strings still say claude-flow in a few places (MCP server key in .mcp.json , doctor banner, daemon log). Batched for an upcoming alpha. Package names like @claude-flow/aidefence stay — they're the actual published packages. 
 
 Install 
 npx ruflo@latest # → 3.7.0-alpha.23 
npx claude-flow@latest # → 3.7.0-alpha.23

</details>