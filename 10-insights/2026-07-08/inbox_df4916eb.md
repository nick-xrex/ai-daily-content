---
id: inbox_df4916eb
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_df4916eb]]"
title: "v3.25.5 — npm wrapper publish + CI-red fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.25.5
source: ruflo-releases
published_at: 2026-07-08T17:27:46+00:00
fetched_at: 2026-07-10T00:44:43.365795+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.25.5 發佈 CI 紅色修復到 npm，包括 @claude-flow/cli@3.25.5、claude-flow@3.25.5 和 @claude-flow/plugin-agent-federation@1.0.0-alpha.17。修復涵蓋 PreToolUse hook stdout 契約（#2613）、可選依賴導入安全性（#2608）、Node 24 pnpm smoke 驗證（#2590）和 in-repo phantom subpath 防護（#2578）。所有 npx 驗證命令（claude-flow、@claude-flow/cli、@claude-flow/plugin-agent-federation）成功運行，V3 CI/CD run 28961054348 通過相關檢查。所有三個 legacy dist-tags（latest、alpha、v3alpha）指向 v3.25.5。"
key_points:
  - "npm 發佈三個套件版本搭配三個 legacy dist-tags（latest、alpha、v3alpha）實現向後兼容"
  - "修復來源：fix/main-v3-ci-red-shim-types 分支，包括 optional dependency 和 CI build 問題"
  - "驗證通過：npx -y claude-flow@3.25.5 --version、npx -y @claude-flow/cli@3.25.5 --version、npx -y @claude-flow/plugin-agent-federation@1.0.0-alpha.17 --help 皆成功"
tags: [ruflo, npm-publish, ci-fixes]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.25.5 — npm wrapper publish + CI-red fixes

Ruflo v3.25.5 發佈 CI 紅色修復到 npm，包括 @claude-flow/cli@3.25.5、claude-flow@3.25.5 和 @claude-flow/plugin-agent-federation@1.0.0-alpha.17。修復涵蓋 PreToolUse hook stdout 契約（#2613）、可選依賴導入安全性（#2608）、Node 24 pnpm smoke 驗證（#2590）和 in-repo phantom subpath 防護（#2578）。所有 npx 驗證命令（claude-flow、@claude-flow/cli、@claude-flow/plugin-agent-federation）成功運行，V3 CI/CD run 28961054348 通過相關檢查。所有三個 legacy dist-tags（latest、alpha、v3alpha）指向 v3.25.5。

### 重點
- npm 發佈三個套件版本搭配三個 legacy dist-tags（latest、alpha、v3alpha）實現向後兼容
- 修復來源：fix/main-v3-ci-red-shim-types 分支，包括 optional dependency 和 CI build 問題
- 驗證通過：npx -y claude-flow@3.25.5 --version、npx -y @claude-flow/cli@3.25.5 --version、npx -y @claude-flow/plugin-agent-federation@1.0.0-alpha.17 --help 皆成功

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.25.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.25.5 — npm wrapper publish + CI-red fixes

Published to npm 
 This release publishes the CI-red fixes from fix/main-v3-ci-red-shim-types to npm, including the root claude-flow wrapper package. 
 Packages 
 
 claude-flow@3.25.5 ( latest , alpha , v3alpha ) 
 @claude-flow/cli@3.25.5 ( latest , alpha , v3alpha ) 
 @claude-flow/plugin-agent-federation@1.0.0-alpha.17 ( latest , alpha ) 
 
 Fixes covered 
 
 #2613 — PreToolUse hook stdout contract for Cursor/Claude Code compatibility 
 #2608 — optional dependency import safety and plugin-agent-federation TS build 
 #2590 — Node 24 pnpm smoke verified green 
 #2578 — in-repo phantom subpath guard verified green 
 
 Verification 
 
 npx -y claude-flow@3.25.5 --version returned ruflo v3.25.5 
 npx -y @claude-flow/cli@3.25.5 --version returned ruflo v3.25.5 
 npx -y @claude-flow/plugin-agent-federation@1.0.0-alpha.17 --help ran successfully 
 V3 CI/CD run 28961054348 completed successfully for the relevant checks 
 
 Tracking issue: #2614 
 Release gist: https://gist.github.com/ruvnet/ed276119404d4d3fffdadfc0797705f8 
 Note: npm packages were published from temporary staging directories to avoid including unrelated dirty worktree state. A follow-up source metadata commit should update package versions to match the published artifacts.

</details>