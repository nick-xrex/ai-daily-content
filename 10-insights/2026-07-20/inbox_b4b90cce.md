---
id: inbox_b4b90cce
date: 2026-07-20
source_ref: "[[00-inbox/.../inbox_b4b90cce]]"
title: "vscode-v0.5.0: release: v0.34.0 (#959)"
url: https://github.com/repowise-dev/repowise/releases/tag/vscode-v0.5.0
source: repowise-releases
published_at: 2026-07-20T09:41:42+00:00
fetched_at: 2026-07-21T01:07:55.279124+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise VS Code 擴充功能 v0.5.0 發布，將 Claude Code 外掛程式升級至 0.34.0 版本並同步 UI 套件。新增與外掛程式同步的功能：init、update、health 命令支援 --verbose 旗標以啟用除錯日誌；pre-modification skill 可讀取 get_risk API 回應中的新 defect_profile 區塊。"
key_points:
  - "Claude Code 外掛程式更新至 v0.34.0"
  - "init/update/health 命令新增 --verbose 旗標支援除錯日誌"
  - "Pre-modification skill 支援讀取 get_risk 回應的 defect_profile 區塊"
tags: [repowise, vscode-extension, claude-code, defect-profiling]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## vscode-v0.5.0: release: v0.34.0 (#959)

Repowise VS Code 擴充功能 v0.5.0 發布，將 Claude Code 外掛程式升級至 0.34.0 版本並同步 UI 套件。新增與外掛程式同步的功能：init、update、health 命令支援 --verbose 旗標以啟用除錯日誌；pre-modification skill 可讀取 get_risk API 回應中的新 defect_profile 區塊。

### 重點
- Claude Code 外掛程式更新至 v0.34.0
- init/update/health 命令新增 --verbose 旗標支援除錯日誌
- Pre-modification skill 支援讀取 get_risk 回應的 defect_profile 區塊

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/vscode-v0.5.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# vscode-v0.5.0: release: v0.34.0 (#959)

Bump the Python packages and the Claude Code plugin to 0.34.0, add the 
changelog section, and take the VS Code extension to 0.5.0 so the bundled 
@repowise-dev/ui catches up with a cycle of graph, health and docs work. 
 Plugin parity: init/update/health document --verbose, and the 
pre-modification skill reads the new defect_profile block on get_risk.

</details>