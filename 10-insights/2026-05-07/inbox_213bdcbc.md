---
id: inbox_213bdcbc
date: 2026-05-07
source_ref: "[[00-inbox/.../inbox_213bdcbc]]"
title: "v12.7.4"
url: https://github.com/thedotmack/claude-mem/releases/tag/v12.7.4
source: claude-mem-releases
published_at: 2026-05-07T02:40:42+00:00
fetched_at: 2026-06-16T00:45:05.933626+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v12.7.4 补丁版本，修复 Codex 对 claude-mem MCP/search 插件的访问问题。通过将 Codex marketplace 指向捆绑的插件根目录恢复访问；新增弹性 MCP launcher fallback 支持本地安装、Codex 缓存、Claude 缓存、远程 marketplace clone 等多个场景。安装期间自动注册 Codex 插件 marketplace、启用 plugin_hooks、清理 legacy AGENTS 模式 Codex context 注入；包含 Codex 会话启动 hook 迁移方案与版本不匹配调查计划。验证涵盖 Codex 0.128.0 本地安装、远程 marketplace 增删与 MCP 初始化测试。"
key_points:
  - "MCP 访问恢复：Codex marketplace 指向本地插件根目录；多层 fallback 覆盖本地/缓存/远程场景"
  - "Codex 生命周期集成：安装时自动注册 marketplace、启用 plugin_hooks、清理遗留 AGENTS 注入模式"
tags: [claude-mem, mcp, plugin-distribution, codex-integration]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v12.7.4

claude-mem v12.7.4 补丁版本，修复 Codex 对 claude-mem MCP/search 插件的访问问题。通过将 Codex marketplace 指向捆绑的插件根目录恢复访问；新增弹性 MCP launcher fallback 支持本地安装、Codex 缓存、Claude 缓存、远程 marketplace clone 等多个场景。安装期间自动注册 Codex 插件 marketplace、启用 plugin_hooks、清理 legacy AGENTS 模式 Codex context 注入；包含 Codex 会话启动 hook 迁移方案与版本不匹配调查计划。验证涵盖 Codex 0.128.0 本地安装、远程 marketplace 增删与 MCP 初始化测试。

### 重點
- MCP 访问恢复：Codex marketplace 指向本地插件根目录；多层 fallback 覆盖本地/缓存/远程场景
- Codex 生命周期集成：安装时自动注册 marketplace、启用 plugin_hooks、清理遗留 AGENTS 注入模式

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v12.7.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v12.7.4

Patch release for the Codex mem-search marketplace fix. 
 Highlights: 
 
 Restores Codex access to the claude-mem MCP/search plugin by pointing the Codex marketplace at the bundled plugin root. 
 Adds resilient MCP launcher fallbacks for local installs, Codex plugin cache installs, Claude plugin cache installs, and remote marketplace clones. 
 Registers Codex plugin marketplaces during install, enables plugin_hooks, and cleans up legacy AGENTS-based Codex context injection. 
 Includes the Codex session-start hook migration and Codex version-mismatch investigation plan. 
 
 Validation: 
 
 npm run build 
 bun test tests/install-non-tty.test.ts tests/infrastructure/plugin-distribution.test.ts tests/servers/mcp-tool-schemas.test.ts tests/setup-runtime.test.ts tests/hook-command.test.ts 
 Docker smoke with codex-cli 0.128.0 for local install, remote marketplace add/upgrade, and MCP initialize.

</details>