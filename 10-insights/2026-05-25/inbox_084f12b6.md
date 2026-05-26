---
id: inbox_084f12b6
date: 2026-05-25
source_ref: "[[00-inbox/2026-05-25/0014-ruflo-releases-v3-10-2-2132-windows-plugin-hooks-fix-7b92]]"
title: "v3.10.2 — #2132 Windows plugin hooks fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.2
source: ruflo-releases
published_at: 2026-05-25T21:21:40+00:00
fetched_at: 2026-05-26T00:21:35.234221+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.10.2 修復 Windows 原生 plugin hooks，無需 WSL 或 Git Bash。開發者 @marioja 詳細記錄問題：plugin hooks.json 中使用 /bin/bash -c、POSIX-only pipeline（jq、xargs -0、tr），以及在原生 Windows 上以 exit 126（「cannot execute binary file」）崩潰的 .sh shim script。新版本引入 Node 跨平台 shim（plugins/ruflo-core/scripts/ruflo-hook.cjs），透過 child_process.spawn 分發，始終 exit 0。初始化時平台檢測會在 Windows 上寫入 .claude/settings.json 覆蓋 bash hooks，Mac/Linux 保持不變。CI 新增 3 個煙霧測試（ubuntu、macOS、windows-latest），靜態審計強制無 /bin/bash；1999 通過、46 略過的測試基線無迴歸。"
key_points:
  - "Node shim（plugins/ruflo-core/scripts/ruflo-hook.cjs）用 child_process.spawn 替代 /bin/bash -c，跨平台相容"
  - "初始化平台檢測：ruflo init on Windows 寫入 .claude/settings.json 覆蓋 plugin bash hooks"
  - "靜態審計強制無 /bin/bash、無 POSIX pipeline；3 煙霧測試驗證 exit 126 修復"
tags: [windows-support, cross-platform, plugin-hooks, ruflo, ci-validation]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.2 — #2132 Windows plugin hooks fix

RuFlo v3.10.2 修復 Windows 原生 plugin hooks，無需 WSL 或 Git Bash。開發者 @marioja 詳細記錄問題：plugin hooks.json 中使用 /bin/bash -c、POSIX-only pipeline（jq、xargs -0、tr），以及在原生 Windows 上以 exit 126（「cannot execute binary file」）崩潰的 .sh shim script。新版本引入 Node 跨平台 shim（plugins/ruflo-core/scripts/ruflo-hook.cjs），透過 child_process.spawn 分發，始終 exit 0。初始化時平台檢測會在 Windows 上寫入 .claude/settings.json 覆蓋 bash hooks，Mac/Linux 保持不變。CI 新增 3 個煙霧測試（ubuntu、macOS、windows-latest），靜態審計強制無 /bin/bash；1999 通過、46 略過的測試基線無迴歸。

### 重點
- Node shim（plugins/ruflo-core/scripts/ruflo-hook.cjs）用 child_process.spawn 替代 /bin/bash -c，跨平台相容
- 初始化平台檢測：ruflo init on Windows 寫入 .claude/settings.json 覆蓋 plugin bash hooks
- 靜態審計強制無 /bin/bash、無 POSIX pipeline；3 煙霧測試驗證 exit 126 修復

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 Windows plugin hooks now work natively without WSL / Git Bash ( #2132 ). 
 Reporter @marioja documented every offending plugin hooks.json file: /bin/bash -c invocations, POSIX-only pipelines (jq, xargs -0, tr), and .sh shim scripts that crashed on native Windows with exit 126 ("cannot execute binary file"). 
 What shipped 
 
 Node shim : new plugins/ruflo-core/scripts/ruflo-hook.cjs (and copies in .claude-plugin/scripts/ and plugin/scripts/ ) — cross-platform port of the bash shim, reads stdin JSON via Node, dispatches via child_process.spawn, always exits 0 
 Init-time platform detection : ruflo init on Windows now writes a .claude/settings.json that overrides plugin bash hooks with node-based equivalents 
 Mac/Linux unchanged : existing ruflo-hook.sh and plugin hooks.json byte-identical — Windows path is purely additive 
 
 CI validation 
 
 Static audit: scripts/audit-plugin-hooks-cross-platform.mjs enforces no /bin/bash , no POSIX-only pipelines, no .sh references in plugin hooks 
 3 new smoke jobs on ubuntu + macos + windows-latest matrix: shim invocation, init-generated settings, end-to-end hook execution (proves no exit-126) 
 Test baseline preserved: 1999 passing | 46 skipped throughout 
 
 Versions 
 
 @claude-flow/cli@3.10.1 
 claude-flow@3.10.1 
 ruflo@3.10.2 
 
 All dist-tags (latest + alpha + v3alpha) updated. 
 🤖 Generated with RuFlo

</details>