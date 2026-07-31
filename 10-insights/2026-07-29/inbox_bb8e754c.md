---
id: inbox_bb8e754c
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_bb8e754c]]"
title: "Ruflo v3.32.38 — Daemons Start Only for Ruflo Projects"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.38
source: ruflo-releases
published_at: 2026-07-29T19:56:43+00:00
fetched_at: 2026-07-31T01:28:28.436791+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.38 修復背景程序洩漏問題。先前在任何包含 .claude/ 資料夾的目錄中執行 read-only 命令，會誤觸發 daemon auto-start 並建立 Ruflo daemon。根本原因是 signed-champion startup migration 建立 .claude-flow/ 狀態目錄，daemon auto-start 誤認為這是先前使用者初始化的證據。修復後要求 daemon auto-start 必須驗證 durable Ruflo project marker（Ruflo runtime config、legacy claude-flow.config.json、initialized .swarm/memory.db、Ruflo-specific Claude settings 或 MCP server entry），泛用 .claude/ 或空 .claude-flow/ 不再觸發。修復已驗證：v3.32.37 重現問題產生 daemon，patched build 無；daemon auto-start regression suite 13/13 pass。"
key_points:
  - "Daemon auto-start 需要 durable project marker（.claude-flow/ runtime config、.swarm/memory.db、Ruflo-specific settings 或 MCP entry），避免誤觸發"
  - "根本原因：signed-champion startup 建立的 .claude-flow/ 目錄被誤認為是使用者初始化證據，導致 daemon 在無關 Ruflo projects 累積"
  - "Explicit `ruflo daemon start` 仍在任何地方可用；初始化的 Ruflo projects 保留自動背景 workers"
tags: [daemon-lifecycle, project-marker, background-process, auto-start]
topics: []
importance: 4
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruflo v3.32.38 — Daemons Start Only for Ruflo Projects

Ruflo v3.32.38 修復背景程序洩漏問題。先前在任何包含 .claude/ 資料夾的目錄中執行 read-only 命令，會誤觸發 daemon auto-start 並建立 Ruflo daemon。根本原因是 signed-champion startup migration 建立 .claude-flow/ 狀態目錄，daemon auto-start 誤認為這是先前使用者初始化的證據。修復後要求 daemon auto-start 必須驗證 durable Ruflo project marker（Ruflo runtime config、legacy claude-flow.config.json、initialized .swarm/memory.db、Ruflo-specific Claude settings 或 MCP server entry），泛用 .claude/ 或空 .claude-flow/ 不再觸發。修復已驗證：v3.32.37 重現問題產生 daemon，patched build 無；daemon auto-start regression suite 13/13 pass。

### 重點
- Daemon auto-start 需要 durable project marker（.claude-flow/ runtime config、.swarm/memory.db、Ruflo-specific settings 或 MCP entry），避免誤觸發
- 根本原因：signed-champion startup 建立的 .claude-flow/ 目錄被誤認為是使用者初始化證據，導致 daemon 在無關 Ruflo projects 累積
- Explicit `ruflo daemon start` 仍在任何地方可用；初始化的 Ruflo projects 保留自動背景 workers

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.38)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.38 — Daemons Start Only for Ruflo Projects

Ruflo v3.32.38: Daemons Start Only for Ruflo Projects 
 Ruflo v3.32.38 fixes a background-process leak discovered during the 
post-release audit: a read-only command in a directory containing only a 
Claude Code .claude/ folder could start a detached Ruflo daemon. 
 The trigger was subtle. Signed-champion startup migration created a 
 .claude-flow/ state directory, and daemon auto-start then mistook that 
startup-created directory for prior user initialization. Repeated commands in 
unrelated Claude projects could therefore accumulate one daemon per directory. 
 Install or upgrade 
 npm install --global ruflo@3.32.38
ruflo --version 
 What changed 
 Daemon auto-start now requires a durable Ruflo project marker: 
 
 a Ruflo runtime config under .claude-flow/ ; 
 a legacy claude-flow.config.json ; 
 an initialized .swarm/memory.db ; 
 a Ruflo-specific Claude settings section; or 
 a Ruflo/Claude Flow MCP server entry. 
 
 A generic .claude/ directory, an empty .claude-flow/ directory, or policy 
state created during the current startup no longer authorizes a detached 
process. Explicit ruflo daemon start remains available everywhere, and 
initialized Ruflo projects retain automatic background workers. 
 Validation 
 
 The exact issue reproduction was run against 3.32.37 and produced a daemon. 
 The same reproduction against the patched build produced no process and no 
daemon PID file, even though signed-champion and policy state were applied. 
 Daemon auto-start regression suite: 13/13. 
 CLI TypeScript build passes. 
 The stable release pipeline builds immutable archives, smoke-installs all 
three public packages, publishes those same bytes, and verifies a fresh 
registry installation. 
 
 This release resolves 
 #2852 .

</details>