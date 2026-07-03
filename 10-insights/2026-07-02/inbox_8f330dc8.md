---
id: inbox_8f330dc8
date: 2026-07-02
source_ref: "[[00-inbox/2026-07-02/2200-superpowers-releases-v6-1-1-7186]]"
title: "v6.1.1"
url: https://github.com/obra/superpowers/releases/tag/v6.1.1
source: superpowers-releases
published_at: 2026-07-02T21:58:30+00:00
fetched_at: 2026-07-02T22:07:14.324353+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "superpowers v6.1.1 發佈修復 Codex SessionStart hook 重新註冊問題。v6.1.0 移除 Codex hook config 後，manifest 缺少 hooks 欄位導致系統自動尋找 hooks/hooks.json（Claude Code SessionStart hook），最終重複註冊；新版本明確聲明 hooks: {} 以阻止 auto-discovery fallback。同時移除孤立的 session-start-codex 死代碼並修正陳舊文檔參考。新增 package-codex-plugin.sh 指令碼用於建構決定性的 Codex 插件包，包括時間戳正規化、可執行權限保留、元數據驗證和可重複構建能力。"
key_points:
  - "明確聲明 hooks: {} 而非缺失或空陣列，以阻止 auto-discovery fallback 執行 Claude SessionStart hook（manifest hooks 配置的陷阱修復）"
  - "移除孤立死代碼（session-start-codex），修正陳舊文檔參考（hooks-codex.json 示例遷移至 Cursor），清理過時的 hook 基礎設施"
  - "新增 package-codex-plugin.sh 建構決定性插件包，支援時間戳正規化、可執行權限保留、元數據驗證、byte-identical 可重複構建"
tags: [codex-hooks, plugin-packaging, manifest-configuration, superpowers, codex-plugin]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v6.1.1

superpowers v6.1.1 發佈修復 Codex SessionStart hook 重新註冊問題。v6.1.0 移除 Codex hook config 後，manifest 缺少 hooks 欄位導致系統自動尋找 hooks/hooks.json（Claude Code SessionStart hook），最終重複註冊；新版本明確聲明 hooks: {} 以阻止 auto-discovery fallback。同時移除孤立的 session-start-codex 死代碼並修正陳舊文檔參考。新增 package-codex-plugin.sh 指令碼用於建構決定性的 Codex 插件包，包括時間戳正規化、可執行權限保留、元數據驗證和可重複構建能力。

### 重點
- 明確聲明 hooks: {} 而非缺失或空陣列，以阻止 auto-discovery fallback 執行 Claude SessionStart hook（manifest hooks 配置的陷阱修復）
- 移除孤立死代碼（session-start-codex），修正陳舊文檔參考（hooks-codex.json 示例遷移至 Cursor），清理過時的 hook 基礎設施
- 新增 package-codex-plugin.sh 建構決定性插件包，支援時間戳正規化、可執行權限保留、元數據驗證、byte-identical 可重複構建

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v6.1.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

v6.1.1 (2026-07-02) 
 Codex 
 
 Codex no longer re-registers the Claude SessionStart hook. v6.1.0 removed the Codex hook config and its manifest hooks pointer, meaning to stop Codex from installing a SessionStart hook — but with no hooks field, Codex fell back to auto-discovering hooks/hooks.json , the Claude Code SessionStart hook that the marketplace ships from the repo root, and re-registered it along with its install-time trust prompt. The Codex manifest now declares an explicit empty hooks object ( hooks: {} ), which Codex reads as "no hooks" instead of reaching the auto-discovery fallback. An absent field, [] , and an empty inline list all collapse back to the fallback, so the value has to be exactly {} . 
 Removed orphaned Codex session-start dead code. hooks/session-start-codex had no caller once the Codex hook config was deleted, so it and its redundant test cases are gone. The worked shell-hook example in docs/porting-to-a-new-harness.md moves from Codex — now native skill discovery with no session-start hook — to Cursor, a live shell-hook harness, and the stale hooks-codex.json pointer in docs/windows/polyglot-hooks.md is corrected. The Codex plugin category is also fixed to "Developer Tools". 
 
 Packaging 
 
 New package-codex-plugin.sh for building the Codex portal package. A maintainer script produces a deterministic Codex "portal" archive — .zip by default, tar.gz on request — that normalizes entry timestamps, preserves executable modes, verifies every packaged skill ships its OpenAI metadata, includes the app and composer icons, and refuses to run against a dirty worktree. The packaged manifest keeps the source hooks: {} object so a portal-installed plugin avoids the same SessionStart auto-discovery, and the script can rebuild a byte-identical archive from a saved metadata source. Covered by a new test suite.

</details>