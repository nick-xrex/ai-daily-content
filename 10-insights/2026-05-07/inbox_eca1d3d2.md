---
id: inbox_eca1d3d2
date: 2026-05-07
source_ref: "[[00-inbox/.../inbox_eca1d3d2]]"
title: "v12.7.5"
url: https://github.com/thedotmack/claude-mem/releases/tag/v12.7.5
source: claude-mem-releases
published_at: 2026-05-07T04:31:22+00:00
fetched_at: 2026-06-16T00:45:05.930579+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v12.7.5 补丁版本，修复 npx 安装时 Codex marketplace 注册冲突。若 Codex 已存在旧的 claude-mem-local 注册源，安装程序自动移除该过期注册并改用本地 npx marketplace，同时保留 Codex plugin_hooks 启用和 legacy AGENTS 清理逻辑。发布工作流指示改用 `npm run build-and-sync` 替代 `npm run build`，确保本地 marketplace 与 worker 二进制同步。验证覆盖本地安装与 Codex 0.128.0 smoke test。"
key_points:
  - "Marketplace 冲突解决：检测并移除 Codex 旧注册源，重新添加本地 npx marketplace；保持 plugin_hooks 启用和 AGENTS 清理流程"
  - "发布流程优化：build-and-sync 命令确保 marketplace 与 worker 二进制同步"
tags: [claude-mem, plugin-management, marketplace, installation]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v12.7.5

claude-mem v12.7.5 补丁版本，修复 npx 安装时 Codex marketplace 注册冲突。若 Codex 已存在旧的 claude-mem-local 注册源，安装程序自动移除该过期注册并改用本地 npx marketplace，同时保留 Codex plugin_hooks 启用和 legacy AGENTS 清理逻辑。发布工作流指示改用 `npm run build-and-sync` 替代 `npm run build`，确保本地 marketplace 与 worker 二进制同步。验证覆盖本地安装与 Codex 0.128.0 smoke test。

### 重點
- Marketplace 冲突解决：检测并移除 Codex 旧注册源，重新添加本地 npx marketplace；保持 plugin_hooks 启用和 AGENTS 清理流程
- 发布流程优化：build-and-sync 命令确保 marketplace 与 worker 二进制同步

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v12.7.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v12.7.5

Patch release for npx installs that hit an existing Codex marketplace registration. 
 Fixes: 
 
 If Codex already has claude-mem-local registered from a different source, the installer now removes that stale registration and re-adds the local npx marketplace instead of failing. 
 Keeps Codex plugin_hooks enablement and legacy AGENTS cleanup after the marketplace registration succeeds. 
 Updates the release workflow instructions to use npm run build-and-sync instead of plain npm run build so the local marketplace and worker are synced during releases. 
 
 Validation: 
 
 npm run build-and-sync 
 bun test tests/install-non-tty.test.ts tests/infrastructure/plugin-distribution.test.ts tests/servers/mcp-tool-schemas.test.ts tests/setup-runtime.test.ts tests/hook-command.test.ts 
 Docker smoke with codex-cli 0.128.0 reproducing the remote-to-local marketplace source conflict and verifying install completion. 
 npx --yes claude-mem@12.7.5 --version

</details>